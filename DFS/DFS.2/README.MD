graph = {
    1: [2, 3],
    2: [4, 5],
    3: [4],
    4: [5],
    5: []
}

def dfs(node, visited):
    if node not in visited:
        print(node, end=" ")
        visited.add(node)

        for neighbour in graph[node]:
            dfs(neighbour, visited)

dfs(1, set())
