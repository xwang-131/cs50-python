# Week 0: Functions, Variables

### functions

### arguments

### variables

### parameters

### str

### int

### float

```python
x = float(input("What's x? "))
y = float(input("What's y? "))
z = round(x / y, 2) # round the float to 2 digits
print(z)
```

```python
x = float(input("What's x? "))
y = float(input("What's y? "))
z = x / y
print(f"{z:.2f}") # format way to round to 2 digits
```

### def

```python
def hello():
    print("hello")

name = input("What's your name? ")
hello()
print(name)
```

```python
def hello(to="world"): # parameter default value "world"
    print("hello,", to)

hello()
name = input("What's your name? ")
hello(name)
```

```python
def main():
    name = input("What's your name? ")
    hello(name)

def hello(to="world"):
    print("hello,", to)

main() # call the function
```

### scope

### return

```python
def main():
    x = int(input("What's x? "))
    print("x squared is", square(x))

def square(n):
    return n * n

main()
```
