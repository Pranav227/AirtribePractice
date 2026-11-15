# Java Assignment 01

## What did you predict for `Warmup.java`, and what did it actually print?

It is helpful to understand how bytes are truncated during explicit type casting. If we do not include an explicit cast, Java throws an error. But if we force the cast, Java simply drops the extra bits on the right, which can produce a surprising result.

I was aware of this behavior, but I could not guess the exact output number at first. After studying it further, I understood that a `byte` follows a wraparound range from `-128` to `127`. If the value goes beyond `127`, it starts again from `-128`. For example:

- `127` remains `127`
- `128` becomes `-128`
- `129` becomes `-127`
- `130` becomes `-126`

So in this case, the value `130` wraps around and becomes `-126`.

I was not surprised by the `switch` statement output because Java executes all cases from the matching case until it reaches a `break` statement or the end of the `switch` block.

## What is the difference between the static variable `totalProducts` and the instance variable `name`?

A `static` variable is also called a class variable, not an instance variable. It is shared among all objects created from the same class. It can be accessed directly using the class name, without creating an object. Although it is technically possible to access it through an object reference, it is not recommended.

In contrast, an instance variable such as `name` belongs to each individual object. Every object has its own copy of the instance variable.

## What does the copy constructor do, and why does changing `p2.name` not change `p1.name`?

A copy constructor accepts an object of the same class as a parameter and is used to initialize a new object with the same values as an existing object.

Here, `p1` and `p2` are two different objects of the same class. The variable `name` is an instance variable, not a static variable. Because of this, each object has its own separate copy of `name`. Changing `p2.name` does not affect `p1.name`.