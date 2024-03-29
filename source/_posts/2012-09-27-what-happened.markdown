---
layout: post
title: "What happened?"
date: 2012-09-27 00:15
comments: true
categories: [personal] 
---

Been awhile
-----------
Sorry was away, been busy. Setup and migrated my old blog posts
over to octopress and hosting it on Linode.com. Some of the older
blog posts may should double titles. The migration script I used
automatically added them and eventuall I'll get to cleaning
them up. With that I've been messing around with some Ruby 
to wrap my head around it and hopefully get some Rails 
development going for certain projects.

Lately, I've started noticing a disconnect in services making
it difficult for people to decide what products they should pay
for in developing a web application. I feel the common items
should be included in whatever platform you decide to go with.
For example, wufoo.com provides a Form building service. While
they are good at what they provide I don't entirely agree with
making this a service that requires any type of payment. The
limit is 3 forms for their free account and once those are used
up it starts at $15/mo. These are simple forms with a pretty UI
for building.

Simply put, this is not a service that should require payment
to build. This falls under a notable feature of a bigger product
along with convenience of having it all accessable through a single
interface. I realize there is an API provided for their service, but,
there again it'll cost you additional fees if you need to do anything
more than simple contact forms.

Writing Ruby plugins
--------------------
I was searching around for helpers for building gems for Ruby.
Come to find out it isn't that difficult to write a gemspec, however,
I did find an interesting application that pretty much acts in a sane
way when building a Ruby gem. [gem-this][] Pretty sweet little application
as it doesn't add a bunch of less than useful files and pretty much sticks
to the convention of keeping everything in a Rakefile and having that
generate your gemspec during build. Not a bad idea and I like gem-this
simplicity when it comes to building documentation, adding binaries, little-to-no
learning curve, and overall keeping simple tasks simple.

``` bash Installing **gem-this** is pretty straight forward
$ gem install gem-this
```

One of the best things about gem-this is that it works on existing projects.
You'd be suprised how many of these gem helpers require building a new project
and including them as dependencies :\

``` bash Generating gem specifics
$ gem-this .
```

It'll append to your existing Rakefile or create a new one. Gemspecs are then
generated with a rake task.

``` bash
$ rake gemspec
```

Other little nice things are including rdoc support and building into its own
directory for easy cleanup.

``` bash
$ rake gem
```

[gem-this]: https://github.com/lazyatom/gem-this
