---
layout: post
title: "Taking a stab at sinatra"
date: 2012-09-28 00:13
comments: true
categories: [ruby, sinatra, oauth]
---

And it is not going well, if anyone has any idea what I am missing
that would be saweet.

Stackoverflow posted here: [clicky][so-ruby-fail]

I've gotten as far as getting a strategy extended in omniauth but
launchpad's oauth documentation is pretty bare and I don't think its
been given much love recently. I know there is a launchpadlib python
library, however, this is ruby so that is out of the question :)

[so-ruby-fail]: http://bit.ly/QzKmaH

### Update

Decided to take a simpler approach and use simple_oauth and put
together my own query strings for the authentication. Still a work in
progress and doesn't really do much at this moment.
