# Development of My VEX VR Dynamic Maze Code

When I first began developing my code for the Dynamic Maze, I faced a significant challenge. Handling situations where the robot encountered walls on three sides. Initially, the robot would become stuck in an infinite loop, continuously turning in place because it lacked a clear path forward. This issue stemmed from an inadequate escape mechanism when no immediate routes were available.

To resolve this, I attempted to implement a reverse mechanic that would allow the robot to backtrack slightly before re-evaluating its surroundings. However, this solution proved inefficient. The robot would frequently reverse into previously explored areas, leading to unnecessary movements and inefficient pathfinding. It also failed to provide a reliable method for determining when and how far the robot should backtrack before trying a new direction.

The breakthrough came when I devised a more structured approach using the distance command and turning right by 90 degrees. Every 250mm that it drove forward, the robot would check its right to determine if there was a gap greater than 260mm. If such a gap was detected, it indicated a potential pathway, prompting the robot to turn and follow that route. If no viable opening was found, the robot continued moving forward. This provided a more systematic method of navigation, ensuring the robot did not get stuck in infinite loops or take unnecessary steps.

Another major challenge arose when the robot mistakenly detected the finish zone as an obstacle. Instead of stopping at the endpoint, it would turn around, treating the finish like a wall. The root of the issue was how my code prioritised sensor input. The down-eye sensor, responsible for detecting the finish, was not given priority over wall detection. To fix this, I restructured the sensor hierarchy in my code, ensuring that the robot first checked for the finish zone separately from walls before deciding on a movement.

After overcoming these challenges, I completed several key tasks:

Reaching the Finish: With the improvements to navigation and obstacle detection, the robot could successfully traverse the maze and stop at the finish.

Returning to the Start: To allow the robot to navigate back to the starting position, I implemented a stack-based approach. As the robot moved through the maze, it recorded each movement by appending it to a stack. Upon reaching the finish, the mapping function was terminated, and the robot began popping moves from the stack, executing the inverse of each action to retrace its path efficiently. 

Attempting Full Maze Mapping: My next goal was to map the entire maze efficiently. To achieve this, I researched Dijkstra’s algorithm for node-based pathfinding. However, implementing this in my code proved to be a challenge. Despite understanding the theory behind it, I struggled to adapt it within the constraints of VEX VR’s environment and my currently existing code. Unfortunately, I was unable to complete this feature, but the research provided valuable insights for future improvements.

Through these iterations and problem-solving approaches, I significantly improved my robot’s performance in navigating the dynamic maze. Although I didn’t achieve full mapping, the experience deepened my understanding of algorithmic problem-solving and autonomous navigation techniques.
