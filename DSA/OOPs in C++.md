
![[Drawing 2023-08-17 04.57.33.excalidraw]]

State/ properties refer to somewhat like name, age and other props of the object.

Note: A class is mostly like a user-defined datatype.

An object is nothing but an instance of a class.

```cpp
class Hero {
    //properties
    int health;
};
```

Now, if we do, 
```cpp
int main()
{
    Hero h1;
    cout<<"size : "<<sizeof(h1)<<endl;
    return 0;
}
```

We get, 4 in output.

But if we make a class with no properties (Empty Class), then we do the same thing, we get size as 1. Just for identification.

#### Use a class from a seperate file, 
> Make a file, MyClass.cpp
> Write all the Code for a class there. (only the class).
> Then use the file by doing #include "MyClass.cpp".
> And the class can now be used.

### Access Modifiers - 
* Public
* Private
* Protected 

By default in any class the access modifier is set to private.
 How to change Access modifier - 
```cpp
class Hero
{
    // properties
    char name[100];
    public:
    int health;
    char level;
};
```

Now, the health and level have become public, only the name still remains to be private.

> Public - can be accessed anywhere using the dot operator.
> Private - Can be accessed from only inside the class.


