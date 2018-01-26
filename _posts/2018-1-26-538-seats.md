---
layout: post
title: "Estimating seat splits of district plans"
category: gerrymandering
tags: [math]
use_math: true
---

# Estimating the number of seats won

FiveThirtyEight has a recent
[project]{https://projects.fivethirtyeight.com/redistricting-maps/} in
which they generate a number of different congressional maps based on
different optimization functions. For each of the eight plans, they
classify the seats according to the Cook PVI as (usually) democratic,
highly competitive or (usually) republican. I think this is a very
interesting project.

Unfortunately, they succumb to the temptation to quantify the expected
number of seats won under each plan. This is probably reasonable to do
for the no-holds-barred democratic and republican gerrymanders in
which there are relatively few competitive seats. But I am hesitant to
place too much weight on their numbers for the other six plans.

In their
[methodology]{https://fivethirtyeight.com/features/we-drew-2568-congressional-districts-by-hand-heres-how/},
the authors calculate seats won as follows: Using a decade of
historical data, they generate a probability that a given district
elects a Democrat based on its PVI score. They then add up these
probabilities. Mathematically this is perfectly defensible --- this is
precisely how you would calculate an expected value from these
probabilities.

My skepticism stems from the similarity between this technique and
that used by Jowei Chen and David Cottrell in their 2016 [Electoral
Studies
paper]{http://www-personal.umich.edu/~jowei/gerrymandering.pdf}. As
Jeff Buzas and I describe in our
[preprint]{https://arxiv.org/abs/1707.08681}, the smoothing process
that is inherent to the addition-of-probabilities technique is
essentially insensitive to all but the most extreme gerrymanders. (See
also my summary in my [guest
post]{http://electionlawblog.org/?p=94161} on the Election Law Blog.)
As such, the expected number of seats won by a given party *as
estimated by this approach* will be stable under all but the most
extreme plans. This is the same pattern seen in the FiveThirtyEight
study.

A reader of the FiveThirtyEight study might compare the expected
number of seats won under the current plan (200.6 according to study)
to the number under a compact plan that respects borders (203.9) and
decide that on a national level, gerrymandering does not have a
significant influence on who controls the US House. It *is* possible
that the net effects of gerrymandering are negligible in terms of
House control, but due to methodological issues, I don't believe this
study provides any evidence for that position.
