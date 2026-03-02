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
> It is used to access properties and methods that belong to to the class.

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
### Key Points
- 
