### SEIR 0508

# Object-Oriented Javascript

![Image Header](https://www.freecodecamp.org/news/content/images/2020/02/OOP-IN-JS-1.png)

## Overview
Object-oriented programming (OOP) is a programming paradigm based on the concept of `objects`, which contain data, in the form of fields, often known as `properties` and functions often known as `methods`. When you define a `class`, you define a *blueprint for an object*. This doesn't actually define any data, but it does define what the class name means, that is, what an object of the class will consist of and what operations can be performed on such an object. In this lesson, we'll be covering how to implement OOP with JavaScript.

## Getting Started
- Fork and Clone
- Create an `index.js` file

## Objectives

- Use the `new` keyword to create objects with shared properties and methods
- Describe the role of classes in JavaScript
- Explain the importance of Object-Oriented Programming
- Define the concept of inheritance as it pertains to classes
- Create a class that inherits from another using the `extends` and `super` keywords

#### What is an object in programming?

An object encapsulates related data and behavior in an organized structure.

We've already gotten exposure to Javascript objects using **object literal notation**. We could define a car object in this way:

```js
const car = {
  make: 'Honda',
  model: 'Civic',
  color: 'red',
  drive() {
    console.log('vroom vroom');
  },
  gps(location) {
    console.log(`Beep boop, driving to ${location}`);
  },
  paint(newColor) {
    console.log(`Your car has been painted ${newColor}`);
    this.color = newColor;
  },
};

```

What's nice about the above code snippet?

<details>

  <summary><strong>Some thoughts...</strong></summary>

  > * Related properties and methods are packaged together.
  > * Fewer global variables.
  > * Readability.

</details>

#### Why might we use an OOP approach to programming?

Object-oriented programming (OOP) provides us with opportunities to clean up our procedural code and model it more-closely to the external world.

OOP helps us to achieve the following...
  * **Abstraction:** hiding all but the relevant data about an object in order to reduce complexity and increase efficiency
  * **Encapsulation:** is the process of combining data and functions into a single unit
  * **Inheritance:** Enables new objects to receive or inherit the properties and methods of existing objects
  * **Polymorphism**: Allows for many forms of the same type of object through inheritance

OOP becomes **very** important as our front-end code grows in complexity. Even a simple app will have lots of code on the front-end to do things like...
* Send requests to a back-end to fetch / update / destroy data
* Update the state of the page as data changes
* Respond to events like clicking buttons

### Creating Objects

![Assembly](https://biol355.github.io/Lectures/Images/iteration/assembly_line.gif)

So far, we've had to make our objects 'by hand' (i.e. using object literals)...

```js
const celica = {
  model: 'Toyota Celica',
  color: 'limegreen',
  fuel:  100,
  drive() {
    this.fuel--;
    return 'Vroom!';
  },
  refuel() {
    this.fuel = 100;
  },
};

const civic = {
  model: 'Honda Civic',
  color: 'lemonchiffon',
  fuel:  100,
  drive() {
    this.fuel--;
    return 'Vroom!';
  },
  refuel() {
    this.fuel = 100;
  },
};
```

Even though we're technically using objects to organize our code, we can see a noticeable amount of duplication. Just imagine if we needed a hundred cars in our app! Our code would certainly not be considered "DRY".

As you may have noticed, some of these properties change between cars, and others stay the same. In the example above, while the `model` and `color` properties may vary, the `fuel` property and `drive` and `refuel` functions are the same for every car.

Making all of these similar objects by hand is just tedious. What if we could build a function that makes them for us?

### Create a `makeCar` Function

Define a function `makeCar` that takes two parameters - `model` and `color` - and returns an object literal representing a car using those params.

```js
// This should return a car object just like the previous example
const celica = makeCar('Toyota Celica', 'limegreen');
```

<details>
  <summary><strong>Solution...</strong></summary>

  ```js
  const makeCar = function(model, color){
    return {
      model: model,
      color: color,
      fuel:  100,
      drive: function() {
        this.fuel--;
        return 'Vroom!';
      },
      refuel: function() {
        this.fuel = 100;
      }
    }
  }
  ```

</details>

This is the basic idea behind OOP; we define a **blueprint** for an object and use it to generate multiple **instances** of it!

![Car Class Blueprint](https://vitalflux.com/wp-content/uploads/2014/10/classes_and_objects.gif)
