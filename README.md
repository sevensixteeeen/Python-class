# Python OOP

>## What is OOP?
>OOP stands for Object-oriented programming.
>Python is an object-oriented language, allowing you to structure your code using classes and objects for better organization and reusability.

## Advantages of OOP
- provides a clear structure to programs.
- Make code eaier to maintain,reuse and debug.
- Helps keeps code clean by avoiding repetition (Dont't repeat by slef principle)
- Allows to build reusable applications with less code.

## What is Classes and Object?
Classes and object are two code concepts of OOP.
Class defines what an object should look like, and object is created based on class
```
ex:
Class                     Objects
fruits:                   Apple, pineapple, berry
cars:                     BMW, Dodge, Land Rover
```

After creating Objects from a class,it inherits all the variables and functions defined inside that class.

## Python __init__ Method
>All Classes have a built-in method called __init__ , it execute when the class is being **initiated**
>it used to assign values to object or perform operations that are necessary when the object is being created.

**ex:**
```Python
class person:
    def __init__ (self,name,age):
        self.name=name
        self.age=age


n=input("enter the name")
a=int(input("enter the age "))
p1= person(n,a)


print(" Name of the person: ",p1.name)
print(" Age of the person: ",p1.age)
```
---

### key points
- without initiated method, it need to set properties manually for each object. 
- It also use default values for parameters in the initiated method.
- It can have as many parameters as we need.

## Python self parameter
> The self parameter is a reference to the current instance of the class.
> It is used to access properties and methods that belong to the class.

**Ex:**
```Python
class people:
    def __init__(self,name,age):
        self.name=name
        self.age=age
        
    def greet(self):
        print("helooo, i'am",self.name, "and i am",self.age,"year old")

n=input("enter the name")
a=int(input("enter the age "))
p1= people(n,a)
p1.greet()
```
---

### Key points
- Without **self**, Python would not know which object's properties you want to access.
- Self doesn't have to be named self, you can call it whatever you like, but it has to be the first parameter of any method in the class.
- accessiblity of any property of the class using **self**.
- by using self it can also call other method.
---

## Python class properties
>properties are variables that belongs to class. they store data for each object created from class.
**Ex:**
```Python
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

p1 = Person("Emil", 36)

print(p1.name)
print(p1.age)
```
---
### Key Points
- properties objects are accessable using dot notation.
- properties values can be modify on object.
- deletable using del keywords.

## Class Properties Vs Object Properties
**Class properties** belong to the class itself. they shared across all objects created from class. if you change a class properties, the change is reflected in every instance(unless the instance overrides it.)

**Object properrties** belong to a specific instance of the class. they are unique to each object, so changing one object's property does not affect others.

**Ex:**
```Python
class Person:
  species = "Human" # Class property

  def __init__(self, name):
    self.name = name # Instance property

p1 = Person("Emil")
p2 = Person("Tobias")

print(p1.name)
print(p2.name)
print(p1.species)
print(p2.species)
---

class Car:
    wheels = 4  # class property

    def __init__(self, brand):
        self.brand = brand  # object property

car1 = Car("Toyota")
car2 = Car("Honda")

print("no. of wheels in cars are ",Car.wheels)   # 4 (class property)
print("Barnd name: ",car1.brand)   # Toyota (object property)
print("Barnd name: ",car2.brand)   # Honda (object property)

Car.wheels = 6
print("no. of wheels in cars are ",car1.wheels)  # 6 (shared change)
print("no. of wheels in cars are ",car2.wheels)  # 6 (shared change)
```
---
##Key points
- During modifying class property, it affects all objects.
- we can add new property to existing objects.

## Class methods 
Methods are functions that belong to a class. They define the behavior of objects created from the class.

**Ex:**
```Python
class Person:
  def __init__(self, name):
    self.name = name

  def greet(self):
    print("Hello, my name is " + self.name)

p1 = Person("Emil")
p1.greet()
```

Note: All methods must have self as the first parameter.

---

### Key points
- Method can be accept parameters just like regular function.
- Methods can access and modify object properties using self.
- Methods can modify the properties of an object.
- The __str__() method is a special method that controls what is returned when the object is printed.
- A class can have multiple methods that work together.
- You can delete methods from a class using the del keyword.

## Python inheritance
inheritance allows us to define a class that inherita all the methods and properties from another class.

**Parent class** is the class being inherited from, also called base class.

**Child class** is the class that inherits from another class, also called derived class.

###creating a parent class
```Python
class Person:
  def __init__(self, fname, lname):
    self.firstname = fname
    self.lastname = lname

  def printname(self):
    print(self.firstname, self.lastname)

#Use the Person class to create an object, and then execute the printname method:

x = Person("John", "Doe")
x.printname()
```

---

## Add the __init__() function 
So far we created a child that inherits the properties and methods from its parent.
We want to add the __init__() function to the child class (instead of the pass keywords)

**NOTE:** The __init__() function is called automatically every time the class is being used to create a new object.)

