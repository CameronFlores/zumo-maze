# Milestone 4
## Get the Zumo to navigate a simple maze with no branching (only one path) and stop when it reaches the end goal
This milestone is simply a matter of combining the previous milestones and adding a right turn function.

## Proof
[![Milestone 4](http://img.youtube.com/vi/3s-mwgOtqvA/0.jpg)](https://www.youtube.com/watch?v=3s-mwgOtqvA "Milestone 4")


## Notes
### Max Speed
To get the zumo up the max speed we use the same reasoining from the previous milestones. 
Going straight we go up to 300 so that we can read turns correctly. 
When turning we can go up to 500 as to half the tutorial's turning time and callibrate it as variables change.
### Goal stop
Stop at T branch (we sense black on all sensors)
### Proprtional and Derivative Approach
* error is how off center zumo is
  int error = line_position - 2500;
* error_change is how off center zumo is compared to last error 
  int error_change = error - last_error;
* PROPRTION_GAIN means slow down as we reach the center
* DERIVATIVE_GAIN means if we're very off center we need to straighten ourselves quickly
```
  double PROPORTION_GAIN = 0.5;
  double DERIVATIVE_GAIN = 3;
  ...
  int left_speed = BASE_SPEED + PROPORTION_GAIN * error + DERIVATIVE_GAIN * error_change;
  int right_speed = BASE_SPEED + -PROPORTION_GAIN * error + -DERIVATIVE_GAIN * error_change;
```
## Problems
As this is just combining the previous milestones there are no new problems.
