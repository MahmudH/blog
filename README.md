# SRP_blogpost

A blog post by Mahmud and Ivan

Single Responsibility Principle is a design principle that states that the functionality of a class should have one, and only one, specific functionality.

To illustrate this, we are going to compare our approaches to the airport-challenge we took at the weekend.

Objects  | Messages
------------- | -------------
Airport  | Calls plane to land
Plane  | Can land

*Snippet from Mahmud's Airport class*
```ruby
  def land(plane)
    fail 'The airport is full' if full?
    fail 'Is stormy so cannot land' if stormy
    plane.land
    @planes << plane
  end
```
*Snippet from Ivan's Airport class*
```ruby
  def land(plane)
    fail 'The airport is full' if full?
    fail 'Is stormy so cannot land' if stormy
    plane.flying = false
    @planes << plane
  end
```
In Ivan's code the land method located in the Airport class does two things - it modifies the @planes variable and sets the flying status of the instance of plane to false. This violates the single responsibility principle.

In Mahmud's code the land method, again located in the Airport class, modifies the @planes variable and calls the plane's land method, which is located in the Plane class. This method changes the instance of plane's flying status to false, but occurs within the Plane class.

In this latter way, We understand that the airport is responsible to call the plane to land but not change the inner workings on the plane itself.
