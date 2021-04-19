_Notes from a guest lecture at RMIT_

Episteme and Techne
-------------------

The story goes that a mathematition and his wife were trying to get a
sofa to fit through a door, but with little success. "Ah!" the
mathematician says with a flash of insight, I can prove this is not
possible. And runs away to write down the details. When he returns to
tell his wife about his impossibility proof, she has already got the
sofa through the door.

The ancient greeks had multiple words for knowledge:
episteme, translated as theoretical or abstract understanding and
techne, translated as art or craft. In this story the mathematician had
great episteme and the wife --- excellent techne.

Episteme is important, and you cannot be a great programmer without it,
but techne is just as important. This talk is about sharing techne by
giving you tips and tricks that I've accumulated over the years. They
will (hopefully) let you solve problems quicker with less frustration
and develop your own instincts and intuition.

A little bit about myself
-------------------------

I am a bit of a starup rat, I have been ground-floor on 3 startups and
started the first deep learning consulting team in Melbourne. I have
been programming for money a bit over 10 years now. I am currently the
CTO of Cortical Labs a synthetic intelligence / biocomputation startup
based in Melbourne.

I also founded the Melbourne ML/AI Meetup, which is the largest AI
meetup in the Asia Pacific region, we have over 6,000 members now. You
can find out more at [<http://mlai.melbourne/>](http://mlai.melbourne/)

You can find out more about what I do by following me on Twitter handle:
[@auastro](https://twitter.com/auastro)

I've been interested in AI since an early age, the first program I ever
wrote was an 'AI'. I realised later it was really just a chatbot, still
not bad for a school child. It just rearranged your words and spit them
back out at you. You could type "I love my dad", and it would reply with
something like "Why do you love your dad?"

I know a lot about programming and I've certainly done a lot of it for
love, money and science. I know more than most, but less than many. The
funny thing about coming close to mastering something is that you
realise how little you really know. I can say for sure that we are only
scratching the surface of what's possible with computers. We are really
not very close at all to understanding the true nature of computation.

The Mental Toolbox
------------------

My father was given his grandfather's toolbox. He still has some of his
grandfather's tools. He also has also added new tools. As a thinker, you
need a mental toolbox. Your success in science and business is dependent
on the quality of your mental tools. I want to show you the tools in my
mental tool box, they are a good start. They have all demonstrated
perennial value to me, some will work well for you, others you will
eventually throw away and replace with better ones.

Polya vs. Feynmann
------------------

"When I am doing research, I often think of the Feynman Problem-Solving
Algorithm, supposedly coined in jest by another Nobel Prize-winning
physicist, Murray Gell-Mann, about Richard Feynman's innate
problem-solving ability: Write down the problem. Think very hard. Write
down the answer."

This is surely effective but cannot be easily taught and cannot even by
carried out by most people (myself included).

In contrast there is Polya's book "How to Solve it" including a 4-step
plan and many heuristic tools to solve problems. Read the book, it's a
gold mine.

Problem solving can be systematised; insight and inspiration are needed
for monumental discoveries but most day-to-day problems can be solved by
systematic thinking and a good mental tool box.

Luckily these can be taught, collected and used by us mere mortals. Here
are some examples from How to Solve it:

-   Can you find a problem analogous to your problem and solve that?
-   Can you find a problem related to yours that has already been solved
    and use that to solve your problem?
-   Can you start with the goal and work backwards to something you
    already know?

What is programming for?
------------------------

The bare essence is "solving problems using computers", We are not
producing computer code for its own sake. Generally if you can solve the
same problem with less code this is good.

Famous quote:

"Measuring programming progress by lines of code is like measuring
aircraft building progress by weight." --- Bill Gates

But our previous definition leaves something to be desired, here's
another try: "Solving a series of related problems using computers with
a team of people"

Generally, you will discover new problems or expand the scope of your
investigation so the ability of code to solve one problem becomes
secondary to its ability to grow into different problems and to be
understood by a team of people.

Understanding by people is critical; in university hardly anyone but you
and your poor lecturer has to read your code. Make your code as neat and
easy to read as possible, then make it neater. I'll often rewrite a
function 2-3 times for readability only. Clean, organised and easy to
read code will make you popular, easy to hire, and live longer.

A Codebase is a living thing
----------------------------

A Codebase lives in constant interaction with a team of programmers,
their collective knowledge and mental models are more important than the
text of the code itself.

Changing Levels
---------------

How do you write a symphony? One note at a time. How do write a million
lines of code? One line at a time.

When you are first learning a musical instrument, you need to think
about every finger movement; each note is a struggle. Slowly, over time
you learn to think in chords and melodies, and then variations and
movements.

Just as when you are learning to program, the syntax of a single line is
a challenge, until lines become functions and functions become
algorithms and systems.

Seeing the whole puzzle while messing with the pieces will not come
immediately, it can only be learned through experience by programming.
Be patient, the skill will come.

Make sure you build systems from start to finish. Normally in a job,
especially if you are hired at a junior level, you will be working in
the corners of other peoples' systems. This is to be expected, but you
also need to learn to invisage whole systems and build them from scratch
yourself.

A critical skill is zooming in and zooming out, changing the level of
your attention. Code is written line-by-line but systems cannot be
designed and maintained so close up. Effective programmers can think
clearly at these different levels and move fluidly between them.

When writing code, every so often, consider the line you are currently
writing. How does it relate to other lines around it, how does this
function relate to the other modules, who calls it? Why? How are the
answers used? Why is this computed here instead of somewhere else? Keep
this up, soon you will be able to see whole systems in your minds eye.

The importance of starting simple
---------------------------------

Always start with the simplist thing possible, the easiest version of
your problem, a smaller dataset, less dimensions.

For example if you are building a predictive model from five different
databases each giving dozens of attributes, start with one database
first, and one or two attributes. Build a basic model, get it working,
assess the results then iterate from there.

The enemy of smart people is over-complication, never solve a harder or
more complex problem than is absolutely necessary; which is normally
when simpler solutions have been demonstrated to be inadequate. Never
dismiss off-hand a simple solution as inadequate --- do not nerd-snipe
yourself.

Always compare against baseline algorithms
------------------------------------------

Whenever you are confronted with a problem, build a "baseline" solution.
This is a brutally simple solution, so simple it's a little bit funny
how stupid it is.

A friend named Matt won a preditction competition with "predict
tomorrow's value as the average of today's value and the value one year
ago". In other scientific or engineering situations this could be using
a linear approximation, PID controller or even evaluating 10 random
solutions and returning the best one.

By its nature this shouldn't take too long to implement: an afternoon to
a few days at most (not including support code). The benefits are huge!
If, for example, your future solutions perform worse than your baseline,
you know there is a bug. Often the baseline model is surprisingly good
and gives you a rough indicator of how much to expect from later
solutions. The baseline model also exercises all your data loading,
evaluation and plotting code while being easy to understand. e.g. if you
get strange output, you can more easily pin it on a data parsing bug.

Tips for testing for scientific code
------------------------------------

Testing scientific and mathematical code tends to have unique
challenges:

-   Many possible configurations
-   Complex algorithms
    -   many stages and pre-processing steps
    -   heavy use of random numbers
    -   complicated internal states
    -   iterative algorithms with complicated stopping conditions

Some suggestions:

-   Automate testing of many random configurations
-   Carefully seed all random number generators
-   Test complex algorithms on simple instances that can be solved
    manually, or instances that are built backwards around known
    solutions, e.g. optimisation problems with a known minimum.
-   If a special case of a problem can be solved easily and/or in closed
    form, test your solver by generating many random instances and
    comparing the solution of your general algorithm to the closed-form
    solution.
-   You get a lot of value testing end-to-end. Don't just test your
    linear regression function, instead generate a synthentic dataset
    with a known linear trend as a CSV then load it and check your
    results, are the final predictions what you expect?
-   Add lots of little sanity checks everwhere. Does it ever make sense
    for this number to be zero? What about negative? This vector should
    sum to 1? Check! It's better to get the right answer than the wrong
    answer twice as fast. Also, most languages have a feature to turn
    off assertions when you really need speed, but I normally leave them
    on unless I have a really good reason to turn them off.
-   Checkpoint all long running computations, ideally you should be able
    to stop any long calculation half way through and then pick it back
    up later by loading the checkpoint, this is invaluable for debugging
    because you can load checkpoints from before a crash.
-   Probabilistic testing is useful but subtle, you can use null
    hypothesis significance testing in automated test suites with a
    p-value like 0.0001 so if you get a failure you know something is
    really broken. Just make sure you pick a sample size with good
    power, ideally something like \>99%

Two types of Bug
----------------

Understand that bugs can be classified into two categories:

-   Whoops Bugs (Concretisation Errors) Failure to implment an algorithm
    correctly.

-   Oooooh Bugs (Semantic Errors) Incorrect answer produced because the
    solution doesn't match the problem.

Whoops bugs are where you slip over on a Banana peel and go whoops
"that's not what I meant to do".

Ooooh bugs are where you go ooooh, I'm at the right number on the right
street, but the suburb is wrong, "Ooooh, there are two streets with the
same name". You realise that the way you thought things were --- is
different to how they actually were.

Your programs will always have bugs, but they will change in character.
You will often need to put as much, or more, effort into debugging your
mental model as debugging your code.

When you start programming the majority of bugs you will need to wade
through a lot of "Whoops" bugs. As you become a better programmer the
majority of significant bugs will become "Oooooh" bugs.

Seed your damn random number generators
---------------------------------------

There is never ever, ever any reason to use an unseeded (pseudo) random
number generator. You will have bugs, the bugs will appear and disappear
because of different random numbers, you will be sad. You always want
things to be more reproducable, never less. With proper seeds anyone can
run you code later and get the exactly same results, magic.

But I want to test my code with lots of different random numbers!

1.  Just use a sequential counter for the seed
2.  Use a splittable RNG (advanced)

The Single Point of Truth principle (or how to wrangle your hyper-parameters)
-----------------------------------------------------------------------------

Generally, within a program or system, for any question you can ask the
should be one way to answer that question and it should come from one
place.

Scientific code will have a lot of tuning knobs that need to set, make
sure the settings for all the different knobs are stored in one place,
both in the code and when in a config file.

Visualisation is your best friend
---------------------------------

Plot and visualise everything, all the time. It will catch a lot of
bugs. You often won't need anything more advanced than line plots and
histograms.

Don't wait around, compress your feedback cycle
-----------------------------------------------

You cannot write bug-free code every time, you cannot make the right
choice every time. The most efficient and effective programmers
eliminate what doesn't work more quickly. Ideally, it should be a few
seconds from pushing enter to finding out if your code is working or
not. If not, fix your build system, fix your test suite; even build a
hardware test rig or create a simulation environment.

This is not always possible due to unforutnate realities, but feedback
loops should always be made as fast as possible. This is worth investing
significant resources. You should always be looking for ways to get the
feedback cycle as tight as possible, you will get more done faster with
less frustration.

(data) Science is non-linear: plan for misunderstandings, bug-fixes and rework
------------------------------------------------------------------------------

In the real world, you can never go from A to B in a straight line. You
are navigating a maze, there will be dead ends. You will need to
backtrack, this is normal, don't let it get you down or frustrate you.
Annoyingly most articles on programming and data science present a
solution, a path through the maze without much attention to the process
of navigating the maze the first time. Critically, following a path
through a maze is easy once you know the way and tells us almost
nothing about how to navigate a new maze.

I've had months long projects, where if I had know the right answer up
front, actually writing the code would have taken me an afternoon.
