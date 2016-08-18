---
layout: post
title:  "Beware the magic! (Active Records/ Sinatra)"
date:   2016-08-18 07:40:44 +0000
---


Moving into the ActiveRecords/ Sinatra portions of the course is a little like walking into an open field after weeks/ months in a dark forest. Ok, that may be a bit overstated, but you're suddenly able to step back and abstract away the drudgery of writing many of your class methods.

Going from (partial example)

```
class Song
  attr_accessor :name, :artist, :genre
  @@all = []

  def initialize(name, artist = nil, genre = nil)
    @name = name
    self.artist = artist if artist
    self.genre = genre if genre
  end
  def self.all
    @@all
  end

  def self.destroy_all
    @@all.clear
  end

  def save
    @@all << self
    self
  end

  def self.create(name, artist = nil, genre = nil)
    new(name, artist, genre).save
  end
end
```

To this:

```
class Song < ActiveRecord::Base
end
```

--note: Its not a direct comparison of methods, ActiveRecords has you using a database, while the other isn't.

And if you need to add associations?

```
class Song < ActiveRecord::Base
  belongs_to :artist
  has_many :genres
end
```

I can call methods like #create(data) or #find_by(data) just by having my class inherent from ActiveRecord::Base. It's really pretty cool, though sometimes I worry that I may forget how to write those methods by hand.. I guess it's sort of like learning math equations by hand, then picking up a calculator that can do it for you with just a few button pushes. Perhaps after a while, my feeling of wonder will fade, but right now I still think this is magic.

I found it pretty easy to rely on these built in methods, to a point where I found myself trying to use them to solve all of my problems. They can't. I found this out while trying to complete the Sinatra-playlister lab. Sometimes you just have to iterate through the database, especially if you need to modify the data stored in there to make a proper comparison. Before being gently reminding that we wrote our own methods before ActiveRecords, I spent hours trying to make the built in methods do something they just can't.

Enjoy the magic, but don't let it blind you to all the other tools you have to solve whatever problem comes your way!




