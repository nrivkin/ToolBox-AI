To use this astar GUI/toy, hit the 'l' key to switch to the 'add lava tiles' mode. Then you can click on any cell to add or remove a lava tile from that cell. Hit the spacebar at any time to have Paul plan (or replan) his path, and highlight that path. To see the f,g, and h values that astar calculates, take a look at the instructions in question 1. Feel free to reach out at any time about problems.

0. Read up on astar [here](http://web.mit.edu/eranki/www/tutorials/search/) and [here](http://www.raywenderlich.com/4946/introduction-to-a-pathfinding). Do your best to understand what the pseudocode in the links mean. What are the advantages that A star has over breadth-first search? What advantages does A star have over depth-first search? 


depth-first searches do not always find the shortest path (they usually don't), and they are computationally intensive, potentially requiring iterating over all nodes.





1. Take a look at lines 124-127 of the code. Try commenting and uncommenting lines and running python astar.py to see what values are printed in each cell. Take a screenshot of each example with some lava tiles placed down, and in your own words, explain what f_score, g_score, and h_score are, and why you see those specific values in the screenshot.

f_score is the total predicted cost to reach th objective. It is the sum of g_score and h_score.

g_score is the distance traveled to reach the square in question. it is calculated by adding one to the parent square with the lowest g_score.

h_score is the distance from a square to the goal, ignoring obstacles. It is the predicted cost of reaching the goal from the location where it appears. It is not the actual number of steps it will takes, but a hueristic estimate.

The screenshots are in the image folder, and are named \*\_score_example.png. h_score shows the distance between the tile and the goal, regardless of obstacles. a specific example would be the green sqaure adjacent to paul. If you count the x distance that would need to be traversed to reacj the cake (ignoring obstacles), you will find it to be eqaul to 17 .g_score shows the distance that would have to be traveled to reach a square. Each square has a numder one greater than the lowest adjacent square. In the example, you can see this by examining any sqare and seeing that it is one greater than its lowest parent. f_score is the sum of g_score and h_score, which can be observed in the example by calculating the scores.



For questions 2, 3, and 4, you should implement the code to get the specified behavior, but also place tiles and set up a scenario/path where that newly implemented behavior is demonstrated (ex. Paul moving diagonally or moving through a swamp.) Then include a screenshot and explanation. Quoting Paul, "Once you make a change, you should include a screenshot of the pygame window that shows the generated path for a given set of obstacles. You should be ready to explain why the shown path is actually the shortest (for instance… “the diagonal move while costly, is necessary in order to reach the goal, paths consisting of just up, down, left, or right would not be able to reach the goal”)."

2. Read the get_open_adj_coords() function and lines 204 to 210 to get an idea of how valid adjacent cells are found. In the current code, valid adjacent cells only include the surrounding cells in the 4 cardinal directions, and moving to any of these cells costs 1 movement point. Add code changing the get_open_adj_coords() function so that surrounding diagonal cells are considered valid adjacent cells and moving to any of these cells costs 3 movement points. This will allow Paul to
move diagonally.

3. Change the program so that pressing 's' allows you to add swamp tiles. Paul should be able to move through swamp tiles, but they will slow him down! Moving into a swamp tile will cost 3 movement points, so Paul should really avoid moving through swamp tiles unless he has to. A swamp.jpg file has been provided for you in the /images folder. You will probably have to make some changes to the costs in get_open_adj_coords and write your own _add_swamp() function to get swamp tiles to behave correctly.

4. Evolve Paul and allow him to jump over lava! Add the ability for Paul to jump one square. This should cost 8 movement points, however. This will involve changing get_open_adj_coords().
