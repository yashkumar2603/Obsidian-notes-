**Formatted Input + output method -**
```python
print(f"Hello, {input("Name: ")}")
```

##### Type Casting the inputs / anything -

- Let’s look a bit more closely at this specific exception: If we look at the bottom, we’ll see that we ran into a `TypeError`, which generally means Python expected a certain variable to be of one type, but found it to be of another type. In this case, the exception tells us that we cannot use the `>` symbol to compare a `str` and `int`, and then above we can see that this comparison occurs in line 2.
- In this case, it’s obvious that `0` is an integer, so it must be the case that our `num` variable is a string. This is happening because it turns out that the `input` function always returns a string, and we have to specify that it should be turned into (or **cast** into) an integer using the `int` function. This means our first line would now look like:

```python
num = int(input("Number: "))
```

#### Sequences - 

##### 1. Strings -

**Ordered**: Yes

**Mutable**: No

We’ve already looked at strings a little bit, but instead of just variables, we can think of a string as a sequence of characters. This means we can access individual elements within the string! 

##### 2. Lists - 

**Ordered**: Yes

**Mutable**: Yes

A [Python list](https://www.w3schools.com/python/python_lists.asp) allows you to store any variable types. We create a list using square brackets and commas, as shown below. Similarly to strings, we can print an entire list, or some individual elements. We can also add elements to a list using `append`, and sort a list using `sort`
##### 3. Tuples - 

**Ordered**: Yes

**Mutable**: No

[Tuples](https://www.w3schools.com/python/python_tuples.asp) are generally used when you need to store just two or three values together, such as the x and y values for a point. In Python code, we use parentheses:

```python
point = (12.5, 10.6)
```

##### 4. Sets - 

**Ordered**: No

**Mutable**: N/A

[Sets](https://www.w3schools.com/python/python_sets.asp) are different from lists and tuples in that they are **unordered**. They are also different because while you can have two or more of the same elements within a list/tuple, a set will only store each value once. We can define an empty set using the `set` function. We can then use `add` and `remove` to add and remove elements from that set, and the `len` function to find the set’s size. Note that the `len` function works on all sequences in python. **Also note that despite adding `4` and `3` to the set twice, each item can only appear once in a set.**

```Python
# Create an empty set:
s = set()

# Add some elements:
s.add(1)
s.add(2)
s.add(3)
s.add(4)
s.add(3)
s.add(1)

# Remove 2 from the set
s.remove(2)

# Print the set:
print(s)

# Find the size of the set:
print(f"The set has {len(s)} elements.")

""" This is a python multi-line comment:
Output:
{1, 3, 4}
The set has 3 elements.
"""
```

#### Loops - 

- We can condense this code using the python `range` function, which allows us to easily get a sequence of numbers. 

```Python
for i in range(6):
    print(i)

""" Output:
0
1
2
3
4
5
"""
```

- This type of loop can work for any sequence! For example, if we wish to print each name in a list, we could write the code below:

```Python
# Create a list:
names = ["Harry", "Ron", "Hermione"]

# Print each name:
for name in names:
    print(name)

""" Output:
Harry
Ron
Hermione
"""
```

- We can get even more specific if we want, and loop through each character in a single name!

```Python
name = "Harry"
for char in name:
    print(char)

""" Output:
H
a
r
r
y
"""
```

### Basic Functions - 

- We can condense this code using the python `range` function, which allows us to easily get a sequence of numbers. The following code gives the exact same result as our code from above:

```Python
for i in range(6):
    print(i)

""" Output:
0
1
2
3
4
5
"""
```

- This type of loop can work for any sequence! For example, if we wish to print each name in a list, we could write the code below:

```Python
# Create a list:
names = ["Harry", "Ron", "Hermione"]

# Print each name:
for name in names:
    print(name)

""" Output:
Harry
Ron
Hermione
"""
```

- We can get even more specific if we want, and loop through each character in a single name!

```Python
name = "Harry"
for char in name:
    print(char)

""" Output:
H
a
r
r
y
"""
```

### Importing Modules -

As our projects get larger and larger, it will become useful to be able to write functions in one file and run them in another. In the case above, we could create create one file called `functions.py` with the code:

```PYTHON
def square(x):
    return x * x
```

And another file called `square.py` with the code:

```python
for i in range(10):
    print(f"The square of {i} is {square(i)}")
```

However, when we try to run `square.py`, we run into the following error:

![Name Error](https://cs50.harvard.edu/web/2020/notes/2/images/NameError.png)

We run into this problem because by default, Python files don’t know about each other, so we have to explicitly `import` the square function from the `functions` **module** we just wrote. Now, when `square.py` looks like this:

```python
from functions import square

for i in range(10):
    print(f"The square of {i} is {square(i)}")
```

Alternatively, we can choose to import the entire `functions` module and then use dot notation to access the `square` function:

```python
import functions

for i in range(10):
    print(f"The square of {i} is {functions.square(i)}")
```

There are many built-in Python modules we can import such as `math` or `csv` that give us access to even more functions. Additionally, we can download even more Modules to access even more functionality!

[[OOPs; Lecture-2]]
[[Functional Programming; Lecture - 2]]
[[Exception Handling; Lecture-2]]
