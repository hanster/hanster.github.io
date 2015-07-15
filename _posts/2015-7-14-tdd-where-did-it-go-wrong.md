---
layout: post
title: TDD Where did it all go wrong?
---

I recently watched a [talk][1] by Ian Cooper, *TDD Where did it all go wrong?*

In the talk, Ian discusses some of the areas in which some people have misinterpreted TDD. He references the classic Kent Beck book, *TDD by example* many times during the talk.

One of the main points I took away was about what to test. You should focus on testing behaviour and not implementation details.
If you test this way, you should be able to change the implementation details and your tests will not break.

## Where did it all go wrong?

Ian mentions 2 points:

- Not writing your tests against behaviour, instead writing them against operations and class.
- Coupling the implemenation details to the tests because we don't understand the refactoring stage in *Red, Green, Refactor*

If you fix these 2 problems, it should lead to smaller test suites that are much easier to understand and less painful to own.

## TDD rebooted

Going back to TDD by Example and really understanding the core principles.

## The Zen of TDD
*Avoid testing implementation details, test behaviours*

- testing per class fails the TDD ethos. Adding a new class should not be the trigger for a new test. The trigger is implementing a new requirement (behaviour.
- testing outside-in, don't make your outside your UX, focus on the domain models and think about using ports and adapter architecture. Think about the surface of a module and test the API. Don't test the internals as you are then coupled to the implementation details.
- test against the use cases.

Recommended reading [Dan North, Intro to BDD][2]

Ian goes on to quote the Kent Beck book on how you should be testing behaviours and thinking about the  the surface layer, external parts and the API of what you are testing.

## What is a Unit Test?

In regards to TDD by example: Test should run in isolation from other tests. Not testing a module in isolation from other modules, i.e. one class under test with everything else mocked out. Mocks can dig into implementation details and cause you to have an over specified test which is tightly coupled to your implementation.

## Red-Green-Refactor

*The Simplist Thing*

Go green as fast as possible, commiting as many sins as needed. Cut and Paste, just hack it to make it work.
It is difficult to do 2 things at once, solving the problem and engineering it well. One or the other.
Get to the solution fast, quote from the book:

```
We can commit any number of sins to get there, because speed trumphs design, just for that brief moment.
```

*Clean Code When*

The refactoring step is when we think about clean code:

- apply patterns
- remove duplication
- sanitize the code smells

**But** you do not write new tests here. You are not introducing public classes. The current test should be covering the new classes. If it is not covered you have added new behaviour. The API should be under test already.
Refactoring changes the implementation details. If you do add tests, you are binding your implementation details to your tests and coupling your tests. *Coupling* is what will kill you.

This leads to:

- less tests
- move faster, as you go quickly to Green
- less tests, mean you move forward quicker and gain momentum

## Gears

5th gear would be the obvious implementation but be careful you don't make leaps that are too big.
When you get to tricky code where you are not sure, you can switch down and write smaller tests to navigate. These would be testing the implementation details.
Acid test, can you throw away these tests on the inside, do we have tests on the outside that test the behaviour?
Implementation tests should really be throw away. Implementation tests are cause coupling as you are testing internally. You can leave the tests but feel free to delete them if you are reimplementing the details.

## Summary

- Main reason to test is new behaviour and not a method on a class.
- Get to Green as quickly as possible, anything goes, then refactor and clean up
- No new tests when refactoring internals and privates, they should already be covered

The big take aways for me were focusing on behaviour in tests and that you don't necessarily have a test file per class.

Watch the [video][1] and read [Test Driven Development By Example][3].


[1]: https://vimeo.com/68375232
[2]: http://dannorth.net/introducing-bdd/
[3]: http://www.amazon.co.uk/gp/product/0321146530/ref=as_li_tl?ie=UTF8&camp=1634&creative=19450&creativeASIN=0321146530&linkCode=as2&tag=amazonss-21&linkId=ZCEFD56GJVZVA6XN
