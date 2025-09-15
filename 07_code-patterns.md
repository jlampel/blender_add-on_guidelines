---
excerpt: Recommendations for building add-ons for Blender
nav_order: 7
nav_exclude: false
search_exclude: false
---

# Code Patterns

## BMesh

When altering meshes, it is important to work with BMesh carefully. Mistakes in memory ownership and reference management can cause errors that are difficult to debug and can even break other add-ons the user may have enabled. Here are some important rules to follow:

- Edit Mesh BMesh is owned by Blender and obtained via `bmesh.frem_edit_mesh()`
    - DO use the reference temporarily

    - DO get fresh references when needed instead of storing stale ones
    - DO NOT store long term references of it

    - DO clear references via Python's garbage collector (`bm = None`)
    - DO NOT call `.free()` on it

    - DO use BMesh objects locally within functions (`bm = bmesh.from_edit_mesh()`)
    - DO NOT use BMesh objects as instance variables (`self.bm = bmesh.from_edit_mesh()`)

- New BMesh is owned by you, fellow add-on developer, and is created via `bmesh.new()`
    - DO call `.free()` when finished with it
    - DO manage its lifecycle


Remember, in Edit Mesh BMesh, you are NOT the owner nor have full control over it! Always call `ensure_lookup_table()` before accessing elements by index or handle IndexError gracefully and refresh tables as needed.


## Draw Callbacks

A draw callback is a function that runs after every draw call and is typically used when drawing custom OpenGL UI elements on top of Blender. Uncaught exception errors in draw callbacks will reliably cause Blender to lock up, so it is important to always wrap them in a `try` block.

Also, limit the amount of computation done in draw callbacks to just what is needed for drawing. Do as much computation as possible beforehand and cache the result so that the draw callback just uses the already computed data. You can no-op in the draw call if the cache is not finished and then tag redraw when the chaching is complete.
