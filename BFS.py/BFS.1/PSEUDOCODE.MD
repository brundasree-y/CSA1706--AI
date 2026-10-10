BEGIN

1. Create a graph using an adjacency list.

2. Define BFS(start).

3. Initialize an empty set called VISITED.

4. Create a QUEUE and insert the START node.

5. WHILE QUEUE is not empty, DO

      a. Remove the first node from QUEUE.

      b. IF the node is not in VISITED, THEN

            i.  Print the node.

            ii. Add the node to VISITED.

            iii. Add all adjacent nodes to QUEUE.

      c. END IF

   END WHILE

6. Call BFS(A).

END
