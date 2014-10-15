---
layout: post
title: "Tap that Class"
date: 2014-10-15 07:25:18 -0400
comments: true
categories: "Ruby", "Programming", "Flatiron School"
---

The Tap method reminds me of Nightcrawler, the furry indigo teleporter from the Marvel Universe. He appears out of nowhere, kicks ass, and then disappears in a puff of smoke. 

![Nightcrawler teleports](http://24.media.tumblr.com/3ffc21146868e5951dd7e686d4fe9cbe/tumblr_mgr6utyoY31qfhq48o9_r2_250.gif)

The Tap method, born in Ruby >= 1.9, is a helper method for that yields a block on your object and returns the object. If it was a method, it looks like this:

<pre><code>
class Object
  def tap
    yield self
    self
  end
end
</code></pre>