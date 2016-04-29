---
layout: post
title: "Let's build our own enum :)"
date: 2014-04-30
---
In this post we'll build our version of  [http://api.rubyonrails.org/v4.1/classes/ActiveRecord/Enum.html](Rails Enum). While our version will be less robust and won't cover nearly 100% of the real Rails Enum functionality, I believe it's a nice exercise in Ruby and Rails metaprogramming. Sometimes to gain real insight onto how Rails magic really works under the hood a good way is to try implemnting a piece of functionality on your own (better still - try to write a blog about it after implemnting something, I guarantee you will learn a lot).

If you're not already familiar with what Rails enums are please [http://api.rubyonrails.org/v4.1/classes/ActiveRecord/Enum.html](refresh your memory)
In a nutshell - Rails enums are a convenience to allow you to map integers to a collection of strings:

```ruby
class User < ActiveRecord::Base
  enum status: ['active', 'inactive', 'archived']
end

joe = User.first
joe.status
=>"active"

```
Did you notice the little magic? As you should know, the status field for User class is an integer(all enum fields must be integers), yet when we asked 'joe' what it's status was instead of returning '0'(which is what actually gets saved in the database) , Rails automagically converts 0 to the enum string value, which is 'active' in this case.



