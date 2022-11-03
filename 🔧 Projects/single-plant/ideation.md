# Ideation

Modelling:
- Randomly generate piece shapes
	- Convex Hull algorithm [1](https://cglab.ca/~sander/misc/ConvexGeneration/ValtrAlgorithm.java), [2](https://cglab.ca/~sander/misc/ConvexGeneration/convex.html)
- Back fill movement w/ random variation
- Tree counter + return to bagup + line in and line out
- Throw plots
- Override step distance
- Model how device will work
- Model optimal tree spacing

Device:
- PCB
- Bluetooth
- GPS (or on phone)
- Battery
- Casing + attachment + impact dampening
- Maybe consider having a "line in" button so the algorithm knows when the line in is over

Algorithm/Machine Learning
- Can try both approaches
- To save computational time, forget lines that are surrounded by other lines. This way, only the most recent line of trees is spaced off of or considered.
- [Find Closest Point](https://ptsjs.org/guide/op-0400)

App:
- Set spacing distance