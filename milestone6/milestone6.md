# Milestone 6
## Get the Zumo to solve a maze with branching and then repeat the maze and follow a memorized path

## Proof
https://www.youtube.com/watch?v=7Bb1Is0jDqo

## Notes
### Turn recording
Update an array everytime you turn so that you can recall what turns you made from the start to the end goal.

### Path optimization
The most optimal path (or at least what we need to account for in this specific maze) is one without any u-turns. We do this by replacing all xUy sequences with their enumerated direction (adding the degrees of x, U, and y to get our new direction). Using our recording, every time we sense a turn we use the pre-recorded turns to instantly make a decision.

## Problems
The only problem would be speed and performance, Since I used the same BASE_SPEED, THRESHOLD and other variables my zumo was only as fast the tutorial which everyone else has access to.

### Path reduce
Shortest path should be \[L, S, S, R, L, L, R, R, S, R, R, L, R, L, R\]

No real problems with path reduce however...
* There is no shorter path than the one calculated by the tutorial code and there is no need for improvement in this aspect
* I originally formatted this function with a case statement for the character search and an if-else if statement for the total_angle search for the sake of optimizing however I noticed that it didn't matter as this function would be quickly computed after finishing the maze the first time around and this slight improve wouldn't show in the second run.
