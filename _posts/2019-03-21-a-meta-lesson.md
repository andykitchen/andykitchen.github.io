---
layout: post
title: A Meta Lesson
---

Two giants of AI, Rich Sutton and Rodney Brookes, have recently
written essays ostensibly presenting two opposing viewpoints for the
future of AI research. I highly recommend reading
[A&nbsp;Bitter&nbsp;Lesson](http://www.incompleteideas.net/IncIdeas/BitterLesson.html)
and the follow up
[A&nbsp;Better&nbsp;Lesson](https://rodneybrooks.com/a-better-lesson/). Both
authors pride themselves on elegant brevity, which is admirable. But
both viewpoints are so rich they really need further elaboration. So this
attempt at synthesis will be much more verbose but hopefully
edifying. Rich Sutton the sage has delivered his edict: it's
traditional for us junior monks ~~researchers~~ to provide the
accompanying exposition and analysis.

First a bit of background: Rich Sutton, as far as I can tell from
studying his work and hearing him speak, believes in a kind of
reward-minimalism. This is the idea that everything _can and should_ be
learned from a reward signal alone. Give me a world, tell me what is
better and what is worse and I will give you an agent. He seems to
have a critical view of any system that tries to include any innate
skill or ability. For example, why build in SLAM (Simultaneous
Location and Mapping)? If the agent needs to locate itself to get a
high reward, it will learn to locate. If it's unnecessary --- it
won't. If there's a better way to get where it needs to go, it will
eventually learn that instead of making a map. Why should we corrupt
our agents with our own limited ideas about how to solve a problem?

Many reward-minimalists believe that some kind of meta-learning will
take place if a sufficiently intelligent agent interacts with a
complex environment. I think Rich has a rich and nuanced view on this,
which I don't fully comprehend. (Side note: I tried to ask him and David Silver at a
NeurIPS panel last year and the question came out all garbled because
I was nervous and jet-lagged). Either way, it's intuitive that an agent
shouldn't just learn how to increase its reward. In a sufficiently
rich environment it should improve its methods of learning,
e.g. develop curiosity, reasoning etc. This is also related to
recursive self-improvement, the idea that an agent could learn to
modify itself and that the subsequent better version could do that
again, improving each time.

Rodney Brookes, on the other hand, has long had a chip on his shoulder
about the amount of compute needed to do AI. He pioneered building
robots with ingenious techniques that use many individually simple
rules that could interact and override each other, called a
subsumption architecture. The emergent behaviour of these interacting
simple rules could robustly solve surprisingly complex problems with
very low computational power and primitive sensors. He expressed his
contrarian approach in the title of his book "Fast, Cheap and Out of
Control".  He created the iRobot company and the Roomba vacuum
cleaner along these principles --- and it worked.

It is therefore not surprising that Rich and Rodney have butted heads
on the role of increased computation power for the development of AI.
Although I was surprised at Rod for his polemic tone and some
mischaracterisations of Rich's arguments. I think that Rich and Rod
both take clear positions with strong examples, my main contention
would be that Rod discounts using learning and search to improve
learning itself and so misses the deeper implications of Rich's
position.

I'm going to try and summarise both their positions in a few
sentences, but you should definitely read both essays especially
because they are so short.

Rich (approx.): learning and search always outperform hand-crafted solutions
given enough compute.

Rodney (approx.): No, human ingenuity is actually responsible for
progress in AI. We can't just solve problems by throwing more
compute at them.

I think both positions are interesting, important and well supported
by evidence. But if you read both essays, you'll see that these
positions are also not mutually exclusive, in fact they are synthetic.
But you need to take your view one level 'up' so to speak. I'll
illustrate this with a quote from Rodney:


> One of the most celebrated successes of Deep Learning is image
  labelling, using CNNs, Convolutional Neural Networks, but the very
  essence of CNNs is that the front end of the network is deigned by
  humans to manage translational invariance, the idea that objects can
  appear anywhere in the frame. To have a Deep Learning network also
  have to learn that seems pedantic to the extreme, and will drive up
  the computational costs of the learning by many orders of magnitude.


All true. But there is a critical omission: translational invariance
isn't necessarily the only good way to solve vision problems. We don't
want an AI algorithm that will exactly relearn to use convolutions. We
want a computer vision system that can learn something even better
than convolutions. Maybe some other more efficient sparse connectivity
pattern or even an entirely different way to do scene parsing. This is
critical, moving past simple feature engineering opened up a whole new
world for computer vision. The choice of convolutions is a
hand-crafted inductive bias --- a choice that will eventually need to
yield to learning as well.  But you see what happened, in the past we
hand-crafted features, now we hand-craft architectures (A point Rob
himself makes) this is exactly what Rich Sutton is critical of; we
should be always seeking to do more with learning and search.  Indeed,
we are using learning and search to improve learning itself,
meta-learning and architecture search are already an important and
growing area of research. Architecture search is relatively
unsophisticated at the moment, but it will hopefully give us something
better than just throwing countless PhD students at the problem (an
algorithm I call&hellip; graduate descent)

Rob goes on to criticise the need for massive data sets in Deep
Learning, this is indeed a fair criticism but totally mischaracterises
Rich; he doesn't even use the word 'data' once in his essay. A robot
that could learn to recognise objects from interaction with the world
alone is certainly one of their shared goals. Even then, the best
one-shot and few-shot learning systems that exist today either make
use of meta-learning or learned vector representations. Just to
reiterate, the most sample efficient systems that exist today _are
learned_.

Rob writes about the need for computational efficiency, he cites the
brain using only 20W.  This I think is a strange point, accurate LSTM
speech recognition models use very little compute and can run
effectively on mobile phones. Training these models may take a very
large amount of compute, optimising their hyperparameters, even more.
But the deployed model is frugal. Isn't the total cost of this system
when deployed on millions of phones still very good?  Google's recent
AlphaStar model runs on a single GPU when it's actually playing. Sure,
training AlphaStar took a huge amount of power --- improve that! Rich
Sutton isn't arguing for wasteful learning and search, he's calling on
us to improve it. He _is_ saying we'll never be able to go back to
hand-written StarCraft bots. Building a StarCraft bot that can rival
AlphaStar with only a few hours of play would be a huge achievement
for AI, but that would mean better learning and search, exactly what
Rich advocates.

If you train an LSTM with reinforcement learning to solve maze after
maze it will learn complex navigation behaviour, backtracking to take
past turns etc. Incredibly, it learns to learn the layout of each
individual maze problem. Does it do SLAM? Does it 'know' where it is?
does it use Bayesian inference? It _does_ do whatever it does, with a
surprisingly small amount of compute after training. Learning-to-learn
can yield systems that are _more_ efficient than anything we can
program. Meta-learning synthesises the need for efficient learning and
moving away from ad-hoc hand-crafting.

Let's elaborate on something from Rich now:


> A similar pattern of research progress was seen in computer Go, only
  delayed by a further 20 years. Enormous initial efforts went into
  avoiding search by taking advantage of human knowledge, or of the
  special features of the game, but all those efforts proved
  irrelevant, or worse, once search was applied effectively at
  scale. Also important was the use of learning by self play to learn
  a value function (as it was in many other games and even in chess,
  although learning did not play a big role in the 1997 program that
  first beat a world champion). Learning by self play, and learning in
  general, is like search in that it enables massive computation to be
  brought to bear. Search and learning are the two most important
  classes of techniques for utilizing massive amounts of computation
  in AI research. In computer Go, as in computer chess, researchers'
  initial effort was directed towards utilizing human understanding
  (so that less search was needed) and only much later was much
  greater success had by embracing search and learning.


Rich is referencing the success of AlphaGo and AlphaZero here. I think
this example is illustrative. AlphaZero has very little Go, Chess or
Shogi specific built into it, aside from being quite amazing it puts
some of Rod's criticisms into focus. It is true that AlphaGo uses a
lot of compute to train, but how many thousands of hours were poured
into the Stockfish position evaluation function? How many more would
be needed to beat AZ? Yes, much research went into AlphaGo itself, but
adding Chess and Shogi after Go took a relative small team less than a
year, how long would it take to port Stockfish to Shogi? Furthermore,
how long would Stockfish need to grind on a move to match the skill of
AlphaZero?  Once trained, AlphaZero's play is _more_ efficient than
Stockfish _for the same skill level_.

I think that Sutton could have been more clear that he does not think
more computation is a panacea in-and-of-itself, but Learning and
search are naturally and passively improved by increasing
computation. He could have emphasised that _improving_ search and
learning by increasing the efficiency is an important goal too. Rob
was too quick to attack only the compute related portions of Sutton's
essay, what he missed was that learning and search will ultimately
improve computational efficiency.

The _meta_ lesson is that the most important thing to improve with
search and learning --- is learning itself. Building an agent with
real-world recursive self-improvement will require all the compute and
ingenuity we can muster.
