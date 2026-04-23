# Week 1: Conditionals

### if

### elif

### else

```python
x = int(input("What's x? "))
y = int(input("What's y? "))
if x < y:
    print("x is less than y")
elif x > y:
    print("x is greater than y")
else:
    print("x is equal to y")
```

### or

### and

```python
x = int(input("What's x? "))
if x % 2 == 0: # check if x is cleanly divided by 2
    print("Even")
else:
    print("Odd")
```

### bool

- True, False

```python
def main():
    x = int(input("What's x? "))
    if is_even(x):
        print("Even")
    else:
        print("Odd")

def is_even(n):
    return n % 2 == 0

main()
```

### match

```python
name = input("What's your name? ")

match name:
    case "Harry" | "Hermione" | "Ron":
        print("Gryffindor")
    case "Draco":
        print("Slytherin")
    case _: # all the other cases
        print("Who?")
```
