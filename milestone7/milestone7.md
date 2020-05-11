# Milestone 7
## Get the Zumo to solve a maze with branching and then repeat the maze and follow a memorized path
In the rules we're told we're only timed for the second run of the maze meaning we can autonomously map the maze out for as long as we like(although for the sake of time I chose to priortize right hand turns as it's faster). This means time improvements must come through efficent movements (moving the robot at max speed, speeding up where we know we don't need to turn), short sensor pauses (as soon as you read a turn or intersection use ballastic movement to immediately take a turn), and an optimal shortest path algorithm.

## Proof


## Notes
### Max Speed
While line following can be done at high speeds, turn sensing (especially ballistic turning with) cannot handle the same high speeds. To adjust for this I allow the the zumo to speed up (and even skip sensing some intersections) along straight lines where there is at least 3 units of space between turns. 

I believe the max speed of the robot is 400 while the max speed that can sense turns is 300.

## Problems
To further optimize I would use millis() to record how long it takes to go one unit and relative to this information map a distance between turns and intersections allowing for speed ups between every turn and intersection.
