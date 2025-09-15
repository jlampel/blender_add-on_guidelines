---
excerpt: Recommendations for building add-ons for Blender
nav_order: 8
nav_exclude: false
search_exclude: false
---

# Delivering Updates

For paid add-ons, minor upgrades, quality of life improvements, and compatibility updates should be free for the user. Significant version updates or overhauls that introduce several new features or otherwise require a large amount of development time can be paid. However, if there is a paid upgrade, the old version should, at minimum, continue to support current Blender LTS versions for at least two years.

Ideally, a user should be able to update their add-ons directly within Blender. Self-updating addons can run into unexpected issues though, so it would be better to use a secondary service, such as Blender Market’s proposed Hive add-on, to manage the rollout. That’s not possible at the moment though, so the current minimum acceptable solution is a button in the preferences that links to where they can check for updates on the web. Add-ons should never automatically update as that may cause the user’s files to break unexpectedly.

Any updater system should display a changelog before an update is installed so that the user can decide if they want to accept the change or not. Checking should happen after Blender has started so as not to slow down the boot process, and should ask if the user would like to restart Blender to apply the changes. Updates should be ignored if they are incompatible with the user’s Blender version. Any buttons to manage or update the add-on should either be placed at the bottom of the add-on’s menu or panel if it has one, or be placed in the add-ons preferences so as not to take up unnecessary space or attention when not actively needed.