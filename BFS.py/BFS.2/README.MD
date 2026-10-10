from collections import deque

graph = {
    1: [2, 3],
    2: [1, 3, 4, 5],
    3: [1, 2, 4],
    4: [2, 3, 5],
    5: [2, 4]
}

def bfs(start):
    visited = set()
    queue = deque([start])

    while queue:
        node = queue.popleft()

        if node not in visited:
            print(node, end=" ")
            visited.add(node)

            for neighbour in graph[node]:
                if neighbour not in visited:
                    queue.append(neighbour)

bfs(1)
