[sig.js](http://mmcdermo.github.io/sig.js)
======
Functional Reactive Programming for UI Design. 
* See examples & code at [mmcdermo.github.io/sig.js](http://mmcdermo.github.io/sig.js)

Intro
-----
In sig.js, Signals encapsulate values and vary over time. 

To create a signal that always has the value "42", we could write:
```
    var sig42 = sig.constant(42);
```
Say we want a signal that has the value "Clicked!" when the mouse is clicked and "Not clicked :(" when the mouse is not clicked. sig.Mouse.clicked is a signal that's true whenver the mouse is being clicked, and false otherwise. We can use *lift* to apply a function to the value of this signal: 
```
    var sigClicked = sig.Mouse.clicked.lift(
        function(c){ return c ? "Clicked!" : "Not clicked :(" });
```
For more info/examples see the examples page above. 

Theory
------
Signals model their own disruption in sig.js by possibly not carrying any value. They could be modeled by the haskell ADT:
    data Signal a = Signal a | SignalNothing

This is crucial because we allow signals to be created and destroyed.