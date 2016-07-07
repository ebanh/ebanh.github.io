---
layout: post
title:  "Class vs Instance #methods and variables"
date:   2016-07-06 04:29:46 -0400
---


We've all seen them and used them throughout the course, but it can be confusing knowing when to use one vs the other. I know I've had this issue, many times just relying on tests to tell me if I should put the 'self.' on that method.

Eventually it starts to get clearer, or maybe it's pretty clear and I'm just slow :P. Anyways, after an assessment with Avidor and quite a few hours redoing my Music Library CLI lab, things started to click.

Let's start with class vs instance variables: 

    @songs

A single @ indicates an instance variable. This is a variable that can only be used by each artist instance. For example, **bob's** @songs only include 'happy dance' and 'run', while **frank's** @songs only includes 'jump' and 'lamp'. Both artists have an instance variable named @songs, but neither artist can see the other's songs.

    @@all

@@ indicates a class variable. This variable can be accessed and used by each of the individual artist instances. If we create a new artists and want to save it to @@all, we can, because this is an class variable. Class variables are usually defined in the overall class, but can also be defined in a class #method.

Class vs Instance #methods:

It's really just understanding the difference between a class and an instance. Once you know this, its just a matter of knowing which you're working with. We know that the Artist class is a template a sorts, defining each artist's properties and what actions it can take, while each artist is an individual instance of that class. 

When we build a #method we need to consider what we're trying to interact with, is it the individual artist, like adding a song to a specific artist, or are we trying to interact with the overall collection of Artists?

If we have the following:

      def self.all
        @@all
      end
     
      def save
        @@all << self
      end

Which is correct?

      def find_by_name(name)
        self.all.detect { |n| n.name == name }
      end

OR

      def self.find_by_name(name)
        self.all.detect { |n| n.name == name }
      end

Let's start with the first #method above:

      def self.all
        @@all
      end
      
We have an advantage with this one. The class variable @@all, which will contain each artist instance, gives us a hint that this should be a class #method. Each artist should be able to access this variable.
Example: **Artist**.*all*
*This is will return an array of all the artist's instances*

      def save
        @@all << self
      end
      
Now why is our #save method an instance method? We need to be able to call this method on each artists object we create, so we can save it to our class variable. 
Example:  **frank**.*save*  
*This will save the artist instance of frank to the the @@all class variable.*

The #find_by_name method is looking over our class variable @@all  through the #self.all method to find a particular artist instance. This is not a method we would call on **frank** or **bob**, but we would call it on our class **Artist**. This is a class method and the correct answer is:

      def self.find_by_name(name)
        self.all.detect { |n| n.name == name }
      end

Example: **Artist**.*find_by_name*(frank)

I hope this has helped clear up when to use a class vs instance #method and the differences between class and instance variables. 
