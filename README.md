# Python OOP

OOP stands for Object-Oriented Programming. Python is an object-oriented language, letting you structure code using classes and objects for better organization and reusability.

---

## 1. What is OOP?
OOP is a way of structuring programs around **classes** (blueprints) and **objects** (instances built from those blueprints), instead of just functions and data floating independently.

## 2. Advantages of OOP
- Provides a clear structure to programs
- Makes code easier to maintain, reuse, and debug
- Keeps code clean by avoiding repetition (the "Don't Repeat Yourself" principle)
- Lets you build reusable applications with less code

---

## 3. Classes and Objects
Classes and objects are the two core concepts of OOP. A class defines what an object should look like, and an object is created based on a class.

| Class | Objects |
|---|---|
| Fruit | Apple, Pineapple, Berry |
| Car | BMW, Dodge, Land Rover |

Once you create objects from a class, each object inherits all the variables and functions defined inside that class.

---

## 4. The `__init__` Method
Every class has a built-in method called `__init__`. It runs automatically when the class is used to create ("initiate") a new object, and is used to assign values to an object or run setup logic at creation time.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age


name = input("Enter the name: ")
age = int(input("Enter the age: "))
p1 = Person(name, age)

print("Name of the person:", p1.name)
print("Age of the person:", p1.age)
```

**Key points**
- Without `__init__`, you'd have to set properties manually on every object
- Parameters in `__init__` can have default values, just like a regular function
- `__init__` can take as many parameters as you need

---

## 5. The `self` Parameter
`self` refers to the current instance of the class. It's how a method accesses the properties and methods that belong to that specific object.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        print("Hello, I am", self.name, "and I am", self.age, "years old")


name = input("Enter the name: ")
age = int(input("Enter the age: "))
p1 = Person(name, age)
p1.greet()
```

**Key points**
- Without `self`, Python wouldn't know which object's properties you're referring to
- `self` doesn't have to be named `self`, but it must be the first parameter of every method in the class
- You use `self` to access any property, or to call another method from within the class

---

## 6. Class Properties
Properties are variables that belong to a class. They store data for each object created from that class.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age


p1 = Person("Emil", 36)

print(p1.name)
print(p1.age)
```

**Key points**
- Properties are accessed using dot notation (`p1.name`)
- Property values can be modified on an object
- Properties can be deleted using the `del` keyword

---

## 7. Class Properties vs Object Properties
**Class properties** belong to the class itself. They're shared across every object created from that class, changing a class property changes it for every instance, unless that instance overrides it.

**Object properties** belong to a specific instance. They're unique to each object, so changing one object's property doesn't affect any other.

```python
class Person:
    species = "Human"  # class property

    def __init__(self, name):
        self.name = name  # instance property


p1 = Person("Emil")
p2 = Person("Tobias")

print(p1.name)
print(p2.name)
print(p1.species)
print(p2.species)
```

```python
class Car:
    wheels = 4  # class property

    def __init__(self, brand):
        self.brand = brand  # object property


car1 = Car("Toyota")
car2 = Car("Honda")

print("Wheels:", Car.wheels)     # 4, class property
print("Brand:", car1.brand)      # Toyota, object property
print("Brand:", car2.brand)      # Honda, object property

Car.wheels = 6
print("Wheels:", car1.wheels)    # 6, shared change
print("Wheels:", car2.wheels)    # 6, shared change
```

**Key points**
- Modifying a class property affects every object that hasn't overridden it
- You can add new properties to existing objects at runtime

---

## 8. Class Methods
Methods are functions that belong to a class. They define the behavior of objects created from it.

```python
class Person:
    def __init__(self, name):
        self.name = name

    def greet(self):
        print("Hello, my name is " + self.name)


p1 = Person("Emil")
p1.greet()
```

Note: every method must take `self` as its first parameter.

**Key points**
- Methods can accept parameters just like a regular function
- Methods can access and modify object properties using `self`
- `__str__()` is a special method that controls what's shown when the object is printed
- A class can have multiple methods that work together
- Methods can be removed from a class with the `del` keyword

---

## 9. Inheritance
Inheritance lets you define a class that inherits all the methods and properties from another class.

- **Parent class** (base class): the class being inherited from
- **Child class** (derived class): the class that inherits from another class

### Creating a parent class
```python
class Person:
    def __init__(self, fname, lname):
        self.firstname = fname
        self.lastname = lname

    def printname(self):
        print(self.firstname, self.lastname)


x = Person("John", "Doe")
x.printname()
```

### Adding `__init__()` to the child class
Give the child its own `__init__` and call the parent's version from inside it:

```python
class Student(Person):
    def __init__(self, fname, lname):
        Person.__init__(self, fname, lname)


x = Student("Mike", "Olsen")
x.printname()
```

Note: `__init__()` runs automatically every time the class creates a new object.

### The `super()` function
`super()` makes the child class inherit all methods and properties from its parent, without you having to name the parent explicitly:

```python
class Student(Person):
    def __init__(self, fname, lname):
        super().__init__(fname, lname)
```

---

## 10. Polymorphism
Polymorphism means "many forms". In code it refers to functions, methods, or operators that share a name but behave differently depending on the object or type they act on.

### Function polymorphism
```python
print(len("hello"))            # 5, characters in a string
print(len((1, 2, 3)))          # 3, items in a tuple
print(len({"a": 1, "b": 2}))   # 2, key/value pairs in a dict
```

### Class polymorphism
Different classes can share a method name and each implement it differently:

```python
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


