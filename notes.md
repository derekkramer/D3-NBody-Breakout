# D3 Breakout Notes 2/8/18

## D3 (Data Driven Documents)

> - Library for producing dynamic, interactive data visualizations in web browsers
> - Started in 2011
> - Developed by Mike Bostock along with Jason Davies, Jeffrey Heer, Vadim Ogievetsky, and the Open Source community
> - Successor to Protovis, a visualization framework
> - D3.js was meant to be a clearer, better performing, more controllable visualization library

## N-Body Problem

> In physics, the n-body problem is the problem of predicting the individual motions of a group of celestial objects interacting with each other gravitationally.

## Functional Concepts

### HTML5 Canvas

`getContext(contextType)`

> Gives us an object that allows us to draw on the canvas element
>
> `contextType` is a string representing one of four types of contexts:
> - **"2d" - Allows for a 2D drawing context**
> - "webgl" - allows for 3D drawing in the canvas
> - "webgl2" - allows for 3D drawing in the WebGL version 2 scope
> - "bitmaprenderer" - allows for replacement of the canvas element with an Image Bitmap

### D3

`d3.range(n)`

> Form of D3 *scale* that is a function that maps from an input domain to an output range. Instead of using an array of exact values, it accepts raw data and converts it into a *range* within the bounds of the visualization.
>
> `n` is the number of values in that array/range

#### d3.forceSimulation()

`d3.forceSimulation(nodes)`

> A part of the d3-force sub-library that creates a new force simulation with the specified array of **nodes** and no forces.

`.drag(d)`

> Sets the drag effect on the nodes in the force simulation, in this case setting it to zero to mimic a  frictionless celestial simulation

`.alphaDecay(a)`

> Sets the "cooling" rate of the force simulation, or how long until the simulation will reach a stable state. In this case making our simulation perpetual

`.force("charge", f)`

> Sets the charge or force put upon a node/nodes within the simulation.

`.forceManyBody().strength(s)`

> This is what makes the simulation act our charge on **every** node in the simulation. The strength function sets the strength of that charge.

`.force("center", c)` & `.forceCenter(x, y)`

> Determines the center point inflicting the charge on the nodes in our simulation.

`.on("tick", ticked)`

> Gives us the opportunity to run the callback function `ticked` at every tick of our simulation, in this case drawing to the canvas with every iteration of the simulation.

`.scaleLinear()`, `.domain([a, b])` & `.clamp(bool)`

> Creates a linear scale with an input domain between `a` and `b`, with an output range specified in the same way (seen above). Linear scales in D3 preserve proportional differences. `clamp` determines whether or not the domain will constrain input values to the strict domain specified or extrapolate values outside of those two values.
>
> *e.g. With a `domain` of `[0, 10]` and a `range` of `[0, 20]`, if an input of `-10` is given, with `clamping(true)` it would change it to `0`, with `clamping(false)` it would accept the `-10` and output `-20` in the range.*