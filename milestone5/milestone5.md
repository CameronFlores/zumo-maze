# Milestone 5
## Get the Zumo to solve a maze with branching

## Proof


## Notes
### left wall algorithm
In other words, whenever we reach a turn or intersection we prioritize in this order left, straight, and right.

## Problems
Apart from typical turning callibration, my problem before looking at the full solution was when I tried a backtracking algorithm. This would have worked by having ranked different directions. I would have recorded every intersection and kept track of which branches of the intersection I explored so that as soon as I reached a dead end I would back track to the latest intersection and explore its children. I fouund this difficult to do for if I turned around for a backtrack the intersections would be in a different direction and I would somehow need to reflect this in the code when choosing a new direction to go to. But after raeding up on the rules I found that because I wasn't timed on the first part of going through the maze it didn't matter if I didn't have the optimal algorithm and with the help of the tutorial I switched to the left-hand-on-the-wall strategy.
