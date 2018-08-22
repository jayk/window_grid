# window_grid

The window_grid script provides tiling-like window-placement 
capabilities for any window-manager. It is ideal for mapping 
to particular key-strokes to resize / reposition windows
on demand. 

![Window-grid demo](/screenshot/window-grid.gif)

This script positions any X11 window based on a grid. 
The grid is subdivided, by default, into 8 segments in 
each direction. (This can be overridden using the -d flag.)

This script requires the following tools to be installed:
`xprop` `wmctrl` `xdotool` and `xrandr`.  

Examples:

    # make active window take up top-left quadrant
    window_grid -w 4 -h 4 -x 0 -y 0
    
    # place active window in bottom-right quadrant
    window_grid -w 4 -h 4 -x 4 -y 4

    # place active window on left-half of screen
    window_grid -w 4 -h 8 -x 0 -y 0

    # place active window at center of screen, with 
    # one grid-space of space between window and 
    # edge of screen
    window_grid -w 6 -h 6 -x 1 -y 1

    # Expand active window's width by one grid-space
    window_grid -w +1

    # Move window to second monitor at top-left
    window_grid -s 1 -x 0 -y 0

    # snap active window fit into the closest grid
    # spaces based on its current size and position
    window_grid -c both

Position and size are specified in grid-units and can be relative.
for example, the options -x 1 -y 1 will place the top-left of the
window 1 grid unit down, and 1 grid-unit right of the top-left of
the screen.  You can also use -x +1 or -x -1 to move the window
one grid unit to the right or left respectively.

Height and width are specified the same way and can also be relative
so if you specify -w +1, the window will be made one grid-unit larger
than it currently is.  The minimum size of a window is 1 grid-unit
in each-direction.  The maximum is the size of the entire screen.

This script works on the active window by default. You can operate
on any window instead by providing its window-id using the -i flag. 

Note that the actual pixel-size of a grid segment will depend on the
your screen size.  For example, for a 1920x1080 display, the default
size of a 1x1 grid segment is 240 x 135. 

## Multiple Monitors

window_grid is multi-display aware and divides each monitor
according to the resolution of that monitor. It can place windows
on multiple screens, and works as you would expect in most 'normal' 
multi-monitor setups.

By default, all positions and sizes are considered relative to the 
monitor the window is currently on. You can switch the 
destination monitor by using the `-s` flag. Screens start at 0 
and are enumerated in the order they are returned by xrandr.
