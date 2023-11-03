from collections import deque
initial_state = (3, 3, 1)
goal_state = (0, 0, 0)
max_missionaries = 3
max_cannibals = 3
def is_valid_state(state):
    missionaries_left, cannibals_left, boat = state
    missionaries_right = max_missionaries - missionaries_left
    cannibals_right = max_cannibals - cannibals_left
    if (missionaries_left < cannibals_left and missionaries_left > 0) or \
       (missionaries_right < cannibals_right and missionaries_right > 0):
        return False
    return True
def generate_next_states(state):
    next_states = []
    missionaries_left, cannibals_left, boat = state
    boat = 1 - boat 
    for m in range(3):
        for c in range(3):
            if 1 <= m + c <= 2:  
                new_state = (missionaries_left - m, cannibals_left - c, boat)
                if is_valid_state(new_state):
                    next_states.append(new_state)
    return next_states
def bfs_search():
    visited = set()
    queue = deque()
    queue.append((initial_state, []))
    while queue:
        current_state, path = queue.popleft()
        if current_state == goal_state:
            return path
        if current_state not in visited:
            visited.add(current_state)
            for next_state in generate_next_states(current_state):
                queue.append((next_state, path + [current_state]))
    return None
solution_path = bfs_search()
if solution_path:
    print("Solution path:")
    for i, state in enumerate(solution_path):
        print(f"Step {i+1}: {state}")
else:
    print("No solution found.")
