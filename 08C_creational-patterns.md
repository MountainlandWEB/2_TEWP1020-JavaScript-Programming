# 08B: Creational Patterns

#### [Table of Contents](#table-of-contents)
  + Factory
  + Singleton
  + Builder
  + Prototype

## The Factory method
<div style="text-align:center">
<img src="https://static.wixstatic.com/media/353803_56f4babad5cc4a0faae91bb5e72808eb~mv2.jpg" width="300" />
</div>

<details open>
<summary>The Factory method</summary>
  
> The factory method is a creational pattern that delegates the responsibility of object instantiation to its concrete subclasses.
>
> ### Scenerio To Think About
> Imagine a drive-thru where customers order meals by number, such as "Combo 1". Customers don't specify ingredients or preparation details; they trust the kitchen to handle that. But how do we design this from a software perspective, such that we create a flexible and loosely coupled design?

> ### Consider Solution #1: Instantiate
> Direct Instantiation by the client: a way to handle this is direct instantiation. Creating burger objects based on multiple conditionals:

```
 let burger;

 if (TYPES.CHEESE) {
     burger = new CheeseBurger();
 } else if (TYPES.DELUXE) {
     burger = new DeluxeCheeseBurger();
 } else if (TYPES.VEGAN) {
     burger = new VeganBurger();
}
```

> This does work, but what happens when we introduce a new burger type or a limited-time special?

> Each addition requires us to modify this logic. This isn't just tedious but also risks introducing errors, particularly if this decision-making code sprawls across the application.

> We have discussed "program to an interface and not to an implementation" before, meaning that clients should remain unaware of the specific types of objects they use, as long as the objects adhere to the interface that they expect.

> While the code above adheres to this principle, we are still limiting ourselves to the concrete implementation when we perform instantiation. This direct instantiation within the client code is brittle. It makes the system less adaptable to change and increases the chances of mistakes.

> We also violate the single-responsibility principle because we are handling the logic of cooking, preparing the drink and the side, all together in one class. If we make a mistake updating any of the conditional code, we might end up taking down the entire burger class. In a real kitchen, the cashier does not decide how to cook the burger or what ingredients to use. The same should be the case with our code.

> ### Consider Solution #2: Encapsulate
> Encapsulate what varies using a simple factory: We know that the burger menu may evolve over time, but we would prefer not to directly modify all of the parts of code that instantiate a burger. Taking the design principle, "encapsulate what varies" into consideration, we can create a class called SimpleBurgerFactory and isolate the burger creation logic to a method called createBurger.

```
const BurgerType = Object.freeze({
    CHEESEBURGER: 'CHEESEBURGER',
    DELUXE_CHEESEBURGER: 'DELUXE_CHEESEBURGER',
    VEGANBURGER: 'VEGANBURGER'
});

class SimpleBurgerFactory {
    createBurger(type) {
        let burger = null;
        switch (type) {
            case BurgerType.CHEESEBURGER:
                burger = new CheeseBurger();
                break;
            case BurgerType.DELUXE_CHEESEBURGER:
                burger = new DeluxeCheeseBurger();
                break;
            case BurgerType.VEGANBURGER:
                burger = new VeganBurger();
                break;
        }
        return burger;
    }
}
```

> Note: The above solution still violates the open/closed principle but it also violates the dependency inversion principle. The simple factory has direct dependencies on the concrete classes that it is creating. And while the simple factory is abstracting away the creation process, the product type still needs to be provided to the factory.

> ### Solution?

</details>

## Factory Method Pattern Exercise

<details open>
<summary>Factory Method Pattern In-Class Exercise</summary>
  
> Implement the Factory Method design pattern.

> The Factory Method is a creational design pattern that provides an interface for creating objects in a superclass but allows subclasses to alter the type of objects that will be created.

> You are given code that includes a few vehicles types and their respective factories. Complete the factory method implementation such that each factory returns the correct vehicle.

### Example:

```
VehicleFactory carFactory = new CarFactory();
VehicleFactory truckFactory = new TruckFactory();
VehicleFactory bikeFactory = new BikeFactory();

Vehicle myCar = carFactory.createVehicle();
Vehicle myTruck = truckFactory.createVehicle();
Vehicle myBike = bikeFactory.createVehicle();

myCar.getType();   // "Car"
myTruck.getType(); // "Truck"
myBike.getType();  // "Bike"
```

</details>

