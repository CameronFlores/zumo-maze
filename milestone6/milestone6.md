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
The only problem would be speed and performance, as I heavily relied on the tutorial to do this my solution is as slow as the standard speed.
