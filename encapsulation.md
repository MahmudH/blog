Encapsulation Blog

Written by Edward and Mahmud.

### What is Encapsulation in Ruby?
Is concept of not overexposing your code. Not allowing other people to change or modify against the intent of the code.


Give an example of a poorly-encapsulated class that uses an attr_accessor
```ruby
class Person

  attr_accessor :name, :age

  def initialize name, age
    @name = name
    @age = age
  end
end
```

Explain why it is a poor example of Encapsulation

This a poorly encapsulated example because we can let the program do what we want but we also allowed it to be changed in ways we don't want.

For example, irb:

person = Person.new('Tim', 10)
person.name = 'Charles'
person.age = 15

person.name = 123
person.age = Person.new('Tim', 10)

Refactor the class to better use Encapsulation.
```ruby
class Person

  attr_reader :name, :age

  def initialize name, age
    @name = name
    @age = age
  end

  def set_name= name
    fail 'Not a string' unless name.is_a? String
    @name = name
  end

  def set_age= age
    fail 'Is not a number' unless age.is_a? Integer
    @age = age
  end
end
```

This is a good example of an encapsulated object because this class allows to only set the name to a string and age to an integer. And also to read name and age. This could be further encapsulated by making the attr_reader private.
