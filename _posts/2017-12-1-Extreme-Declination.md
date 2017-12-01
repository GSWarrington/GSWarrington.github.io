---
layout: post
title: "Congressional elections with extreme partisan asymmetry"
category: gerrymandering
tags: [SCOTUS,PA,math]
use_math: true
---

# Extreme values of partisan asymmetry

With the upcoming court cases in Pennsylvania, I went back to look at
which historical congressional elections have displayed the most
significant partisan asymmetry. The current Pennsylvania district,
amazingly, occupies three of the top seven spots among elections with
the most pro-Republican advantage according to a scaled declination
measure.

The [declination](https://arxiv.org/abs/1705.09393) can be used to
measure asymmetry in how Democrats and Republicans are treated by a
district plan. It takes values between -1 and +1 with 0 indicating
symmetry, negative values indicating pro-Democrat asymmetry and
positive values indicating pro-Republican asymmetry. Empirical data
suggests that there are issues with comparing the value of declination
between elections that have greatly different numbers of
seats. Scaling the declination by one half of the log of the number of
seats appears to make a reasonable adjustment for such
differences. This scaled version is denoted by $\tilde{\delta}$ in the
below tables (both tables are from my paper cited above).

The first table lists the ten congressional elections since 1972 with
the most positive value of $\tilde{\delta}$. Note that seven of the
elections are from 2012 or later. Ohio and North Carolina each make
two appearances while Pennsylvania appears three times.

<img src="{{ site.baseurl }}/images/Rep-ten.jpg" width="400">

The second table considers the corresponding ten elections with the
most negative values of $\tilde{\delta}$. Here too the list is
dominated by a few states: notably Massachusetts and Texas. In this
case, though, there are no elections since 2012 that appear.

<img src="{{ site.baseurl }}/images/Dem-ten.jpg" width="400">

The values of $\delta_N$ are a measure of how many seats are allocable
to the partisan asymmetry. A closely related measure is referred to as
the *$S$-declination* in [this
paper](https://arxiv.org/abs/1707.08681) with J. Buzas.