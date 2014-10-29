---
layout: post
title: "Method_Missing: Gone Girl Your Code"
date: 2014-10-29 07:58:15 -0400
comments: true
categories: 
---

Yes, Gone Girl is a verb. To avoid giving anything away, take it to mean to disappear, go absolutely mental, and return to an altered reality. Ruby has something similar: method_missing.

->![Gone Girl](http://media.giphy.com/media/5xtDarmb4oa1Jl01uik/giphy.gif)<-

Wonder how ActiveRecord creates those find methods on the fly? Method_messing. In fact, method_missing is a pillar of metaprogramming and is instrumental in the creation of DSLs. 

When a method is called, Ruby looks for the method in the instance methods, class methods, superclass methods, mixins, etc. Method_missing is the **last resort**.

This means right before Ruby throws a NoMethod error, you can catch it with method_missing.

To see how it works, let's see how Active Record's find_by* methods are created:

```ruby
class ActiveRecord::Base
  def method_missing(meth_sym, *args, &block) #1
    if meth_sym.to_s =~ /^find_by_(.+)$/ #2
      run_find_by_method($1, *args, &block) #3
    else
      super #4
    end
  end
```

1. Method_missing takes three parameters: the method name, splatted arguments, and then a block to run.
2. ActiveRecord is converting the method name into a string and then using Regex to match a find_by* pattern.
3. This is the black box where the find_by* method is actually defined. **When the method is defined, method_missing will no longer be called for that particular method name.**
4. Super allows Ruby to continue doing it's thing if the match did not happen.

Try it yourself:

```ruby
def method_missing(method, *arguments, &block)
  if method.to_s =~ /pattern_to_match/
    #This sends a method to your entire class. 
    #You can also use self.send to define 
    #only an instance method.
    self.class.send (:define_method, method) do
      # Your magic
    end
  else
    super
  end
end

#To ensure continuity in how Ruby treats methods, 
#you override the respond_to method Ruby has 
#with a match to your new method.
def respond_to?(method, include_private = false)
  method_id.to_s =~ /^what_is_[\w]+/ ? true : super
end
```

Go forth and catch those missing methods. Do not, however, Gone Girl.

<iframe width="100%" height="166" scrolling="no" frameborder="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/162832361&amp;color=ff5500&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false"></iframe>