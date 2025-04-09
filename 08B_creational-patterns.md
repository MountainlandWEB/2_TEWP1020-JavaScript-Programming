# 08B: Behavioral Patterns

#### [Table of Contents](#table-of-contents)
  + Chain of Responsibility
  + Command
  + Iterator
  + Mediator
  + Memento
  + Observer
  + State
  + Strategy
  + Template Method
  + Visitor

Behavioral design patterns are concerned with algorithms and the assignment of responsibilities between objects.

## Chain of Responsibility

<details open>
<summary>Chain of Responsibility</summary>

> The Chain of Responsibility pattern lets you pass requests through a series of handlers without knowing who is going to handle it. Each handler chooses to either process the request or pass it to the next one if it is unable to handle that request. This pattern encourages loose coupling between the sender and receiver, providing freedom in handling the request, as any handler can be added, removed, or modified independently without affecting others.
>
> ### Scenerio To Think About
> Imagine that you’re working on an online ordering system. You want to restrict access to the system so only authenticated/authorized users can create orders. Also, users who have administrative permissions must have full access to all orders.

> After a bit of planning, you realized that these checks must be performed sequentially. The online ordering system can attempt to authenticate a user whenever it receives a request that contains the user’s credentials. However, if those credentials aren’t correct and authentication fails, there’s no reason to proceed with any other checks.

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
