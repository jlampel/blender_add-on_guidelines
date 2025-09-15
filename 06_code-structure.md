---
excerpt: Recommendations for building add-ons for Blender
nav_order: 6
nav_exclude: false
search_exclude: false
---

# Code Structure

## Files

All add-ons should use the multi-file structure instead of being a single python file, even if it is incredibly simple, so that it can work with add-on updaters and the Blender development plugin for Visual Studio Code.

Folder and file names should not contain spaces or any special characters except for underscores. Python does not work well or at all when the module / file names contain spaces, dashes, or periods. Blender is able to get around this, but it will still cause complications. The only safe non-alphanumeric character is the underscore.

Use forward slashes (`/`) when referencing files paths rather than backslashes (`\`), since the first will work on both Windows and Linux while the latter will not work on Linux and sometimes need to be doubled (`\\`) on Windows to avoid accidentally creating a character code (such as `\n`).

## External Modules

Some add-ons may require external modules in order to function, which may introduce dependency issues when not managed correctly. If at all possible, it’s best to bundle any necessary modules with the add-on so that there are fewer things that could go wrong during the installation process.

If the module can’t be distributed with the add-on, for example if it would break copyright to do so, the add-on should detect whether or not the correct version of the modules are installed, provide a link to where the user can install or update the module, and have a customizable path for where the add-on looks for the module so that the user can install it in any directory they choose. Rather than return an error, the add-on should require the correct version of the module before registering the operators that depend on it. The add-on should also check the installation of the module every time it’s registered and return a warning if it detects a potential conflict.