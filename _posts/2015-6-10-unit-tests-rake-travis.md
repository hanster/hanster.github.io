---
layout: post
title: Unit and integration tests with Rake and Travis CI
---

I recently added some tests to my TicTacToe implementation which played a full game multiple times.
As this usually took a few minutes to fully run, it was interfering with the speed of the feedback loop when doing TDD.

I had originally just marked the slow tests as pending when doing my TDD cycle but during my last Iterative Planning Meeting (IPM), Jim and Nathan mentioned that I should not have any pending tests committed. They suggested I use [Rake][1] to separate the tests.

I split my integration tests out to a `/integration/` folder.

The following Rake task ran the unit tests for quick feedback. Note that the default Rake task is set to run the unit tests:

{% highlight ruby %}
task :default => [:spec]

task :spec do
  desc "Run the specs."
  RSpec::Core::RakeTask.new(:spec) do |t|
    t.pattern = "spec/tictactoe/**/*_spec.rb"
  end
end
{% endhighlight %}

The Rake task for running the integration tests, this depends on the spec task so all the tests are run:

{% highlight ruby %}
task integration: [:spec] do
  desc "Run the specs including the integration specs."
  RSpec::Core::RakeTask.new(:integration) do |t|
    t.pattern = "spec/integration/**/*_spec.rb"
  end
end
{% endhighlight %}

With the Rake tasks now set up I also took steps to add the project to [Travis CI][2].
Travis CI is a continuous integration tool which will build your project and run any tests every time you make a commit to Github.

To get my TTT project working I needed to add a Gemfile to indicate the project dependencies.

{% highlight ruby %}
source 'https://rubygems.org'

gem 'rake'
gem 'rspec'
gem 'simplecov'
{% endhighlight %}

Next a `.travis.yml` is needed to indicate what Rake task I want Travis CI to run:

{% highlight ruby %}
script: bundle exec rake integration
{% endhighlight %}


## TL; DR
Slow feedback loop so I used Rake to split my tests and then added the project to Travis CI for continuous integration.

[1]: https://github.com/ruby/rake
[2]: https://travis-ci.org/
