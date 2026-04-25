# Week 9: Object-Oriented Programming

```python
def main():
    name = get_name()
    house = get_house()
    print(f"{name} from {house}")

def get_name():
    return input("Name: ")

def get_house():
    return input("House: ")

if __name__ == "__main__":
    main()
```

- tuple: immutability; list: mutability

```python
def main():
    name, house = get_student()
    print(f"{name} from {house}")

def get_student():
    name = input("Name: ")
    house = input("House: ")
    return name, house # one tuple with two values
```

```python
def main():
    student = get_student()
    print(f"{student['name']} from {student['house']}")

def get_student():
    student = {}
    student["name"] = input("Name: ")
    student["house"] = input("House: ")
    return student
```

- classes
  - blueprint, create your own data types

```python
class Student:

def main():
    student = get_student()
    print(f"{student.name} from {student.house}")

def get_student():
    student = Student() # create an object from class
    student.name = input("Name: ")
    student.house = input("House: ")
    return student
```

- objects
  - instances of classes
- attributes
- instance variables

```python
def get_student():
    name = input("Name: ")
    house = input("House: ")
    student = Student(name, house) # parse data into the class, constructor call, construct an object
    return student
```

- methods
- `__init__`

```python
class Student:
    # initialization method, initialize the object
    def __init__(self, name, house): # self gives you access to the object that you just created
        self.name = name
        self.house = house
```

- raise: related to exceptions

```python
class Student:
    def __init__(self, name, house):
        if not name:
            raise ValueError("Missing name")
        if house not in ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]:
            raise ValueError("Invalid house")
        self.name = name
        self.house = house

def get_student():
    name = input("Name: ")
    house = input("House: ")
    try:
        return Student(name, house)
    except Value:
        ...
```

- `__str__`

```python
class Student:
    def __init__(self, name, house):
        # Validating
        if not name:
            raise ValueError("Missing name")
        if house not in ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]:
            raise ValueError("Invalid house")
        self.name = name
        self.house = house

    def __str__(self):
        return f"{self.name} from {self.house}"

def main():
    student = get_student()
    print(student)

def get_student():
    name = input("Name: ")
    house = input("House: ")
    return Student(name, house)

if __name__ == "__main__":
    main()
```

- properties `@property`
  - attributes, but more control over
- decorators

```python
class Student:
    def __init__(self, name, house):
        # Validating
        if not name:
            raise ValueError("Missing name")
        self.name = name
        self.house = house # without underscore, assignment will go thru the setter function, thru that validating check

    def __str__(self):
        return f"{self.name} from {self.house}"

    # Getter
    @property
    def house(self):
        return self._house # distinguish between attribute house and function house

    # Setter
    @house.setter
    def house(self, house):
        if house not in ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]:
            raise ValueError("Invalid house")
        self._house = house
```

```python
def main():
    student = get_student()
    student._house = "Number Four, Privet Drive" # attribute is editable with that underscore, BUT DONT, DONT TOUCH IT
    print(student)
```

- class methods `@classmethod`

[student.py](/student.py)

```python
import random

class Hat:
    def __init__(self):
        self.houses = ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]

    def sort(self, name):
        print(name, "is in", random.choice(self.houses))

hat = Hat()
hat.sort("Harry")
```

```python
import random

class Hat:
    # class variable: a variable inside this class
    houses = ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]

    @classmethod
    def sort(cls, name):
        print(name, "is in", random.choice(cls.houses))

Hat.sort("Harry") # there is only one hat, we don't init a hat object, we just accessing the class method inside a class
```

```python
class Student:
    def __init__(self, name, house):
        self.name = name
        self.house = house

    def __str__(self):
        return f"{self.name} from {self.house}"

    @classmethod
    def get(cls): # we can call this method, without instantiating a student object first
        name = input("Name: ")
        house = input("House: ")
        return cls(name, house)

def main():
    student = Student.get()
    print(student)

if __name__ == "__main__": # avoid accidently executing main when making a module or package
    main()
```

- static methods `@staticmethod`
- inheritance: key feature of object oriented programming

```python
class Student:
    def __init__(self, name, house):
        if not name:
            raise ValueError("Missing name")
        self.name = name
        self.house = house
    ...

class Professor:
    def __init(self, name, subject):
        if not name:
            raise ValueError("Missing name")
        self.name = name
        self.subject = subject

    ...
```

```python
class Wizard:
    def __init__(self, name):
        if not name:
            raise ValueError("Missing name")
        self.name = name

    ...

class Student(Wizard): # Student inherits from, or a subclass of Wizard
    def __init__(self, name, house):
        super().__init__(name) # Student inherits functionality and using it by calling superclass's method
        self.house = house

    ...

class Professor(Wizard):
    def __init__(self, subject):
        super().__init__(name)
        self.subject = subject

    ...

wizard = Wizard("Albus")
student = Student("Harry", "Gryffindor")
professor = Professor("Severus", "Defense Against the Dark Art")
```

- operator overloading
  - `+`: plus, concatenate, join a list...

```python
class Vault:
    def __init__(self, galleons=0, sickles=0, knuts=0): # defaults 0
        self.galleons = galleons
        self.sickles = sickles
        self.knuts = knuts

    def __str__(self):
        return f"{self.galleons} Galleons, {self.sickles} Sickles, {self.knuts} Knuts"

    def __add__(self, other): # overload the + operator, add two Vault objects
        galleons = self.galleons + other.galleons
        sickles = self.sickles + other.sickles
        knuts = self.knuts + other.knuts
        return Vault(galleons, sickles, knuts)

potter = Vault(100, 50, 25)
print(potter)

weasley = Vault(25, 50, 100)
print(weasley)

total = potter + weasley
print(total)
```
