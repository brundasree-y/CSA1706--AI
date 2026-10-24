import heapq

graph = {
    'A': ['B', 'C', 'D'],
    'B': ['A', 'E'],
    'C': ['A', 'E', 'F'],
    'D': ['A', 'F'],
    'E': ['B', 'C', 'H'],
    'F': ['C', 'D', 'G'],
    'H': ['E', 'G'],
    'G': ['F', 'H']
}

h = {
    'A': 40, 'B': 32, 'C': 25, 'D': 35,
    'E': 19, 'F': 17, 'H': 10, 'G': 0
}

def gbfs(start, goal):
    queue = [(h[start], start, [start])]
    visited = set()

    while queue:
        _, node, path = heapq.heappop(queue)

        if node in visited:
            continue
        visited.add(node)

        if node == goal:
            print("Path:", " -> ".join(path))
            return

        for neighbor in graph[node]:
            if neighbor not in visited:
                heapq.heappush(
                    queue,
                    (h[neighbor], neighbor, path + [neighbor])
                )

gbfs('A', 'G')
