SOLID PRINCIPLES IN RUBY
------------------------

S.O.L.I.D STANDS FOR:

S – Single-responsiblity principle 

O – Open-closed principle

L – Liskov substitution principle

I – Interface segregation principle

D – Dependency Inversion Principle



Applying these principles in programming will allow us to write better quality code and therefore be a better developer.

Single Responsibility Principle
-------------------------------

Every class should have a single responsibility, and that responsibility should be entirely encapsulated by the class.

Consider a class Person and every person has name, age, height and weight as attributes.

class Person
  attr_accessor :name, :age, :height, :weight
  def initialize(args)
    @name = args[:name]
    @age = args[:age]
    @height = args[:height]
    @weight = args[:weight]
  end

  def bmi_calculation
    weight / height**2
  end
end

This is not a good way of coding as Person class contains the logic that calculates BMI of that person.The responsibility of Person is to hold info/logic about the Person, not the BMI. 

class Person
  attr_accessor :name, :age, :height, :weight
  def initialize(args)
    @name = args[:name]
    @age = args[:age]
    @height = args[:height]
    @weight = args[:weight]
  end

end

class BMICalculator
  def bmi_value(weight,height)
    weight / height**2
  end
end

Now BMICalculator class holds the logic for calculation of the BMI and Person class  only stores the info about person. This complies to the SRP, because, every class has it's own responsibility.





