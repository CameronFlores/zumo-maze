# Milestone 2
## Get the Zumo to follow a line on the floor for at least 4 feet

## Proof
[![Milestone 2](http://img.youtube.com/vi/DObMGvQM3i0/0.jpg)](https://www.youtube.com/watch?v=DObMGvQM3i0 "Milestone 2")


## Notes
### Max Speed
While I found no need to greatly change the proportion gain I found that 300 was a reliable BASE_SPEED. 
As I needed help in all aspects of learning how to work the zumo I went straight to the tutorial, this is how I understand the variables:
### follow_line
PROPRTION_GAIN- helps center the robot based on line position.

DERIVATIVE_GAIN- helps center the robot based on previous error, speed up when we're getting off center fast but slow down once we're within a certain threshold.

## Problems
### Callibration
While I was able to get the zumo to move and even turn the way I wanted it to I was unable to get it to follow a line. After consulting the tutorial I learned about callibration as well as how to read data from line sensors.
### Takeaway
Exploring the follow_line function wasn't much of a concern to me as the maze will have straight lines, our code only needs to handle miniscule centering as opposed to the curved lines shown in the tutorial. What I take away from this is that I may be able to speed up the zumo when I give it straight lines.
