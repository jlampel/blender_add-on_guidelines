---
excerpt: Recommendations for building add-ons for Blender
nav_order: 5
nav_exclude: false
search_exclude: false
---

# Warnings and Errors

Users should not be able to use an add-on in contexts that it does not work in. For example, if it only works in object and edit mode, the options to use it should not appear in draw mode or sculpt mode. Operators should remain grayed out until all knowable conditions are met, such as having more than one object selected or an object of a certain type selected. The tooltip should clearly state the conditions so that the user can know what they need to do to enable it. It is always better to not allow the user to use the function at all than to return an error.

If an add-on should or might be able to work but it is impossible to know if it will return the expected behavior, or if the it detects conditions that are not ideal for its use, a concise warning should be displayed in the status bar as well as a more descriptive one in the console if necessary. Nothing should appear under the mouse or block interaction. This also implies that ideal conditions should be well thought through and checked for.

Ideally, users should never encounter an error, but unfortunately that’s an impossible goal. Errors should be reported to the user in the status bar and in the console. The message in the status bar should be concise but descriptive if possible, and the message in the console should show the full python exception.

In addition to the status bar and console messages, a popup should appear that allows the user to directly report an error, either via GitHub, the Blender Market, or email, depending on the preference of the creator. The error reporting function should copy the contents of the console and add any relevant information about the scene so that the user doesn’t have to go digging for or remember any technical information. If possible, options to also send along the .blend file and computer specs should be included, but they need to be explicit options for those under NDAs and those with privacy concerns.
