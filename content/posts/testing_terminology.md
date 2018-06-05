---
title: "Testing Terminology: Integrating your units"
date: 2018-05-24T07:27:17+03:00
tags: ["python", "testing"]
draft: true
---

It's always good to start with an example. Let's say we're traveling to Italy to enjoy its wonderful cousine. 
We want to get a Pizza and one restaurant's menu says it costs 9.99€ (Euros). As tourists from afar we are used to 
evaluating prices at our own currency, so we wrote the following function: 


{{< highlight python >}}
def calculate_price_in_required_currency(price, currency, required_currency):
    exchange_rate = get_currency_exchange_rate(currency, required_currency)
    return float(price) * exchange_rate
{{< /highlight >}}

This function performs our simple task: Given a **`price`** (9.99€) 
in a **`currency`** (Euro [EUR]), fetch (from a public API) an updated currency to **`required_currency`** exchange rate 
(1.21 EUR/USD at time of writing), calculate and return the price in the required currency.

{{< highlight python >}}
calculate_price_in_required_currency(9.99, 'EUR', 'USD')
>>> 12.06

{{< /highlight >}}

Let's define a few concepts based on our function:

* **Input** - `price`, `currency` and `required_currency`. Parameters that are inserted to the component and represents pieces of information for it.
* **Business Logic** - Our function gets the most recent exchange rate, calculates and provides the price in the required currency. 
When we use the function, we expect it to behave in a certain expected way, that is, promise to keep up with its business logic.
This does not mean the calculating would yield the same result if we performed it repeatedly with the same input (exchange rates tend to change over time).
But it will always return a number that represents the price in our desired currency. The function is expected to provide different outputs for different inputs.
* **Dependency** - `get_currency_exchange_rate` is an external service. Our function depends on it to perform its business logic.
Our function uses the service's interface and expects a specific type of result. specifically- 
given currency A and B, it'll return their updated exchange rate.
* **Output** - price in required currency.

Given these definitions, There are two main concerns 

1. The function would always behave the same
2. The function's dependencies would hold true to their interfaces.

### Types of Developer Tests
#### Unit - Testing a component in isolation
> a component does what it should, given fixed parameters and dependency states.

![Unit Tests scheme](/imgs/unit.png)

Key concepts: Business Logic, Coverage

Focus: Expected Outcome, Edge Cases.


#### Integration - Testing Component's compatibility with dependencies
![Integration Test scheme](/imgs/integration.png)


 


### Test Driver Development (TDD)
### Coverage and What to test