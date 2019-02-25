---
layout: post
title: Generating Combinations
---

For a recent project (that I'll be writing more about in the future)
I needed to be able to generate permutations efficiently; this
got me reading about [combinatorial number systems](https://en.wikipedia.org/wiki/Combinatorial_number_system) which provide the mathematical tools
for doing various clever things with combinations.
On the Wikipedia page for combinatorial number systems I stumbled
across [Gosper's hack](https://en.wikipedia.org/wiki/Combinatorial_number_system#Applications)
which is a great little bit of code for generating all possible
combinations of a bitset very quickly. For example, if you want to generate
all 64-bit values with exactly 3-bits set, Gosper's hack
would let you generate them quickly and in ascending order.


```c
/* 
 *  Gosper's hack
 */
unsigned long comb_next(unsigned long b)
{
        unsigned long u, v;

        u = b & -b;
        v = u + b;

        if (!v) return v;
        return v + (((v^b)/u)>>2);
}
```

This function, given some input bitset, will generate the next
combination in sequence. So two obvious questions
are: what value should we start with? and what if we
want to generate only length N-bit strings with K-bits set,
instead of full 64-bit strings. Now, it took me an afternoon of thinking
about this code, before I got Ah-ha! moment about how it works.
And you may enjoy puzzling over it, so spoiler warning below.

The initial value should be the smallest number with K-bits set,
which will just have all the lowest bits set. You could write
this out manually, but there is a bit-twiddling trick you can use;
which is: `(1L << k) - 1`. If we only want to generate N-bit strings,
we can create an N-bit mask and do a logical 'and' in the right place.

Finally if you do an instruction level benchmark on this piece of
code using Linux 'perf' you will notice that it spends
most of the time in the single integer division instruction.
However `u` is always a power of two, so this actually
corresponds to a bit shift by the index of the only set bit;
this leads to an optimization, which increased the performance
well over 5x on my CPU.

```c
unsigned long comb_next(unsigned long b, unsigned long mask)
{
        unsigned long u, v;

        u = b & -b;
        v = u + b;
        v = v & mask;

        if (!v) return v;
        return v + ((v^b)>>(__builtin_ctzl(u)+2));
}
```

Here `b` is some value with K bits set, mask is a value with all
N lowest bits set. It returns the next combination with K of N bits set.
It will return 0 after the last combination in the sequence.

If you compile this for a modern x86-64 chip with `gcc -c -O2 -march=native ...`
you get a very compact 9 instructions, which run very fast.
On my i7 laptop in a tight loop it can generate over 500 million
combinations per second:

```
0000000000000000 <comb_next>:
   0:	c4 e2 e8 f3 df       	blsi   %rdi,%rdx
   5:	48 8d 04 17          	lea    (%rdi,%rdx,1),%rax
   9:	48 21 f0             	and    %rsi,%rax
   c:	74 13                	je     21 <comb_next+0x21>
   e:	f3 48 0f bc d2       	tzcnt  %rdx,%rdx
  13:	48 31 c7             	xor    %rax,%rdi
  16:	83 c2 02             	add    $0x2,%edx
  19:	c4 e2 eb f7 ff       	shrx   %rdx,%rdi,%rdi
  1e:	48 01 f8             	add    %rdi,%rax
  21:	c3                   	retq   
```

So there you have it, channelling [Dan Lemire](https://lemire.me/blog/),
a compact, ultra-fast way to generate all the combinations in a bitset.
If you come up with a further optimization or found this snippet
useful, drop me a line.

AK
