import heapq

graph = { 'V1': {'V2': 9, 'V3': 4}, 'V2': {'V3': 2, 'V4': 7, 'V5': 3}, 'V3': {'V4': 1, 'V5': 6}, 'V4': {'V5': 4, 'V6': 8}, 'V5': {'V6': 2}, 'V6': {} }

def uniform_cost_search(start, goal): queue = [(0, start, [start])] visited = set()

while queue:
    cost, node, path = heapq.heappop(queue)

    if node in visited:
        continue

    visited.add(node)

    if node == goal:
        print("Path:", " -> ".join(path))
        print("Total Cost:", cost)
        return

    for neighbor, weight in graph[node].items():
        if neighbor not in visited:
            heapq.heappush(
                queue,
                (cost + weight, neighbor,
                 path + [neighbor])
            )

print("Goal not found")
uniform_cost_search('V1', 'V6')
