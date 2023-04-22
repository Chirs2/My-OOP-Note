# Object Oriented Programming Note
---

__What is OOP?__

A prgramming practice that focus on definition more than input value to design a reuseable software systems with creation of class. The goal is to create an object that we can define and provide functionality to solve problems.

1. __Obejct__ 

    * A combination of data and functional code. This is because real-world objects have states and behaviour.
    * An object is an intance
    * States: The characteristic, Measurable data of an object
    * Behaviour: The available functionality of the object (what can it do?)
    * Object’s Data → called: attributes
    * Object’s Code → called: methods

    Example - dog
    
    | Dog may have the following attributes | Dog may have the following methods |
    | ------------------------------------- | ---------------------------------: |
    | Name                                  | bark()                             |
    | Color                                 | eat()                              |
    | Breed                                 | sleep()                            |
    | isHungry                              |                                    |
    | isThirsty                             |                                    |

2. __Class&Object__
   
   *Class* is an abstract description of all objects that can be made from this set class where an object can be instantiated from.A Class Contains _Attributes_
   
   *Attributes*: An Object’s accessible tools
      1. Fields: Variables that belong to an object or a class
        
        Type 1: It belongs to the instance of the class
        
        Type 2: It belongs to the class itself
      2. Methods: Functions that the object or the object can call
  
  Example: 
  ``` pythonscript
    # The Most Basic Class

      class ClassName: # Notice that Class names are capitalized
	        pass # An Empty Block
        #end of ClassName

      obj = ClassName()
      print(obj) 
      obj = ClassName()
  ```
  
   Creating a Method for a Class example
   ``` pythonscript
    class Person:
	  def greet(self):
		print(‘Hello, how are you?’)
	  #end of greet
	  #end of class Person
	  p = Person()
	  p.greet() # outputs the greet message
   ```
3. __The __init__ method & self parameter__

    def __init__(self): → The __init__ method
  
    * The initialization method is executed as soon as an object of the class is instantiated.
    * It helps us to do any initialization for the object’s attributes.
    * self parameter is used to denote that the method is applied and accessible for the object itself.  
    * self will also treat its own attributes as local.

Example
``` python script
  class Person:
	  def __init__(self, name):
		   self.name = name
	    #end of initialization
	  def greet(self): # the self parameter is always required
		   print(“Hello, my name is”, self.name)
	#end of greet
  #end of class Person

  p = Person(‘Mr. Park’)
  p.greet()
``` 

4. __What is Encapsulation?__
    * Information Hiding: Restricting the access to the classes/objects’ certain attributes and methods.
    * In Python, this isn’t really possible: hence we use a special system. → We hide attributes and methods by using a double underscore __ as a prefix. 
    * Data Protection
    * Restricting certain methods to be callable

Example: 
``` Python Script
class Student:
  def __init__(self,nameF, nameL, num):
    self.firstName = nameF
    self.lastName = nameL
    self.__studentNumber = num

#end of Student

s1 = Student("Mr.", "Park", 10)
print(s1.firstName) # Returns/Outputs “Mr.”

s1.firstName = "Ms."
print(s1.firstName) # Returns/Outputs “Ms.”
```
5. __Overrides__
    * _Overloading_: Two methods in one class that have the same method name, but different parameters. No Overloading in Python 3
    * _Overriding_: Two methods with the same method name and parameters.
      * One method is in the parent class (lesson 3)
      * One method is in the child class (lesson 3)
      * Overriding allows the child class to provide specific implementation for a method that exists in the parent class
      * You can also override built-in magic-methods. OR Base-functions

6. __Polymorphism__
    * Polymorphism: A method that can be used across different classes and object that is dependent on the parameters.
      Poly → Many
      Morphism → Forms
    * Ideas:
        * Different Classes (non-inherited) can have the same named methods (Simple) → Polymorphism.
        * Within a set of inherited classes have the same methods.

Example:
``` Python Script
class Bear:
    def sound(self):
        print("Groarrr")
 
class Dog:
    def sound(self):
        print("Woof woof!")
 
def makeSound(animalType):
    animalType.sound()

bearObj = Bear()
dogObj = Dog()
 
makeSound(bearObj)
makeSound(dogObj)
```

7. __Base Overrides__
    We can have:
      * Two different classes have a same attributes and methods
      * A child of a parent have an overrided method where the child would utilize the method differently.
    These are the two fundamental concepts of overriding and polymorphism in Python.
    If we we can override a built-in methods/operators that we use in Python 3 as well for our own objects.
    _Benefits_:
      Can start to complete mathematical operations on custom Objects
      Can start to compare equality between custom Objects
    Therefore: We can start to manipulate how the Object behaves when met with built-in methods and operators

Example
``` Python Script
class Dog:
	def __init__(self,name):
		self.__name = name
	
	def __str__(self):
		return “Woof, I’m %s.” % self.__name

corgi = Dog(“Tobasco”)
print(corgi) → “Woof, I’m Tobasco.”
```

8. __ __repr__() base function __
    
    When we try to make our custom objects printable, we actually need to override _ __repr__ _ and _ __str__ _
   
    _ __repr__ _→ Allows us to present a printable version of our object
    
    _ __str__ _ → Allows us to convert our object to a string

<img width="824" alt="截屏2023-04-21 下午9 09 48" src="https://user-images.githubusercontent.com/66268852/233753877-20ff34bb-f947-4c64-acdb-2052ea06d1b3.png">

9. __What is Inheritance?__
    _Inheritance_: When an object or class is based on another class; where its features are from a parent class

    _Types_:

      _Single Inheritance_: A subclass inheriting the features of a single superclass / parent class

      _Multiple Inheritance_: A subclass inheriting the features of a multiple parent classes

      _Multilevel Inheritance_: A subclass is inheriting from another subclass… A → B → C
  
     Inheritance can have an hierarchy (branching like a tree) and/or be a hybrid: mixing the types of inheritances

Example
``` Python Script
 class Person:
  def __init__(self, name):
  	self.__name = name 
  
  def getName(self):
    return self.__name
 
 class Student(Person):
  def __init__(self, name, num):
    Person.__init__(self, name)
    self.__sNum = num
  
  def getStudentName(self):
    return("%s: %s" % (self.__sNum,self.getName()))
p = Person(“Mr. Park”)
s = Student(“Random Child”, “1234”)
print(p.getName()) # Output: “Mr. Park”
print(s.getStudentName(), “and” , s.getName()) # Output: “1234: Random Child and Random Child”
```

10. __What is super()?__
    super() → is a built-in method for classes to refer their parent class
      This prevents us from doing ParentClass.method(self)
      The self with self gets confusing… 

Example
``` Python Script
class Person:
  def __init__(self, name):
  	self.__name = name 
  
  def getName(self):
    return self.__name
class Student(Person):
  def __init__(self, name, num):
    super().__init__(name)
    self.__sNum = num
  
  def getStudentName(self):
    return("%s: %s" % (self.__sNum,self.getName()))

p = Person(“Mr. Park”)
s = Student(“Random Child”, “1234”)
print(p.getName())
print(s.getStudentName(), “and” , s.getName())

```
11. __Iterable Objects__
      
      Iterable Objects: Objects that we can iterate through like a sequence.
      
      Examples: Strings & Lists (sets and dictionaries too)
      
      Recall that we could iterate through Strings and Lists
      
      To access individual values without indexing, we were able to use for loops
      
      Note:
        
        The portion of the iterable object must be a sequence
        
        Iterable doesn’t always mean indexable
        
  

