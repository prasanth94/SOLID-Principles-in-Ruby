SOLID PRINCIPLES IN RUBY
------------------------

S.O.L.I.D STANDS FOR:

S – Single-responsiblity principle
O – Open-closed principle
L – Liskov substitution principle
I – Interface segregation principle
D – Dependency Inversion Principle

S – Single-responsiblity principle 


Applying these principles in programming will allow us to write better quality code and therefore be a better developer.

Single Responsibility Principle
-------------------------------

Every class should have a single responsibility, and that responsibility should be entirely encapsulated by the class.

Consider a class Person and every person has name, age, height and weight as attributes.

class Person
  attr_accessor :name, :age, :height, :weight
  def initialize(args)
    @name = args[:name]
    @height = args[:height]
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
    @height = args[:height]
  end
end

class BMICalculator
  def bmi_value(weight,height)
    weight / height**2
  end
end

Now BMICalculator class holds the logic for calculation of the BMI and Person class  only stores the info about person. This complies to the SRP, because, every class has it's own responsibility.


Open/closed principle
---------------------

One software entity (class/module) must be open for extension but closed for modification.

Let's see another example:

class Grade
  def report
    #logic_for_generating_grade_report
  end

  def print
  	report.to_json
  end
end

Here in this example, if we need to change the format of the grade report htats get printed, we need to change the code in the Grade Class, which is not a good practice.

class Grade
  def report
    #logic_for_generating_grade_report
  end

  def print(formatter)
  	formatter.format report
  end
end

In the above example, we are passsing the object of the type of the format you need to the Print method so that you dont want to change the code every time you need a new print format thus 


Liskov substitution principle
-----------------------------






