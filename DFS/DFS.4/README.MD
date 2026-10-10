graph = {
    1: [2, 3],
    2: [5, 6],
    3: [4, 7],
    4: [8],
    5: [],
    6: [],
    7: [8],
    8: []
}

def dfs(node, visited):
    if node not in visited:
        print(node, end=" ")
        visited.add(node)

        for neighbour in graph[node]:
            dfs(neighbour, visited)

dfs(1, set())
