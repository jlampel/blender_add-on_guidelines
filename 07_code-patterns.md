# Code Patterns

## Draw Callbacks

A draw callback is a function that runs after every draw call and is typically used when drawing custom OpenGL UI elements on top of Blender. Uncaught exception errors in draw callbacks will reliably cause Blender to lock up, so it is important to always wrap them in a `try` block. 

Also, limit the amount of computation done in draw callbacks to just what is needed for drawing. Do as much computation as possible beforehand and cache the result so that the draw callback just uses the already computed data. You can no-op in the draw call if the cache is not finished and then tag redraw when the chaching is complete. 
