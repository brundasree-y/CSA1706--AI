colors = ["Red", "Green", "Blue", "Yellow"]
N = 4
grid = [[-1] * N for _ in range(N)]

def solve(pos=0):
    if pos == N * N:
        return True

    r, c = divmod(pos, N)

    for color in range(4):
        valid = True

        for dr, dc in [(-1, 0), (1, 0),
                       (0, -1), (0, 1)]:
            nr, nc = r + dr, c + dc

            if 0 <= nr < N and 0 <= nc < N:
                if grid[nr][nc] == color:
                    valid = False
                    break

        if valid:
            grid[r][c] = color

            if solve(pos + 1):
                return True

            grid[r][c] = -1

    return False

if solve():
    for row in grid:
        print(" ".join(colors[x] for x in row))
