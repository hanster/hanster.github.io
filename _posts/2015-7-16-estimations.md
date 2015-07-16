---
layout: post
title: Estimations
---

## How long will that take?
During my apprenticeship I have been working on a weekly schedule which start with an Iterative Planning Meeting (IPM).

Jim and Nathan act as the clients and as we pull stories into the current iteration they ask how long a story will take.

At 8th Light we use a technique called PERT. This involves providing 3 estimates: Optimistic, Realistic and Pessimistic.

- **Optimistic Estimate** - This assumes that everything possible goes smoothly and you have no problems in doing the task.
- **Realistic Estimate** - This is the estimate that is most likely to be correct.
- **Pessimistic Estimate** - This assumes things went really badly.

In the Clean Coders book, Uncle Bob calls the estimates Optimistic, Nominal and Pessimistic.
He states that the Optimistic and Pessimistic Estimates should have a less than 1% chance of success.

Given these 3 values, to calculate the points for the story we work out the weighted mean. This value is more skewed towards the Realistic Estimate and the calculation is as follows:

{% highlight ruby %}
Weighted mean = (O + 4R + P) / 6

Standard deviation = (P-O) / 6

Task Estimate = Weighted mean + Standard deviation * 2
{% endhighlight %}

This value should be a more realistic estimate.

## Group estimating

When working with other software developers we all need to give input into what we think each of the estimates might be for a given task.
In order to avoid influencing each other, we all give our estimates at once. Everyone gives their estimates by doing a sort of rock, papers, scissors motion with 2 closed fists, and then holding out the number of fingers they think the task will take.

If everyone agrees we move onto the next task, otherwise we discuss our choices and do another round.
This discussion helps to ensure everyone be on the same level.

