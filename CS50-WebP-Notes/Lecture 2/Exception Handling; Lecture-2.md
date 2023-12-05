During this lecture, we’ve run into a few different exceptions, so now we’ll look into some new ways of dealing with them.

In the following chunk of code, we’ll take two integers from the user, and attempt to divide them:

```python
x = int(input("x: "))
y = int(input("y: "))

result = x / y

print(f"{x} / {y} = {result}")
```

In many cases, this program works well:

![Good example](https://cs50.harvard.edu/web/2020/notes/2/images/dividegood.png)

However, we’ll run into problems when we attempt to divide by 0:

![Bad example](https://cs50.harvard.edu/web/2020/notes/2/images/dividebad.png)

**We can deal with this messy error using [Exception Handling](https://www.w3schools.com/python/python_try_except.asp). In the following block of code, we will `try` to divide the two numbers, `except` when we get a `ZeroDivisionError`:**

```python
import sys

x = int(input("x: "))
y = int(input("y: "))

try:
    result = x / y
except ZeroDivisionError:
    print("Error: Cannot divide by 0.")
    # Exit the program
    sys.exit(1)

print(f"{x} / {y} = {result}")
```

In this case, when we try it again:

![Divide by 0 exception](https://cs50.harvard.edu/web/2020/notes/2/images/divide0.png)

However, we still run into an error when the user enters non-numbers for x and y:

![Value error](https://cs50.harvard.edu/web/2020/notes/2/images/valueError.png)

We can solve this problem in a similar manner!

```python
import sys

try:
    x = int(input("x: "))
    y = int(input("y: "))
except ValueError:
    print("Error: Invalid input")
    sys.exit(1)

try:
    result = x / y
except ZeroDivisionError:
    print("Error: Cannot divide by 0.")
    # Exit the program
    sys.exit(1)

print(f"{x} / {y} = {result}")
```

**sys module helps us to do the exit program thing. and try statement helps us to do exception specific coding.**
