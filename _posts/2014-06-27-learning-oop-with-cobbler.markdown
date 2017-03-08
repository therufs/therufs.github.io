---
layout: post
title:  "Learning OOP with Cobbler"
date: 2014-06-27 14:04
categories: academy
---

While talking to a student today, I said "A class definition is like a recipe; you have to actually make the recipe before you have any cobbler."


There are many different types of cobblers, but they all start with a filling.

{% highlight ruby %}
# filling.rb

require 'active_support/inflector'

class Filling
  attr_reader :fruit

  def initialize (fruit)
    @fruit = fruit
  end

  def cook
    puts "Chop the " + @fruit.pluralize + " into bite-size pieces."
    puts "Using berries? No chopping required."
    puts "Put the fruit in a skillet and add sugar and lemon juice."
    add_seasoning
    puts "Bring to a boil, then simmer on low until the mixture is thick."
    puts "Don't forget to stir regularly to keep from scorching."
  end

  def add_seasoning
    case @fruit
    when "apple"
      puts "Add some cinnamon, nutmeg, and cloves."
    when "peach"
      puts "Add some fresh or dried ground ginger if you like."
    else
      puts "Add some spices if you feel like!"
    end
  end
end
{% endhighlight %}

Likewise, they all have a topping.

{% highlight ruby %}
# topping.rb

class Topping
  attr_reader :type

  def crunchy
    puts "To make crunchy topping:"
    puts "Combine oats, brown sugar, and butter to form a crumbly and delicious mess."
    @type = "crunchy"
  end

  def biscuit
    puts "To make biscuit topping:"
    puts "Follow the directions on the Bisquick box.  I'm not even joking."
    @type = "biscuit"
  end

  def brush_with_milk
    puts "Brush a little milk on top to give the biscuity goodness a nice sheen."
  end
end
{% endhighlight %}

All cobblers get assembled in pretty much the same way, too.

{% highlight ruby %}
# cobbler.rb

class Cobbler
  attr_accessor :filling, :topping

  def initialize(filling)
    @filling = Filling.new(filling)
    @topping = Topping.new
    @pan = []
  end

  def assemble
    @pan << @filling
    puts "Pour filling into the pan."
    @pan << @topping
    puts "Distribute topping evenly on top."
    if @topping.type == "biscuit"
      @topping.brush_with_milk
    end
  end

  def bake(time, temp)
    puts "Baking for " + time.to_s + " seconds at " + temp.to_s + " degrees F."
    sleep(time)
    puts "*********"
    puts "* DING! *"
    puts "*********"
    puts "The cobbler is ready! It's golden brown on top and bubbly underneath."
  end

  def eat
    puts "You decide to have some cobbler!"
    puts "The " + @filling.fruit + " cobbler is DELICIOUS."
  end
end
{% endhighlight %}

There's our recipe, and its sub-recipes. Now to actually make a cobbler!
'
{% highlight ruby %}
# make_cobbler.rb
require 'cobbler'
require 'filling'
require 'topping'

# We choose a fruit for our cobbler.
peachcobbler = Cobbler.new("peach")

# We cook the filling
peachcobbler.filling.cook

# Give it a nice biscuit topping
peachcobbler.topping.biscuit

# Assemble and bake! Not too long, or we'll get bored and forget.
peachcobbler.assemble
peachcobbler.bake(3, 400)

# TADA!
peachcobbler.eat
{% endhighlight %}

I could eat so much cobbler right now.
