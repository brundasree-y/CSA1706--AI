graph = {
    1: [2, 7],
    2: [3, 6],
    3: [4, 5],
    4: [],
    5: [],
    6: [],
    7: [8, 10],
    8: [9],
    9: [],
    10: []
}

def dfs(node, visited):
    if node not in visited:
        print(node, end=" ")
        visited.add(node)

        for neighbour in graph[node]:
            dfs(neighbour, visited)

dfs(1, set())
