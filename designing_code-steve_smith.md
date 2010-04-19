# Designing Code: Beautiful, simple, and usable text
  **bold**[Slides](http://www.slideshare.net/orderedlist/designing-code)

## Presenter 
   ![Steve Smith](http://farm5.static.flickr.com/4030/4533226349_99338ee20a.jpg "Steve Smith")   
   [Steve Smith](http://orderedlist.com/who-we-are/)  
   [Ordered List](http://orderedlist.com/)   
   [@orderedlist](http://twitter.com/orderedlist)   
   [steve@orderedlist.com](mailto:steve@orderedlist.com)   

## Focus
   How can we apply traditionally visual design concepts to code?   
   Design is not just visual, it's a thought process.   

## Why design your code?
   Reasons to care about beauty   

   * "Design is the application of intent... an antidote to accident" - Robert L Peters
   * Design is intentional.
   * Accident == Bug!

   So, good design reduces bugs.  

### Sanity   
   Design for your own sanity.  Your sanity is underrated.  Keep
   yourself sane, and make it more pleasant for yourself to code. 

### Growth
   Design for future growth.  Growth also applies with respect to how
   many people will work on the code. 

   Six months from now, you will be a different person, with different skills, thought
   processes...  Design for your future self. 

### User Experience
   Sometimes we are the end user (the ones using the code.)  Sometimes
   it's the public (using an API.)  Sometimes it's devs on our team.
   Sometimes it's open source!  Other devs are the user.  Think about
   the entire user-experience up front, and let your design reflect
   that.  

** Balance
   Alignment and order

   We will constantly learn how to do this better.

   Balance, using grids, to increase scan-ability.  Make it fun and
   easy to read.  

   If things are balance (eg table, vs csv) it's easier to read and
   work with.

   Look at the code 'outside' of what it does, and look at it
   aesthetically, get a 'feel' for it.

   NOT:
   foo = bar
   foobar = foobarbaz
   foobazbar = barboofaz

   BUT:
   foobar    = foobarbaz
   foobazbar = barboofaz
   foo       = bar

   NOT:
   def foo
     some dumb stuff
   end

   def bar
     soem more dumb stuff
   end

   BUT:
   def foo; some dumb stuff;      end
   def bar; some more dumb stuff; end

   "The waterfall commit"

   Clean Code:
   descriptive method names
   do one thing

** Clarity
   Simplicity and Understanding

   Writing clear code so we can read & understand it, visually and
   literally.

*** Clarify using consistent names.

   class Post
     key :title, String
   end

   class Category
     key :name, String
   end

   class Theme
     key :moniker, String
   end

   ... fail. (is it title? name? moniker?)

   Look through files to determine whether a naming convention already
   exists.  If so, follow it.  Consistency of method naming, etc.

   class User
     key :inactive, Boolean, :default => false
   end

   that is declaring in the negative... confusing!

   def active?; !inactive?; end

   def activate!; self.inactive = false; end

   BETTER:
   use positive grammar

   class User
     key :active, Boolean, :default => true
   end

   def inactive?; !active?; end

   def deactivate!; self.active = false; end

*** Clarify using method description
    Avoid complex conditionals

    def do_something
      if foo? && foo == bar && baz != bah
      do stuff
    end

    extract the conditional into its own method
    def do_something
      if conditions_met?
      do do stuff
    end
      
    def conditions_met?
      if foo? && foo == bar && baz != bah
    end
   
** Harmony
   Integration and experience

   Developing desiging and writing your code so it work cohesively and uniformly.

*** Harmonize with Integration
Magic sucks.  

We shouldn't have to sift through other people's code to find out
where things are happening...

Write our code so the end user application can hook into our code when
it needs to, where it wants to, and we can leave the rest of their
application alone!  (Extension, not modification) 

*** Harmonize with User Experience
    We don't consider the user experience before we jump into coding. 

    When Steve starts a design, he writes ideas on a sketchpad, about
    how it should look overall.  It's a general concept of how it
    should look and be used. 

    John will describe how he wants the API to look, and be used by
    the end user.  (With syntax.)

    "Simplicity does not precede complexity, but follows it" - Alan
    Perlis

    We have to work really hard to make things simple:

    Nested page title

    <title>
      Project Title - Portfolio - Ordered List
    </title>

    First thought:
    item.breadcrumb

    The item, and any parents that are not the homepage, then the site
    itself. 

    <title>
      {{ item.breadcrumb | map: 'title' | join: ' - ' }}
    </title>

    ... They would have to remember that EVERY time for every page.

    Next thought:
    TOO MUCH CODE

    Rather than thinking about what they could supply and how it could
    be used, they thought about how they wanted to use it, and how
    they could provide it.

    {% title '//' }

    (where '//' is separator)

    It wasn't difficult to write, but made the UX much better.  They
    got there by thinking about how things should look to the user.
    
** Wrap Up
   Write, then simplify, then write, then simplify.

   Make it work, make it elegant, make it fast.

   Clean Code: "nobody writes functions like this"

   Refactoring is good for the soul.

*** Before you write your code
    Design the experience
    Happy developers are good developers; if you contemplate suicide
    every time you open your text editor, you probably need to
    refactor (or you're not going to be very productive.)
    Good tests help here.

*** Simplicity wins
    Steve has never met anyone that said "I wish this product were
    more complex."  They ask for features, but never complication.

    Think through the design and how to simplify visually,
    programmatically, and how in terms of experience.
    
** Questions
*** Steves heroes of good code:
   John Nunemaker
   Rick Olsen

   
*** Objections to writing good code
    "I don't have time..."
    In the 15 minutes at the end of the day, you're not going to write
    great code anyway.  Spend that time cleaning up shop.

    It's the codewise equivalent of a clean versus a messy desk. 
    "The psyche of order is more productive... The less clutter
    visually and conceptually, the better." - Steve Smith.

