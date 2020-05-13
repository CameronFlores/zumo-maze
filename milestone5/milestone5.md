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

Apart from typical turning callibration, my problem before looking at the full solution was when I tried a backtracking algorithm. This would have worked by having ranked different directions. I would have recorded every intersection and kept track of which branches of the intersection I explored so that as soon as I reached a dead end I would back track to the latest intersection and explore its children. I found this difficult to do for if I turned around for a backtrack the intersections would be in a different direction and I would somehow need to reflect this in the code when choosing a new direction to go to. But after reading up on the rules I found that  I wasn't timed on the first part of going through the maze. This meant that it didn't matter if I didn't have the optimal algorithm to find the end all I needed was a way to optimally shorten my path. With the help of the tutorial I switched to the left-hand-on-the-wall strategy so I could find a simplier solution as well as follow along when the tutorial for path shortening is eventually realeased.

Before looking at the tutorial I had a priority turn system which was something akin to:
```
while (line_on_left || line_on_right) {
      finish_counter++;
      if (finish_counter > 60) {
        solved();
      }
      else if (line_on_left) {
        path[turn_counter] = 'L';
        turn_counter++;
        turn_left();
      }
      else if (line_straight) {
        path[turn_counter] = 'S';
        turn_counter++;
        follow_line();
      }
      else if (line_on_right) {
        path[turn_counter] = 'R';
        turn_counter++;
        turn_right();
      }
    } 
```

Notes/buzzer won't play. Had to debug by commenting out parts of the code and changing variables in a way that narrowed down possible errors. Most common error I found was going or turning too fast for the sensors to read.

