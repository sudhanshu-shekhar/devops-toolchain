A network of circuitous indirections used to manage configuration and seem to intertwine like a labyrinth of straw in a bird nest. People often construct a bird nest in order to provide a consistent location for an external dependency.

Unfortunately, while the network of indirections may originally have served the purpose of a reliable abstraction, it comes at the expense of a new burden, administration of the bird nest, itself. Configuration bird nests are hard to maintain because they are brittle, unwieldily, tangled, and difficult to repair.

Configuration bird nests typically evolve in to multiple levels, and when one attempts to navigate their structure, they get the sense they are playing a game of mental pin ball. Indeed, one might find nested nests, as is the case when one mechanism of indirection gets mixed up with the mechanism of another kind.

Bird nests have the nasty effect of encouraging administrators of bringing more "straw" to the nest. Configuration bird nests are similar to <a href='http://c2.com/cgi/wiki?BigBallOfMud'>big balls of mud</a> except that often times, bird nest structure is premeditated along with the expectation the structure will require tending.

Example: SymbolicLink Bird Nest

A SymbolicLink Birds Nest, is a delicately tended structure of symbolic links typically exposing a single "well known" path with multiple levels of symbolic links below. Manifestations of this anti-pattern often emerge when an application requires a consistent path but the system infrastructure must be malleable.

Of course, limited use of symbolic links serves a a purpose but one must question situations when more than one level is in use.

Example: File Include Bird Nest
Configuration files are often organized into sections. As time goes on it is sometimes desirable to store each section in its own file so they can be individually managed and tied together via "include" statements. This often results in the administrator having to visit many files to understand overall structure.