from collections import deque

graph = {
    0: [1],
    1: [3],
    2: [1],
    3: [4, 2],
    4: [5],
    5: [7],
    6: [4],
    7: [6]
}

def bfs(start):
    visited = {start}
    queue = deque([start])

    while queue:
        node = queue.popleft()
        print(node, end=" ")

        for neighbour in graph[node]:
            if neighbour not in visited:
                visited.add(neighbour)
                queue.append(neighbour)

bfs(0)
