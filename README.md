# window_grid

Tools for adding grid/tiling functionality to any window manager.


The window_grid script provides tiling-like capabilities for any window-manager.

This script positions an X11 window based on a grid. 
The grid is subdivided, by default, into 8 segments in 
each direction. (This can be overridden using the -d flag.)

Position and size are specified in grid-units and can be relative.
for example, the options -x 1 -y 1 will place the top-left of the
window 1 grid unit down, and 1 grid-unit right of the top-left of
the screen.  You can also use -x +1 or -x -1 to move the window
one grid unit to the right or left respectively.

Height and width are specified the same way and can also be relative
so if you specify -w +1, the window will be made one grid-unit larger
than it currently is.  The minimum size of a window is 1 grid-unit
in each-direction.  The maximum is the size of the entire screen.

Note that the actual pixel-size of a grid segment will depend on the
your screen size.  For example, for a 1920x1080 display, the default
size of a 1x1 grid segment is 240 x 135. 

This script is screen-aware and divides each monitor according to 
the resolution of that monitor. It can place windows on multiple 
screens, and works in most 'normal' multi-monitor setups,
but note that it currently does not create windows larger than the 
screen the window starts on. Note also that when choosing sizes and 
positions, the grid size used is based on the monitor the window 
starts on. So in configurations where resolution is different, 
the grid may not line up the way you want. Because of this, if 
you wish to move windows between displays, it's best to use 
your window manager (or another tool) to move them to the 
display you want them on before invoking this script to do 
grid-positioning. This functionality may be added in a future 
version.
