graph = {
    'A': ['B'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': ['C'],
    'F': ['G'],
    'G': []
}

def dfs(node, visited):
    if node not in visited:
        print(node, end=" ")
        visited.add(node)

        for neighbour in graph[node]:
            dfs(neighbour, visited)

dfs('A', set())
