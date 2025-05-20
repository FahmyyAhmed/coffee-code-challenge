## ☕ Coffee Shop Challenge

A small OOP Python project simulating customer interactions in a coffee shop. It models **Customers**, **Coffees**, and their **Orders**, complete with validation, relationships, and basic analytics.

---

## 📁 Project Structure

```
coffee_shop/
├── coffee.py     # Coffee class definition
├── customer.py   # Customer class definition
├── order.py      # Order class definition
└── main.py       # Optional entry point or testing script
```

---

## 🧠 Overview

This app models a basic coffee shop ordering system with three classes:

* `Customer`: Can place orders and track their coffee history.
* `Coffee`: Represents a type of coffee with tracked orders.
* `Order`: Represents a transaction between a customer and a coffee.

All relationships are bidirectional and automatically updated upon order creation.

---

## 👤 Customer

### Initialization

```python
customer = Customer("Alex")
```

* **Name must be a string** between 1–15 characters.

### Methods

| Method                                     | Description                                                  |
| ------------------------------------------ | ------------------------------------------------------------ |
| `name` (property)                          | Get/set the customer's name with validation.                 |
| `orders()`                                 | Returns all orders placed by the customer.                   |
| `coffees()`                                | Returns a unique list of `Coffee` instances ordered.         |
| `create_order(coffee, price)`              | Creates a new order with the given coffee and price.         |
| `most_aficionado(coffee)` *(class method)* | Returns the customer who spent the most on the given coffee. |

---

## ☕ Coffee

### Initialization

```python
coffee = Coffee("Latte")
```

* **Name must be a string** of **at least 3 characters**.
* Once initialized, the name cannot be changed.

### Methods

| Method            | Description                                                   |
| ----------------- | ------------------------------------------------------------- |
| `name` (property) | Get the name of the coffee.                                   |
| `orders()`        | Returns all orders made for this coffee.                      |
| `customers()`     | Returns a unique list of `Customer` instances who ordered it. |
| `num_orders()`    | Returns the number of orders made.                            |
| `average_price()` | Returns the average price paid for this coffee.               |

---

## 📦 Order

### Initialization

```python
order = Order(customer, coffee, 4.5)
```

* Requires:

  * `Customer` instance
  * `Coffee` instance
  * `price`: must be a `float` between `1.0` and `10.0`
* Automatically updates the customer’s and coffee’s order lists.

### Properties

| Property   | Description                             |
| ---------- | --------------------------------------- |
| `customer` | Returns the linked `Customer` instance. |
| `coffee`   | Returns the linked `Coffee` instance.   |
| `price`    | Returns the order price (float).        |

---

## 🔀 Object Relationships

```python
# Linking objects
alex = Customer("Alex")
latte = Coffee("Latte")
alex.create_order(latte, 3.5)

# Accessing relationships
alex.orders()        # [Order]
alex.coffees()       # [latte]
latte.orders()       # [Order]
latte.customers()    # [alex]
```

---

## ✅ Validation Summary

| Field            | Validation                       |
| ---------------- | -------------------------------- |
| `Customer.name`  | str, 1–15 characters             |
| `Coffee.name`    | str, min 3 characters, immutable |
| `Order.price`    | float, 1.0–10.0                  |
| `Order.customer` | Must be a `Customer` instance    |
| `Order.coffee`   | Must be a `Coffee` instance      |

---

## 🧪 Example Usage

```python
from customer import Customer
from coffee import Coffee

c = Customer("Lena")
capp = Coffee("Cappuccino")

c.create_order(capp, 4.0)
c.create_order(capp, 5.0)

print(c.coffees())             # [capp]
print(capp.num_orders())       # 2
print(capp.average_price())    # 4.5
```

---

## 📌 Notes

* To avoid circular imports, `create_order()` handles importing `Order` within the method body.
* All relationships are automatically synchronized when using `create_order()`. coffee-code-challenge