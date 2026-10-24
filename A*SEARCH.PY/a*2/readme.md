import heapq

graph = {
    'A': ['B', 'C'],
    'B': ['A', 'C', 'D'],
    'C': ['A', 'B', 'E'],
    'D': ['B', 'F', 'G'],
    'E': ['C', 'G'],
    'F': ['D', 'G'],
    'G': ['D', 'E', 'F']
}

h = {
    'A': 5, 'B': 6, 'C': 4,
    'D': 3, 'E': 3, 'F': 1, 'G': 0
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
