# Task 5

## **Task:**

You are building an iOS app for a restaurant that displays their menu and allows
customers to place orders. The restaurant has different categories of dishes,
such as appetizers, entrees, and desserts. Create a class hierarchy for the
different types of dishes that the restaurant serves. Each dish should have a
name, description, and price.

## **Solution:**

First, we can create a base class **`Dish`** that contains the common properties
of all dishes:

```swift
class Dish {
    let name: String
    let description: String
    let price: Double

    init(name: String, description: String, price: Double) {
        self.name = name
        self.description = description
        self.price = price
    }
}
```

Next, we can create subclasses for each category of dishes. For example, the
**`Appetizer`** class might look like this:

```swift
class Appetizer: Dish {
    let isHot: Bool

    init(name: String, description: String, price: Double, isHot: Bool) {
        self.isHot = isHot
        super.init(name: name, description: description, price: price)
    }
}
```

And the **`Entree`** class might look like this:

```swift
class Entree: Dish {
    let isVegetarian: Bool

    init(name: String, description: String, price: Double, isVegetarian: Bool) {
        self.isVegetarian = isVegetarian
        super.init(name: name, description: description, price: price)
    }
}
```

Finally, we can create a **`Dessert`** class:

```swift
class Dessert: Dish {
    let hasGluten: Bool

    init(name: String, description: String, price: Double, hasGluten: Bool) {
        self.hasGluten = hasGluten
        super.init(name: name, description: description, price: price)
    }
}
```

With this class hierarchy, we can easily create instances of different types of
dishes and access their properties. For example:

```swift
let mozzarellaSticks = Appetizer(name: "Mozzarella Sticks", description: "Fried cheese sticks with marinara sauce", price: 6.99, isHot: true)

let veggieBurger = Entree(name: "Veggie Burger", description: "A delicious plant-based burger with all the fixings", price: 10.99, isVegetarian: true)

let chocolateCake = Dessert(name: "Chocolate Cake", description: "A rich, decadent chocolate cake with whipped cream", price: 7.99, hasGluten: true)
```

By using inheritance and subclasses, we can easily add new categories of dishes
and reuse code across different types of dishes.
