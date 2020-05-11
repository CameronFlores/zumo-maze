# zumo-maze
## Milestones
- [x] Milestone 1- Create your own code that moves the Zumo at least 4 feet
- [x] Milestone 2- Get the Zumo to follow a line on the floor for at least 4 feet
- [x] Milestone 3- Get the Zumo to follow a line along 2' x 2' square. (Create a square using the tape, 2ft on each side. Place the Zumo anywhere on the square and get it to follow the square for at least a full lap.)
- [x] Milestone 4- Get the Zumo to navigate a simple maze with no branching (only one path) and stop when it reaches the end goal
- [x] Milestone 5- Get the Zumo to solve a maze with branching
- [x] Milestone 6- Get the Zumo to solve a maze with branching and then repeat the maze and follow a memorized path
- [x] Milestone 7 Have a final run in the practice maze of under XX seconds. (Will set this time once I have a practice maze up and running...)

Process:
In the rules we're told we're only timed for the second run of the maze meaning we can autonomously map the maze out for as long as we like(although for the sake of time I chose to priortize right hand turns as it's faster). This means time improvements must come through efficent movements (moving the robot at max speed, speeding up where we know we don't need to turn), short sensor pauses (as soon as you read a turn or intersection use ballastic movement to immediately take a turn), and an optimal shortest path algorithm.

With this in mind my goal is to play around with and understand the tutorials in order to find the max speeds that I can move and sense with.
