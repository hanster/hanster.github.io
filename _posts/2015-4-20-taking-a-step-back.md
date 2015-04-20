---
layout: post
title: Breaking down a problem and taking a step back
---

Recently I have been doing some pairing while trying to implement [mastermind][1] the TDD way.
We had problems when trying to write the next test in the simplist way possible.

It turns out that we went down the wrong path and so any tests we tried to think about seemed to be a big step and quite complex. Jarkyn had recently been reading [Test-Driven Development by Example][2], by Kent Beck. She recalled that if such a thing happens, sometimes it's best to go back a few steps and try another route.
This can give you a new perspective on the problem and so taking a step back can actually help you move forward.

Finding it hard to write tests can also be a design smell. In my case it was due to having the input tightly coupled to the game.

I found an interesting [article][3] on the 8th Light blog explaining this situation. 
Two [SOLID][4] principles are mentioned, [Dependency Inversion Principle][5] and [Single Responsibility Principle][6]. These applying these two principles will help decouple objects and make testing easier.

I plan to write more about the SOLID principles as I apply them and to help solidify my understanding.

[1]: http://en.wikipedia.org/wiki/Mastermind_%28board_game%29
[2]: http://www.amazon.co.uk/Driven-Development-Addison-Wesley-Signature-Series/dp/0321146530
[3]: http://blog.8thlight.com/josh-cheek/2011/10/01/testing-code-thats-hard-to-test.html
[4]: http://en.wikipedia.org/wiki/SOLID_%28object-oriented_design%29
[5]: http://en.wikipedia.org/wiki/Dependency_inversion_principle
[6]: http://en.wikipedia.org/wiki/Single_responsibility_principle
