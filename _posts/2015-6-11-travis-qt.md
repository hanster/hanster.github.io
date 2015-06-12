---
layout: post
title: Problems with QT and Travis CI
---

In my previous post I added Rake and also got my project building on Travis CI.

After implementing the Graphical User Interface (GUI) using [QT][1] via the [qtbinding][2] gem, I had some problems with getting Travis CI to run my GUI tests.

Even though my Rake task ran fine on my machine I needed to do some extra changes for Travis CI to run correctly.

First Travis CI couldn't load the qtbindings file correctly.
I had to change `require 'qt'` to `require 'Qt'`. Note the capital `Q` is needed for it to load on Travis CI.

Once the file was loaded I then got the following error once the tests tried to run on Travis CI.

```
rspec: cannot connect to X server
```

Mateu had ran into this problem a few weeks ago and it seems that you need to do some extra set up to run GUI related tests as indicated in this [Travis CI help page][3].

My `.travis.yml` file is now:

{% highlight ruby %}
before_install:
  - "export DISPLAY=:99.0"
  - "sh -e /etc/init.d/xvfb start"

script: bundle exec rake integration
{% endhighlight %}

It takes approximately 6 minutes for Travis CI to pull in the QT bindings but at least I now have continuous integration running on every push to GitHub.

[1]: http://www.qt.io/
[2]: https://github.com/ryanmelt/qtbindings/
[3]: http://docs.travis-ci.com/user/gui-and-headless-browsers/#Using-xvfb-to-Run-Tests-That-Require-GUI-(e.g.-a-Web-browser)
