from collections import deque

def water_jug():
    start = (12, 0, 0)
    target = (6, 6, 0)
    capacities = (12, 8, 5)

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
                        capacities[j] - state[j]
                    )

                    if amount > 0:
                        new_state = list(state)
                        new_state[i] -= amount
                        new_state[j] += amount
                        new_state = tuple(new_state)

                        if new_state not in visited:
                            visited.add(new_state)
                            queue.append(
                                (new_state, path + [new_state])
                            )

water_jug()
