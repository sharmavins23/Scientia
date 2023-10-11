The grid cell is a type of [[Neuron|neuron]] within the [[Entorhinal Cortex|entorhinal cortex]] firing at regular intervals as an animal navigates an open area, allowing it to understand its position in space by storing and integrating information about location, distance, and direction. It's thought to take inputs from the [[Speed Cell|speed cell]] and [[Head Direction Cell|head direction cell]] to compute its own path and fire based on this positioning.

![[Wikipedia's Autocorrelation of Grid Cells in Physical Space.jpg]]

Interestingly, the grid cell fires at extremely regular patterns in fixed space (as seen in the above picture - Red indicates higher firing amounts). These extremely regular 'hexagonal' or 'square-like' patterns are thought to be composed together in 'grid cell modules.'

Alongside the [[Boundary Cell|boundary cell]], [[Head Direction Cell|head direction cell]], [[Place Cell|place cell]], and [[Speed Cell|speed cell]], they form a larger set of [[Neuron|neurons]] involved in cognitive mapping of an environment.

## Grid Cell Modules

Suppose a grid cell is defined as a value that fires when an animal travels over any $x, y$ such that $x=[x]$ and $y=[y]$, i.e. $x,y$ are discrete values. Conceptually, the animal may be at any point in the Cartesian plane, as long as they are at an integer-oriented location.

Several grid cells may choose to 'transform' the Cartesian plane by rotation or by scale (or both). With many grid cells overlapping and firing, this patterning eventually generates a [[sparse distributed representation|SDR matrix]] of the animal's position travelling through a box.

## Theta Rhythmicity

Like other parts of the [[Hippocampus (Archicortex)|hippocampal formation]] and [[Entorhinal Cortex|ERC]], neural activity seems heavily dependent on a [[hippocampal theta rhythm|theta wave]]. This frequency seems to be $6\to 9$ Hz in rats. Grid cells, in particular, seem to align their phases fairly well based on theta waves, 'resetting' as animals pass through grid vertices.