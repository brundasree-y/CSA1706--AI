from collections import deque

def water_jug():
    start = (0, 0, 8)
    target = (0, 4, 4)
    capacity = (3, 5, 8)

    queue = deque([(start, [start])])
    visited = {start}

    while queue:
        state, path = queue.popleft()

        if state == target:
            for step in path:
                print(step)
            return

        for i in range(3):
            for j in range(3):
                if i != j:
                    amount = min(
                        state[i],
                        capacity[j] - state[j]
                    )

                    if amount > 0:
                        new = list(state)
                        new[i] -= amount
                        new[j] += amount
                        new = tuple(new)

                        if new not in visited:
                            visited.add(new)
                            queue.append((new, path + [new]))

water_jug()
