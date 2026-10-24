def alphabeta(depth, index, is_max, values, alpha, beta):
    if depth == 3:
        return values[index]

    if is_max:
        best = float('-inf')

        for i in range(2):
            value = alphabeta(
                depth + 1, index * 2 + i,
                False, values, alpha, beta
            )
            best = max(best, value)
            alpha = max(alpha, best)

            if beta <= alpha:
                break

        return best

    else:
        best = float('inf')

        for i in range(2):
            value = alphabeta(
                depth + 1, index * 2 + i,
                True, values, alpha, beta
            )
            best = min(best, value)
            beta = min(beta, best)

            if beta <= alpha:
                break

        return best


values = [2, 3, 5, 9, 6, 1, 11, 5]

result = alphabeta(
    0, 0, True, values,
    float('-inf'), float('inf')
)

print("Best value:", result)
