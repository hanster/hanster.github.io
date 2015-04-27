---
layout: post
title: Temporal Coupling
---

### What is temporal coupling?

Temporal coupling is when methods of a class need to be called in a specific order to function correctly.
This means they are closely coupled in time.

### Seeing the problem

In my ruby Mastermind implementation, I had some unit tests that were calling one method before checking a result of a call to a separate method.

{% highlight ruby %}
it "is over when the exact matches is 4" do
  stubDisplay.set_exact_matches(4)
  game.start

  expect(game.over?).to be false
  game.get_exact_matches

  expect(game.over?).to be true
  expect(stubDisplay.get_exact_matches_times_called).to eq(1)
end
{% endhighlight %}

Here, you can see that the call to `get_exact_matches` needs to be made so that some state is changed.
The next call to `over?` is now coupled to the previous call.

###How I fixed it

In order to change the coupling, the `over?` method was refactored to take in some parameters.

{% highlight ruby %}
it "is over when the exact matches is 4" do
  expect(game.over?(1, Game::EXACT_MATCHES_WIN)).to be true
end
{% endhighlight %}

The two parameters are the number of guesses and the exact matches of the current guess.
This change removes the methods need to rely on the state of the game and so avoiding any temporal coupling as in the previous code example.

Spotting these design smells can be difficult in the beginning. That's why we practise and get feedback to improve and gain experience.
