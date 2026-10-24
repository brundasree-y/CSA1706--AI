colors = ["Red", "Green", "Blue", "Yellow"]

graph = {
    'A': ['B', 'D'],
    'B': ['A', 'C', 'E'],
    'C': ['B', 'F'],
    'D': ['A', 'E', 'G'],
    'E': ['B', 'D', 'F', 'H'],
    'F': ['C', 'E', 'I'],
    'G': ['D', 'H'],
    'H': ['E', 'G', 'I'],
    'I': ['F', 'H']
}

color = {}

def map_coloring(node):
    if node == len(graph):
        return True

    region = list(graph.keys())[node]

    for c in colors:
        if all(color.get(n) != c for n in graph[region]):
            color[region] = c

            if map_coloring(node + 1):
                return True

            del color[region]

    return False

if map_coloring(0):
    for region, c in color.items():
        print(region, ":", c)
else:
    print("No solution")
