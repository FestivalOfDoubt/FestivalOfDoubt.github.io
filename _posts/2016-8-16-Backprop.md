---
layout:     post
title:      Backprop
date:       2016-8-17 
author:     Amonoymynmns
visible:    false
---

## Matrix derivates

Let $y = Wx$ If W is a vector and x is a vector then we have the familiar result that $\frac{\partial y}{\partial W} = x$. Actually, this is wrong. The partial differential should be a matrix,… blah blah. We get away with this because J(x) is diagonal and therefore is the same as element wise multiplication.


## Automatic gradients

You may have noticed that each function `Softmax, Layer, …` has two methods, `.calc` and `.grad`. This allowed us to evaluate the function, and its gradient at a point. However, this is pointing towards something deeper. 

The usual story, but related to the structure of code, which should help make the connection to duals clear?

```python
Sigmoid := Dual(Forward, Backward)
Layer := Dual(Forward, Backward)
MultiLayer := Dual(Forward, Backward)

```


## Efficiency

Tapes, graphs, 

You may have also noticed that a few things were repeated within the code (e.g. the evaluation of the activation functions, when we already had used it…). The point is that this code could easily be optimised if we had kept track of which … how about using a tape? or even better a computational graph?