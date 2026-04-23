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

if __name__ == "__main__": # ?
    main()
```

### tuple

- tuple: immutability; list: mutability

```python
def main():
    name, house = get_student()
    print(f"{name} from {house}")

def get_student():
    name = input("Name: ")
    house = input("House: ")
    return name, house # one tuple with two values

if __name__ == "__main__": # ?
    main()
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

if __name__ == "__main__":
    main()
```

### classes

- blueprint