car1 = Car("Ford", "Mustang")
boat1 = Boat("Ibiza", "Touring 20")
plane1 = Plane("Boeing", "747")

for x in (car1, boat1, plane1):
    x.move()
```

Because of polymorphism, the same loop calls `move()` on all three, even though each class does something different.

### Polymorphism with inheritance
Child classes inherit a method from their parent but can override it:

```python
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


car1 = Car("Ford", "Mustang")
boat1 = Boat("Ibiza", "Touring 20")
plane1 = Plane("Boeing", "747")

for x in (car1, boat1, plane1):
    print(x.brand, x.model)
    x.move()
```

`Car` inherits `brand`, `model`, and `move()` from `Vehicle` unchanged. `Boat` and `Plane` inherit the same properties but override `move()`.

---

## 11. Encapsulation
Encapsulation means keeping data (properties) and methods together in a class, while controlling how that data is accessed from outside. It protects against accidental changes and hides the internal details of how the class works.

### Private properties
A double-underscore `__` prefix makes a property private:

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.__age = age  # private property


p1 = Person("Emil", 25)
print(p1.name)
print(p1.__age)  # raises AttributeError
```

### Getting a private property
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.__age = age

    def get_age(self):
        return self.__age


p1 = Person("Tobias", 25)
print(p1.get_age())
```

### Why use encapsulation?
- **Data protection**: prevents accidental modification of data
- **Validation**: lets you validate data before it's set
- **Flexibility**: internal implementation can change without breaking external code
- **Control**: you decide exactly how data is accessed and modified

```python
class Student:
    def __init__(self, name):
        self.name = name
        self.__grade = 0

    def set_grade(self, grade):
        if 0 <= grade <= 100:
            self.__grade = grade
        else:
            print("Grade must be between 0 and 100")

    def get_grade(self):
        return self.__grade

    def get_status(self):
        return "Passed" if self.__grade >= 60 else "Failed"


student = Student("Emil")
student.set_grade(85)
print(student.get_grade())
print(student.get_status())
```

### Protected properties
A single underscore `_` marks a property as "intended for internal use". Python doesn't enforce this, it's a convention other developers are expected to respect:

```python
class Person:
    def __init__(self, name, salary):
        self.name = name
        self._salary = salary  # protected property


p1 = Person("Linus", 50000)
print(p1.name)
print(p1._salary)  # accessible, but shouldn't be touched directly
```

### Private methods
The same `__` prefix works on methods:

```python
class Calculator:
    def __init__(self):
        self.result = 0

    def __validate(self, num):
        return isinstance(num, (int, float))

    def add(self, num):
        if self.__validate(num):
            self.result += num
        else:
            print("Invalid number")


calc = Calculator()
calc.add(10)
calc.add(5)
print(calc.result)
# calc.__validate(5)  # raises AttributeError from outside the class
```

### Name mangling
Python implements private members by renaming them internally: `__age` becomes `_ClassName__age`.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.__age = age


p1 = Person("Emil", 30)
print(p1._Person__age)  # works, but defeats the purpose of encapsulation
```

---

## 12. Inner Classes
An inner class is a class defined inside another class. It can access the outer class's properties and methods, and is useful for grouping helper classes that only make sense in one place.

```python
class Outer:
    def __init__(self):
        self.name = "Outer Class"

    class Inner:
        def __init__(self):
            self.name = "Inner Class"

        def display(self):
            print("This is the inner class")


outer = Outer()
print(outer.name)
```

### Accessing the inner class
Create an object of the outer class, then create an object of the inner class from it:

```python
class Outer:
    def __init__(self):
        self.name = "Outer"

    class Inner:
        def __init__(self):
            self.name = "Inner"

        def display(self):
            print("Hello from inner class")


outer = Outer()
inner = outer.Inner()
inner.display()
```

### Accessing the outer class from the inner class
Inner classes don't automatically see the outer instance, pass it in explicitly:

```python
class Outer:
    def __init__(self):
        self.name = "Emil"

    class Inner:
        def __init__(self, outer):
            self.outer = outer

        def display(self):
            print(f"Outer class name: {self.outer.name}")


outer = Outer()
inner = outer.Inner(outer)
inner.display()
```

### Practical example
```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model
        self.engine = self.Engine()

    class Engine:
        def __init__(self):
            self.status = "Off"

        def start(self):
            self.status = "Running"
            print("Engine started")

        def stop(self):
            self.status = "Off"
            print("Engine stopped")

    def drive(self):
        if self.engine.status == "Running":
            print(f"Driving the {self.brand} {self.model}")
        else:
            print("Start the engine first!")


car = Car("Toyota", "Corolla")
car.drive()
car.engine.start()
car.drive()
```

### Multiple inner classes
A class can have more than one inner class:

```python
class Computer:
    def __init__(self):
        self.cpu = self.CPU()
        self.ram = self.RAM()

    class CPU:
        def process(self):
            print("Processing data...")

    class RAM:
        def store(self):
            print("Storing data...")


computer = Computer()
computer.cpu.process()
computer.ram.store()
```

---

## 13. Quick Mental Model
- Class defines the blueprint, object is the instance built from it
- `__init__` runs on creation, `self` refers to "this object" inside a method
- Class properties are shared, object properties are per-instance
- Inheritance: child reuses or overrides parent behavior, `super()` calls the parent without naming it
- Polymorphism: same method name, different behavior per class
- Encapsulation: `_protected` is a convention, `__private` triggers name mangling

## Resources
- Official docs: https://docs.python.org/3/tutorial/classes.html
