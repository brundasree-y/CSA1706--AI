from collections import deque

def water_jug():
    start = (0, 0)
    queue = deque([(start, [])])
    visited = set()

    while queue:
        (a, b), path = queue.popleft()

        if (a, b) in visited:
            continue
        visited.add((a, b))

        path = path + [(a, b)]

        if a == 4:
            for state in path:
                print(state)
            return

        states = [
            (5, b),
            (a, 3),
            (0, b),
            (a, 0),
            (a - min(a, 3-b), b + min(a, 3-b)),
            (a + min(b, 5-a), b - min(b, 5-a))
        ]

        for state in states:
            if state not in visited:
                queue.append((state, path))

water_jug()
