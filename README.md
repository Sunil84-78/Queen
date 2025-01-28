def is_safe(board, row, col, N):
    # Check the column
    for i in range(row):
        if board[i] == col or \
           board[i] - i == col - row or \
           board[i] + i == col + row:
            return False
    return True

def solve_n_queens(board, row, N):
    if row == N:  # All queens are placed
        return True

   for col in range(N):
        if is_safe(board, row, col, N):
            board[row] = col  # Place the queen
            if solve_n_queens(board, row + 1, N):
                return True
            board[row] = -1  # Backtrack
    return False

def print_solution(board, N):
    for i in range(N):
        row = ['Q' if x == board[i] else '.' for x in range(N)]
        print(' '.join(row))

def n_queens(N):
    board = [-1] * N  # Initialize the board
    if solve_n_queens(board, 0, N):
        print_solution(board, N)
    else:
        print("No solution exists")


