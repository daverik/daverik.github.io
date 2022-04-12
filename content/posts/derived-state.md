---
title: "Use Derived State"
date: 2022-04-12T16:00:43+02:00
draft: true
tags: ["programming", "typescript", "react"]
---

This is a bit of a pet peeve of mine.

When reviewing applications I often see candidates store redundant state. Here's an example:

```
type ShoppingCart = {
  items: Array<{ price: number, quantity: number }>
  count: number
  total: number
}
```

Then when they add a new item to the cart they update the count and total in the shopping cart. The same goes when removing or
in any other way modifying the state of the shopping cart.

See, this is completely redundant. "count" can already be derived from items.length and "total" is just the sum of price * quantity for all items.

Less state means less things that can be wrong. It also means you have less to think about when adding a new function that modifies the state of the shopping cart.

https://isamatov.com/react-derived-state/