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

Classes that are derived must be substitutable fro their base class i.e if S is subclass of T then objects of type T may be replaced with objects of type S.

class Vehicle
  def start
  	Vehicle started
  end

  def stop
  	Vehicle stopped
  end
end

class Car
  def start
  	Car started
  end

  def end
    Car stopped
  end
end


In the above example, Vehicle and Car classes have the same interfaces and hence we can substitute the subclass with base class like below.

car1 = Vehicle.new
car2 = Car.new

So by knowing the interface of a vehicle we can find out the interfaces of class Car.


Interface segregation principle
------------------------------

A client should not be depend on a class, that has an interface, that client does not use.
If it depends, then client should be modified everytime when there is a change in the class.

In the below example rating_value method in Employee class is partially used by class SoftwareEngineer and class Intern which should be done according to Interface segregation principle. 

class Employee
  def salary_value
  	#Calculate salary logic
    return salary
  end

  def rating_value
    #calculate rating
  	return rating
  end

  def training_grade
    #Calulate training grade
    return grade
  end
end


class SoftwareEngineer < Employee
  def details
    @employee.salary_value
    @employee.rating_value
  end
end

class Intern < Employee
	def details 
	  @employees.training_grade
	end 
end

In order to avoid this bad practice we can split the interface in to two as shown below.

class Employee
  def salary_value
    return salary
  end

  def rating_value
  	return rating
  end

end

class SoftwareEngineer < Employee
  def details
    @employee.salary_value
    @employee.rating_value
  end
end

class Trainee
  def training_grade
    #Calulate training grade
    return grade
  end
end

class Intern < Trainee
	def details 
	  @trainee.training_grade
	end 
end










