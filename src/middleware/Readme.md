# Debounce
https://levelup.gitconnected.com/debounce-in-javascript-improve-your-applications-performance-5b01855e086
## Purpose
Keep the next menu from being loaded immediately on hover so that users can take their time navigating between menus (the altnerative is to force users to move from menu to sub-menu in a horizontal line).
## API
Put a function, a delay time d, and an "immediate" flag in -- get out a function that will not call itself until d ms after its last trigger, thereupon executing its input.
## How It Works
1. Pass it a func(tion), a wait (time); tell it whether you want it to run (immediate)ly (after the wait time ?)
2. It gives you a function that...
3. Captures the context and args it is called with, passing them on to func (through "later")...
4. Clears any existing timeouts. 
5. The first time it is called, it sets a timer to execute "func". It resets the timer each additional time it is called. (This is closure magic -- "timeout" is preserved in the function's closure -- the debounce function which returns it and is called at the beginning.)
6. If it is "immediate", "func" gets executed on the first call of the debounced function. (?)

Still unclear: leading vs. tail-end execution = ?
## Problems
This should have a cancellation option so that the function does not get called if you exit the menu before it gets executed.