**Ex:**
```Python
class Person:
  def __init__(self, fname, lname):
    self.firstname = fname
    self.lastname = lname

  def printname(self):
    print(self.firstname, self.lastname)

class Student(Person):
  def __init__(self, fname, lname):
    Person.__init__(self, fname, lname)

x = Student("Mike", "Olsen")
x.printname()
```

---

More functions
- Super function: Python also has a super() function that will make the child class inherit all the methods and properties from its parent. By using the super() function, you do not have to use the name of the parent element, it will automatically inherit the methods and properties from its parent.


## Python polymorphism 
The Polymorphism means "many forms", and in programming it refers to methods/functions/opertors with the same name that can be executed on many objects or classes.

### Function polymorphism 
- **len():** for string len returns the number of characters.
- **tuples** len() returns the number of items in the tuple.
- **dictionaries** len() returns the number of key/value pairs in the dictionary.


## class polymorphism 
Polymorphism is often used in Class methods, where we can have multiple classes with the same method name.
For example, say we have three classes: Car, Boat, and Plane, and they all have a method called move():

**Ex:**
```Python
class Car:
  def __init__(self, brand, model):
    self.brand = brand
    self.model = model

  def move(self):
    print("Drive!")

class Boat:
  def __init__(self, brand, model):
    self.brand = brand
    self.model = model

  def move(self):
    print("Sail!")

class Plane:
  def __init__(self, brand, model):
    self.brand = brand
    self.model = model

  def move(self):
    print("Fly!")

car1 = Car("Ford", "Mustang")       #Create a Car object
boat1 = Boat("Ibiza", "Touring 20") #Create a Boat object
plane1 = Plane("Boeing", "747")     #Create a Plane object

for x in (car1, boat1, plane1):
  x.move()
```
---
>Look at the for loop at the end. Because of polymorphism we can execute the same method for all three classes.

## Inheritance Class Polymorphism 
What about classes with child classes with the same name? Can we use polymorphism there?

Yes. If we use the example above and make a parent class called Vehicle, and make Car, Boat, Plane child classes of Vehicle, the child classes inherits the Vehicle methods, but can override them:

**Ex:** 
```Python
class Vehicle:
  def __init__(self, brand, model):
    self.brand = brand
    self.model = model

  def move(self):
    print("Move!")

class Car(Vehicle):
  pass

class Boat(Vehicle):
  def move(self):
    print("Sail!")

class Plane(Vehicle):
  def move(self):
    print("Fly!")

car1 = Car("Ford", "Mustang")       #Create a Car object
boat1 = Boat("Ibiza", "Touring 20") #Create a Boat object
plane1 = Plane("Boeing", "747")     #Create a Plane object

for x in (car1, boat1, plane1):
  print(x.brand)
  print(x.model)
  x.move()
```
---
Child classes inherits the properties and methods from the parent class.

In the example above you can see that the Car class is empty, but it inherits brand, model, and move() from Vehicle.

The Boat and Plane classes also inherit brand, model, and move() from Vehicle, but they both override the move() method.

Because of polymorphism we can execute the same method for all classes.

## Python Encapsulation
>Encapsulation is about protecting data inside a class. It means keeping data (properties) and methods together in a class, while controlling how the data can be accessed from outside the class,This prevents accidental changes to your data and hides the internal details of how your class works.

##Private properties
In Python, you can make properties private by using a double underscore __ prefix:
**Ex:**
```Python
class Person:
  def __init__(self, name, age):
    self.name = name
    self.__age = age  # Private property

p1 = Person("Emil", 25)
print(p1.name)
print(p1.__age)  # This will cause an error
```

Note: Private properties cannot be accessed directly from outside the class.

##Get private property value
To access a private property, you can create a getter method:

**Ex:**
```Python
class Person:
  def __init__(self, name, age):
    self.name = name
    self.__age = age

  def get_age(self):
    return self.__age

p1 = Person("Tobias", 25)
print(p1.get_age())
```


