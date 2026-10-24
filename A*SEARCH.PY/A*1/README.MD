import heapq

graph = {
    'S': {'A': 3, 'D': 4},
    'A': {'S': 3, 'D': 5, 'B': 4},
    'B': {'A': 4, 'C': 4, 'E': 5},
    'C': {'B': 4},
    'D': {'S': 4, 'A': 5, 'E': 2},
    'E': {'D': 2, 'B': 5, 'F': 4},
    'F': {'E': 4, 'G': 3.5},
    'G': {'F': 3.5}
}

h = {
    'S': 11.5, 'A': 10.1, 'B': 6.8,
    'C': 3.4, 'D': 9.2, 'E': 7.1,
    'F': 3.5, 'G': 0
}

def astar(start, goal):
    queue = [(h[start], 0, start, [start])]
    best = {start: 0}

    while queue:
        f, cost, node, path = heapq.heappop(queue)

        if node == goal:
            print("Path:", " -> ".join(path))
            print("Cost:", cost)
            return

        if cost > best[node]:
            continue

        for neighbor, distance in graph[node].items():
            new_cost = cost + distance

            if new_cost < best.get(neighbor, float('inf')):
                best[neighbor] = new_cost
                heapq.heappush(
                    queue,
                    (new_cost + h[neighbor],
                     new_cost, neighbor,
                     path + [neighbor])
                )

astar('S', 'G')
