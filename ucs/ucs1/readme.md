graph = { 'S': {'A': 1, 'G': 12}, 'A': {'B': 3, 'C': 1}, 'B': {'D': 3}, 'C': {'D': 1, 'G': 2}, 'D': {'G': 3}, 'G': {} }

path = ['S', 'A', 'C', 'D', 'G']

cost = 0

for i in range(len(path) - 1): cost += graph[path[i]][path[i + 1]]

print("Path:", " -> ".join(path)) print("Total Cost:", cost)
