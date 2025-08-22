Object Oriented Programming, often referred to as OOP, is a common programming paradigm found in many high level languages such as javascript and Python. In OOP we will make and manipulate Objects through the use of Classes to handle *data* and *logic*. Let's run through the very basics of OOP.

## Classes

A Class is a blueprint to create an object. When we create an object from a class we call this new object an "instance" of the Class. Typically, we will need to store this object in a variable so that we can access it later. All classes contain a list of properties and methods(), so any instance of a class will have these properties and methods as well.  

A Class's properties are used to store *data* about the object. We can think of these as adjectives. Note that properties will always be written in all lower case. 

A Class's methods() are used to perform *logic* related to the object. We can think of these as verbs. Note that methods() are written in all lower case but have a set of parentheses on the end. These parentheses are used to pass *arguments* to the method, essentially extra instructions for what the object will do. Some methods will take *multiple arguments*, when multiple arguments are needed we separate them with a ",". Not all methods() will require extra arguments, but many will.

## Putting it all together: Dot notation

In this example we have a **Class** called **Desk**. The **Desk** class has the following properties and methods:

| properties | description                                     | methods       | description                                                               |
| ---------- | ----------------------------------------------- | ------------- | ------------------------------------------------------------------------- |
| height     | The height of the desk in meters                | move()        | Moves the desk to an (x,y,z) coordinate                                   |
| weight     | The weight of the desk in kilograms             | hold()        | Places an object on the desk (the desk stores that object)                |
| color      | The color of the desk in ARGB                   | flip()        | Flips the desk, removing all objects                                      |
| legs       | The amount of legs                              | rotate()      | Rotates the desk around its y axis in radians                             |
| position   | The position of the desk as (x,y,z) coordinates | take()        | Removes an object from the desk                                           |
|            |                                                 | remove_legs() | Removes an amount of legs. Returns an int of the amount of legs remaining |

In GDScript, we may create a new object in the following way:

```gdscript
var new_desk = Desk.new()
```

Remember, when we make an object we need to store it in a variable so that we can reference it later. Next, we may want to change some information about the desk. We can access an object's properties by using what we call dot notation. Here is an example accessing the legs property:

```gdscript
new_desk.legs
```

Notice that the object and its property are separated by a "." (hence dot notation). We can access any property in this way. Here are a few more examples:

```gdscript
new_desk.height
new_desk.color
new_desk.position
```

We can also change the value of a property by using an "=" to *assign* a new value to the property in the same way that we have with variables.

```gdscript
new_desk.legs = 3 # This desk now has 3 legs
new_desk.legs = 90 # This desk now has 90 legs
```

We can also use them in a calculation such as below:

```gdscript
var my_variable = new_desk.legs + 20 # This would store 110 in my_variable
```

We can access an objects methods() using dot notation as well. Below is an example of rotating the new_desk object:

```gdscript
new_desk.rotate(0.5 * PI) # This is in radians, in degrees this would be 90 degrees
```

And here we'll move the desk to some new location

```gdscript
# Notice that this method() takes 3 arguments separated by commas
new_desk.move(15, 0, 15)
```

You may have noticed that we have a property for position that is an (x,y,z) coordinate as well. We could set the desk's position using either the move() method() or the position property.

```gdscript
# These two lines do the same thing
new_desk.position = Vector3(15, 0, 15) # A Vector3 collects an (x,y,z) coordinate together
new_desk.move(15, 0, 15)
```

Some methods will *return* a value. This means that it will send *data* out when we call it. If we use the remove_legs() method we see that it will *return* an integer of the amount of legs remaining:

```gdscript
# This line would print whatever the current amount of legs minus 3 to the output. Every time we ran this line the new_desk would have 3 less legs as well.
print(new_desk.remove_legs(3))  
```

## A Godot Example



## Now it's your turn!

