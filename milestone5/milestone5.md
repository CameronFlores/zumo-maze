# Milestone 5
## Get the Zumo to solve a maze with branching

## Proof
https://www.youtube.com/watch?v=OEinZ59EXVA

## Notes
### left wall algorithm
In other words, whenever we reach a turn or intersection we prioritize in this order left, straight, and right.
### end goal
End goal is a thick T branch, all sensors are black for a long time.
### 1 Left turn
Immediately turn left
### 1 Right turn
Immediately turn right
### Multiple turns
Priority in order: Turn left, go straight, go right

## Problems
Follow tutorial in order to learn how to interact with intersections and deal with potentially skipping valuable turns.

Apart from typical turning callibration, my problem before looking at the full solution was when I tried a backtracking algorithm. This would have worked by having ranked different directions. I would have recorded every intersection and kept track of which branches of the intersection I explored so that as soon as I reached a dead end I would back track to the latest intersection and explore its children. I found this difficult to do for if I turned around for a backtrack the intersections would be in a different direction and I would somehow need to reflect this in the code when choosing a new direction to go to. But after reading up on the rules I found that  I wasn't timed on the first part of going through the maze. This meant that it didn't matter if I didn't have the optimal algorithm to find the end all I needed was a way to optimally shorten my path. 

With the help of the tutorial I switched to the left-hand-on-the-wall strategy.

I had a priority turn system which was something akin to:
```
void turn_priority() {
  line_position = linesensors.readLine(sensor_vals);
  int finish_counter = 0;

  bool line_on_left = sensor_vals[0] > THRESHOLD;
  bool line_on_right = sensor_vals[5] > THRESHOLD;
  bool line_straight = line_position < 3000 || line_position > 2000;

  if (line_straight && !line_on_left && !line_on_right) {
    motors.setSpeeds(BASE_SPEED, BASE_SPEED);
    follow_line();
  }
  else if (!line_on_left && !line_on_right && !line_straight) {
    path[turn_counter] = 'U';
    turn_counter++;
    u_turn();
  }
  else {
    bool was_left = line_on_left;
    bool was_right = line_on_right;
    while (line_on_left || line_on_right) {
      finish_counter++;
      if (finish_counter > 60) {
        solved();
      }
      else if (was_left && !line_on_left || !line_on_right) {
        path[turn_counter] = 'L';
        turn_counter++;
        turn_left();
        break;
      }
      else if (line_straight && !line_on_left || !line_on_right) {
        path[turn_counter] = 'S';
        turn_counter++;
        follow_line();
        break;
      }
      else if (was_right && !line_on_left || !line_on_right) {
        path[turn_counter] = 'R';
        turn_counter++;
        turn_right();
        break;
      }
    } 
  }
}
```

While this solution (and other similar versions of this code) worked for the most part it had numerous problems.
* Jerky at intersections, always swerves in order to straighten itself. howeber this could be attributed to the ballastic turning functions
```
void turn_left() {
  motors.setSpeeds(-500, 500);
  delay(100);
}

void turn_right() {
  motors.setSpeeds(500, -500);
  delay(100);
}

void u_turn() {
  motors.setSpeeds(-500, 500);
  delay(150);
}
```
* Difficulty implementing finish_counter. Required that all sensors were triggered for a long period of time. Occassionally resulted in intersections with a left and right turn pausing the zumo 

While this solution works I defaulted to the tutorial code as it wasn't jerky at the intersections and was better suited for implementing finish_counter. 

