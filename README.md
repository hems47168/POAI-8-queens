# POAI-8-queens
def solve_queens(n):
    def can_place(board, row, col):
        for i in range(row):
            if board[i] == col or board[i] - i == col - row or board[i] + i == col + row:
                return False
        return True

    def place_queens(board, row):
        if row == n:
            result.append(board[:])
            return
        for col in range(n):
            if can_place(board, row, col):
                board[row] = col
                place_queens(board, row + 1)

    result = []
    place_queens([-1] * n, 0)
    return result

def print_board(board):
    n = len(board)
    for row in range(n):
        line = ""
        for col in range(n):
            if board[row] == col:
                line += "Q "
            else:
                line += ". "
        print(line)
    print()

def main():
    n = 8
    solutions = solve_queens(n)
    print(f"Total solutions: {len(solutions)}")
    for i, solution in enumerate(solutions):
        print(f"Solution {i + 1}:")
        print_board(solution)

if __name__ == "__main__":
    main()
