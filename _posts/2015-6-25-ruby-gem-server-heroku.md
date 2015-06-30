---
layout: post
title: Running a Ruby Gem server on Heroku
---

As part of my current iteration, I had a task to build and push the core logic for my TicTacToe game to my own gem server.
This is a step by step guide on how to use [geminabox][1] and [Heroku][2] to achieve your own Ruby Gem server.
Using this [blog post][3]

## Heroku account

Heroku toolbelt installed:
On OSX if you have homebrew installed you can run

{% highlight bash %}
brew install heroku-toolbelt
{% endhighlight %}


Create a folder for the project.

Add a `config.ru` file that will be used when the server starts.

{% highlight bash %}
require "rubygems"
require "geminabox"

Geminabox.data = File.expand_path('data', File.dirname(__FILE__))
run Geminabox
{% endhighlight %}

You will also need a Gemfile to specify the dependencies:

{% highlight bash %}
source 'https://rubygems.org'

gem 'thin'
gem ‘geminabox'
{% endhighlight %}

Add a `Procfile` for Heroku to run at start up:

{% highlight bash %}
web:     bundle exec thin -p $PORT start
{% endhighlight %}

Run the server and then add the Gem(s) you want.

Stop the server and then make the folder a Git repo with `git init`.

The Git repo can then be deployed to Heroku and when the app starts up, we have a running Ruby Gem server that will have your Gems ready to serve.

Since we are using the free version of Heroku, whenever the application sleeps or is redeployed, it will be in the same state as in the Git repo. So any newly added Gems will not be available.

A work around for this is to run the Gem server locally and upload any new Gems. Since we defined a data folder, we can commit the changes and the Gem(s) will be stored.


Create an app in Heroku so you can push your server up.

In the folder with your server, which should now be a Git repo, you need to set up the newly created Heroku app as a remote repository so you can push to it.

{% highlight bash %}
heroku git:remote -a desolate-caverns-2106
{% endhighlight %}

Where `desolate-caverns-2106` is your application name`.

Next push your code to Heroku:
{% highlight bash %}
git push heroku master
{% endhighlight %}

The server should start straight away.

To use the gem you need to add the following to the Gemfile of your project.

{% highlight bash %}
gem 'tic_tac_toe_core', '0.1.0', :source => 'https://desolate-caverns-2106.herokuapp.com/'
{% endhighlight %}

Where the gem name and source are related to your own gem and Heroku address.

## Conclusion
Now you have your own gem server running on Heroku. To upload new gems, you will need to add them to your local instance and then commit the changes to Git. You can then push these changes back to Heroku so that anytime it redeploys / wakes up, it will have the Gems ready.
Note that any Gems you upload will be wiped out as Heroku will not save any data.


[1]: https://github.com/geminabox/geminabox
[2]: https://heroku.com
[3]: http://www.rubyhood.com/2011/06/hosting-gem-server-on-heroku.html
