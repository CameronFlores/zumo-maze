# Milestone 7
## Get the Zumo to solve a maze with branching and then repeat the maze and follow a memorized path

## Proof


## Notes
### Max Speed
After trial and error I found that the max speed for straight lines is 250 and turns is 300 (I'm assuming we are forced to use lower values to compensate since there are more calculations to be done).

Addressing the first problem I stated below, I modified the runSolvedMaze() function to speed up to 400 when I want to run straight through an intersection (because I don't have to worry about calculations or the positioning of the sensors) and slow down to 300 and 250 when a turn is coming. (using the recorded array)

## Problems
* To further optimize I could use millis() to record how long it takes to go one unit and relative to this information map a distance between turns and intersections. If I could record not just turns but units themselves I would be able to run a path without reading any intersectinos at all.

* Ballistic turning does not work. For whatever reason trying to use ballistic turning in this format results in the robot's sensors not reading any turns and repeatedly u-turning. I had to rely on the tutorial's sensor-based turning instead. Additionally, using a hybrid-turning system seems to just make the robot turn too far and often leads to more sensor errors.

* There is no shorter path than the one calculated by the tutorial code. My depth-first-search method wasn't working so I simplified things and followed the tutorial code.

* We could possibly go faster with a smaller derivative variable and a different error threshold though I didn't bother messing with it as inaccuracies and misreading turns is already happening and I didn't htink it was much of a factor since we're only dealing with straight lines.
