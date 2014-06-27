---
layout: post
title:  "Learning OOP with Cobbler"
date: 2014-06-27 14:04
categories: academy
---

While talking to a student today, I said "A class definition is like a recipe; you have to actually make the recipe before you have any cobbler."

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
    puts "Filling goes into the pan."
    @pan << @topping
    puts "Topping goes on top."
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


# make_cobbler.rb
require 'cobbler'
require 'filling'
require 'topping'

peachcobbler = Cobbler.new("peach")

peachcobbler.filling.cook
peachcobbler.filling.add_seasoning

peachcobbler.topping.biscuit

peachcobbler.assemble

peachcobbler.bake(3, 400)

peachcobbler.eat

{% endhighlight %}

I could eat so much cobbler right now.
