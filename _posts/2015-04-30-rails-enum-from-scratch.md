---
layout: post
title: "Let's build our own enum :)"
date: 2014-04-30
---
In this post we'll build our version of [Rails Enum](http://api.rubyonrails.org/v4.1/classes/ActiveRecord/Enum.html). While our version will be less robust and won't cover nearly 100% of the real Rails Enum functionality, I believe it's a nice exercise in Ruby and Rails metaprogramming. Sometimes to gain real insight onto how Rails magic really works under the hood you have to try implement a piece of functionality on your own.

If you're not already familiar with what Rails enums are please [refresh your memory](http://api.rubyonrails.org/v4.1/classes/ActiveRecord/Enum.html), if you are please skip ahead.

In a nutshell - Rails enums are a convenience to allow you to map integers to a collection of strings:

```ruby
class User < ActiveRecord::Base
  enum status: ['active', 'inactive', 'archived']
end

joe = User.first
joe.status
=>"active" 

```
In the example above the class user has a field called status which is in integer (all enums are in fact integers). However, when you query for joe's status, Rails automagically returns the string 'active' instead of 0, the actually stored value. Rails simply remembers to match each integer value to it's place in the enum array (0 for active, 1 for inactive etc etc).
So Rails just made your life easier as an applicaiton developer by allowing you to work with strings instead of integer values (it's easier to ask if joe is active instead of asking if joe's status == 0 right?) yet still have the benefit of saving a lot of space in your database by not actually storing the strings themselves but lean integers instead.






