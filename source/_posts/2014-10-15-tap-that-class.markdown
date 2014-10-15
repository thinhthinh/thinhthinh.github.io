---
layout: post
title: "Tap that Class"
date: 2014-10-15 07:25:18 -0400
comments: true
categories: "Ruby", "Programming", "Flatiron School"
---

The Tap method reminds me of Nightcrawler, the furry indigo teleporter from the Marvel Universe. He appears out of nowhere, kicks ass, and then disappears in a puff of smoke. 

<center>
![Nightcrawler teleports](http://24.media.tumblr.com/3ffc21146868e5951dd7e686d4fe9cbe/tumblr_mgr6utyoY31qfhq48o9_r2_250.gif)</center>

The Tap method, born in Ruby >= 1.9, is a helper method that yields a block on your object and returns the object. As a method, it looks like this:

<pre><code>class Object
  def tap
    yield self
    self
  end
end
</code></pre>

This is especially useful when you are creating new classes because it allows you to assign properties from the get-go.

<pre><code>nightcrawler = Hero.new
nightcrawler.name = "Nightcrawler"
nightcrawler

#with tap
nightcrawler = Hero.new.tap{|h| name = "Nightcrawler"}
</code></pre>

When you have many properties to set, this allows you to group all methods in an easy-to-read tap block.

<pre><code>nightcrawler = Hero.new.tap do |h|
  h.name = "Nightcrawler"
  h.power = "teleportation"
  h.train_under_xavier
  h.runaway
  h.redemption
  h.anything_else_you_want
end
</code></pre>

Refactoring with tap can aid in readability. However, overdoing it with the tap blocks may result in the opposite. With great power, comes great responsibility.

Superpowers in mind, here's the latest track from UK electro-duo Alunageorge. Goodbye for now.  

<iframe width="100%" height="166" scrolling="no" frameborder="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/170305212&amp;color=ff5500&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false"></iframe>