# Milestone 7
## Get the Zumo to solve a maze with branching and then repeat the maze and follow a memorized path
Time to beat: 15s
## Proof
[![Milestone 7](http://img.youtube.com/vi/CHDmdfwsvJ8/0.jpg)](https://www.youtube.com/watch?v=CHDmdfwsvJ8 "Milestone 7")

About 13s (2 second improvement!)
## Notes
### Max Speed
After trial and error I found that the max speed for straight lines is 250 and turns is 300 (I'm assuming we are forced to use lower values as compared to previous Milestones in order to compensate since there are more calculations to be done).

Addressing the first problem I stated below, I modified the runSolvedMaze() function to speed up to 400 when I want to run straight through an intersection (because I don't have to worry about calculations or the positioning of the sensors) and slow down to 300 and 250 when a turn is coming. (using the recorded array)

## Problems
### Using millis()
I made a partner array (long path_time\[50\]) that recorded the difference of time between the end of one turn to the start of another turn. With this information I made a completely ballistic maze solver that didn't need to read sensors and didn't risk jerky movement at intersections I had problems with before. We take the time between turns (unused time in array gets deleted alongside path elements in path_reducer) and move forward at twice the speed in half the time.
And if there is a turn it is done ballastically and we go forward again until time is up and we perform the next turn.
However:
* Callibration was too difficult. While it was fast and moving in the correct, general direction each iteration made it slightly off track. It was too difficult to balance traction, uneven motors, and random error for this to work. I'd have to be really lucky to get an acceptable run given how many turns there are.

### Ballistic turning
* Ballistic turning does not work. Again callibaration was too difficult and it put the zumo in positions where it didn't know how to handle what it was sensing. Instead I sped up the rotation of reactive turns to be higher, the only problem with this is a little time is lost when he robot occassionally turns too far and needs to straighten out and turning speed had a smaller limit than what would be possible with ballastic turning.

### Acceleration function
* I also created a function that increased the BASE_SPEED every tenth second by 10 (using millis();) with a max speed of 300 if the upcoming turn was straight and decreased every tenth of a second by 10 with a min speed of 250 if the upcoming turn was left or right (slow down so that we can turn correctly). Essentially this would speed through intersections we go straight through and slow down when a turn is coming up
* Unfortunately this method doesn't account for left or right turns that are far away from each other and don't need to slow down for awhile.

### Current method
* I speed up when the upcoming turn is straight and slow down when an upcoming turn is left or right
* Like the acceleration function this method doesn't account for left or right turns that are far away from each other. However what made this function faster was the fact that we had a constant high speed in places where the acceleration had gradually increasing speed
* Given more time and testing I would improve this by combining this with my millis() idea and have the zumo run at high speeds until a path_time (changed to be proprtional to the speed of the car) is almost up. In this case we slow down at upcoming turns but only at the last second allowing for max speeds for as long as possible.
* However I still believe the fastest method would be the a completely ballastic maze run using millis() and instead of improving my current method I spent too much time tinkering with my ballastic method.
