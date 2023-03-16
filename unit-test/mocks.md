# Mocks

### Description

```
In software development, a mock is an object that simulates the behavior of a real object in a controlled environment.
It is used mainly in unit testing, with the purpose of testing the behavior of some part of the part of the code without
depending on another part of the system.
```

###### With this little introduction let's have a demonstration, for a better visualization of what a mock is.

### Example

> Suppose you are developing a system for an online store and in a certain part of the code you calculate the total
> price of a purchase. To test this functionality you need to simulate the behavior of other objects, such as shopping
> cart and products. Instead of creating real objects, the programmer can create mocks of these objects, which mimic the
> expected behavior during testing.

##### With that we will do the following:

Create the following classes:

```js
// Product.js
class Product {
    constructor({id, name, price}) {
        this.id = id;
        this.name = name;
        this.price = price;
    }
}
```

```js
// Cart.js
class Cart {
    constructor(products) {
        this.products = products;
    }
}
```

Create a file to test the functionality `calculateFinalPrice`:

```js
// index.test.js
const {deepEqual} = require('assert');
const Product = require('../entities/product');
const Cart = require('../entities/cart');

(async () => {
    {
        const product1 = new Product({id: 1, name: 'TV', price: 200.00});
        const product2 = new Product({id: 2, name: 'Smartphone', price: 100.00});
        const product3 = new Product({id: 3, name: 'Smartwatch', price: 50.00});
        const cart = new Cart([product1, product2, product3]);

        const result = service.calculateFinalPrice(cart.products);
        const expected = 350.00;

        deepEqual(expected, result);
    }
})();
```

In the demo above we create 4 mocks, 3 for products and one for a cart, then calculate the total price with them and
follow the
unit test. You can see that the concept is simple but essential, since the more independent of third
parts of the code the better.