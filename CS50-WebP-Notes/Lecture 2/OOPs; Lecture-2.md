### Object Oriented Programming in Python - 

[Object Oriented Programming](https://en.wikipedia.org/wiki/Object-oriented_programming) is a programming paradigm, or a way of thinking about programming, that is centered around objects that can store information and perform actions.

- **Classes**: We’ve already seen a few different types of variables in python, but what if we want to create our own type? A [Python Class](https://www.w3schools.com/python/python_classes.asp) is essentially a template for a new type of object that can store information and perform actions. Here’s a class that defines a two-dimensional point:

```python
class Point():
    # A method defining how to create a point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
```

- Note that in the above code, we use the keyword `self` to represent the object we are currently working with. `self` should be the first argument for any method within a Python class.

Now, let’s see how we can actually use the class from above to create an object:

```python
p = Point(2, 8)
print(p.x)
print(p.y)

""" Output:
2
8
"""
```

Now, let’s look at a more interesting example where instead of storing just the coordinates of a Point, we create a class that represents an airline flight:

```python
class Flight():
    # Method to create new flight with given capacity
    def __init__(self, capacity):
        self.capacity = capacity
        self.passengers = []

    # Method to add a passenger to the flight:
    def add_passenger(self, name):
        self.passengers.append(name)
```

However, this class is flawed because while we set a capacity, we could still add too many passengers. Let’s augment it so that before adding a passenger, we check to see if there is room on the flight:

```python
class Flight():
    # Method to create new flight with given capacity
    def __init__(self, capacity):
        self.capacity = capacity
        self.passengers = []

    # Method to add a passenger to the flight:
    def add_passenger(self, name):
        if not self.open_seats():
            return False
        self.passengers.append(name)
        return True

    # Method to return number of open seats
    def open_seats(self):
        return self.capacity - len(self.passengers)
```

Note that above, we use the line `if not self.open_seats()` to determine whether or not there are open seats. This works because in Python, the number 0 can be interpretted as meaning `False`, and we can also use the keyword `not` to signify the opposite of the following statement so `not True` is `False` and `not False` is `True`. Therefore, if `open_seats` returns 0, the entire expression will evaluate to `True`

Now, let’s try out the class we’ve created by instantiating some objects:

```python
# Create a new flight with o=up to 3 passengers
flight = Flight(3)

# Create a list of people
people = ["Harry", "Ron", "Hermione", "Ginny"]

# Attempt to add each person in the list to a flight
for person in people:
    if flight.add_passenger(person):
        print(f"Added {person} to flight successfully")
    else:
        print(f"No available seats for {person}")

""" Output:
Added Harry to flight successfully
Added Ron to flight successfully
Added Hermione to flight successfully
No available seats for Ginny
"""
```
