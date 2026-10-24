def minimax(node, is_max): if not isinstance(node, list): return node

values = [minimax(child, not is_max) for child in node]

if is_max: return max(values) else: return min(values) tree = [ [[2, 3], [5, 9]], [[0, 1], [7, 5]] ]

result = minimax(tree, True)

print("Minimax value:", result)
