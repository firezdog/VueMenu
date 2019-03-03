# Debounce
## Purpose
Keep the next menu from being loaded immediately on hover so that users can take their time navigating between menus (the altnerative is to force users to move from menu to sub-menu in a horizontal line).
## API
Put a function, a delay time d, and an "immediate" flag in -- get out a function that will not call itself until d ms after its last trigger.
## How It Works
