---
layout: post
title: Q-learning
subtitle: Automated Stock Trading
thumbnail: assets/images/projects/q-learning/stock-market.jpg
type: ml
---

A Q-learning approach was used to implement a rudimentary method for automated
stock trading. It worked, sort of. Useful if you have infinite money. But it was
a fun project and a good learning experience.

### Description
Historical stock price data was fed to the Q-learning algorithm, which used the
past five days price changes to update the reward table and make the decision
whether to buy, sell, or hold a given stock. The algorithm was applied to a
cleaned version of the S&P 500 from the New York Stock Exchange from 2010
through 2016, totaling 467 individual stocks over 1,762 days.

My expectations for this project were fairly low as Q-learning was a completely
new concept to me and I wasn't be certain that:
1. The algorithm was actually entirely appropriate for this problem and that it
   would perform well. Or,
2. I could implement Q-learning in such a was as to have what would be generally
   be considered a successful result.

### Method
So the goal was simply to predict whether a given stock price would rise, fall,
or remain unchanged for each day. If a stock was predicted to rise the algorithm
would buy 10 shares (an amount I set arbitrarily); if the stock was predicted to
fall it would sell all shares (again, arbitrary); and if the stock was predicted
to remain unchanged no action was taken. (Although this may be a terrible
financial strategy I believed it would at least demonstrate the algorithms
ability to predict.)

A second model which randomly bought and sold according to the same rules was
created as a benchmark. I didn't (and still don't) have the arcane knowledge
used by human day traders to play the markets, and I thought such stiff
competition was out of the league of my simple approach.

Both models were allowed an unlimited supply of funds to buy stocks, but any
money they lost would count against their net worth.

### Results
Both the Q-learning model and the random model were able to be profitable
(possibly due to the general tendency of the market as a whole to grow over
time) but the Q-learning model accrued a net worth of
around $1.5 million, about 10x more than the random model.
However, both models exhibited large oscillations in their net worth that
would make any investor skittish; the models would often lose 20% or more of
their net worth over a matter of weeks, sometimes as much as 80% or 90%.

### Conclusion
Although the experiment may have little utility in the real world due to the
simplified envirionment and unrealistic parameters (such as having an unlimited
reserve of funds) it did show some amount of promise in that the Q-learning
model:
1. Made a profit rather than a loss. And,
2. Performed significantly better than random chance (which is about what I
   would expect from myself if I were to attempt the task).

Upon review, the experiment appears to have significant deficiencies but it was
still useful as a first exploration, it was engaging to choose a problem and
design an approach without much restriction, and it was an enjoyable project to
learn and work on.


#### A Story about Integrity
A funny thing happened while working on this project. This was the final project
for the machine learning class I was taking. I was lucky to have the final exams
for my other classes scheduled early during finals week so I spent the second
half of the week working on this project 8 - 10 hours a day.

As I recall, it was late one night when I was getting towards the end of writing
up my results when the conclusion in my outline didn't really seem to make sense
as I thought about the argument in more detail as I wrote it out in longform. I
went back to check the code and, sure enough, discovered I had made a mistake
implementing the algorithm that seemed as though it might have artificially
improved the results.

I experienced a mix of emotions as I sat alone with my work late at night.
First, disappointment that I had been suseptible to making a careless mistake.
Then panic started to build as I began to realize it also meant that the past
few days of work had largely been wasted and I worried if I would be able to
repeat all that work and finish the project on time. That was followed by a
sneaky thought that maybe I should just finish writing the report and turn it in
since I was fairly certain no one would ever know and I was already running
short on time; how long would it take to make the change, run the algorithm
again, analyze the results, and write up the new findings?

I have to admit that it took me 15 or 20 minutes to take a breath, calm down,
and deliberate among my options. Rather quickly I knew that the only right thing
to do was to run the experiment again with the corrected code but it took me a
while longer to summon the will to repeat all the work I had just done, now in
an even shorter timeframe. I set the program to run overnight and simply
appreciated the easy sleep afforded to me by a clear conscience and mounting
fatigue rather than think about the intimidating amount of work waiting for me
the next day.

When I reviewed the new results I was relieved to find that they were not
significantly different so I was able to reuse much of my analysis and report,
only tweaking a few things and rewriting the final section of my report. I only
had to sacrifice one full day of my expected rest after the school year to
finish the report and turn it in.

It was a valuable experience for me to discover that rigorous integrity doesn't
always require mountains more work and the satisfaction with one's self and the
final work product is a substantial reward. Doing the right thing was well worth
it.


### Language
- Python
  - numpy
  - pandas
  - matplotlib

[Full Report](/assets/images/projects/q-learning/Q_Learning_Final_Project.pdf)
