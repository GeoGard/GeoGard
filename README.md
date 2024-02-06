- 👋 Hi, I’m @GeoGard

<!---
GeoGard/GeoGard is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->


class TicTacToe:
    def __init__(self) -> None:
        self.player = 'X'
        self.board = [
            ['-', '-', '-'],
            ['-', '-', '-'],
            ['-', '-', '-']
        ]

    def display_board(self):
        for i in range(3):
            for j in range(3):
                print(self.board[i][j], end=' ')
            print()

    def play(self, row, col):
        if row < 0 or row > 2 or col < 0 or col > 2:
            print("Wrong row or col")
        elif self.board[row][col] == '-':
            self.board[row][col] = self.player
            self.player = 'X' if self.player == 'O' else 'O'
        else:
            print("Error, position is occupied")

    def get_winner(self):
        for i in range(3):
            if self.board[i][0] == self.board[i][1] == self.board[i][2] != '-':
                return self.board[i][0]
            if self.board[0][i] == self.board[1][i] == self.board[2][i] != '-':
                return self.board[0][i]
        
        if self.board[0][0] == self.board[1][1] == self.board[2][2] != '-' or \
           self.board[0][2] == self.board[1][1] == self.board[2][0] != '-':
            return self.board[1][1]
        
        return None

    def is_tie(self):
        if all(self.board[row][col] != '-' for row in range(3) for col in range(3)):
            return self.get_winner() is None
        return False


game = TicTacToe()
while True:
    print(game.player, "plays")
    game.display_board()
    row = int(input("Row: "))
    col = int(input("Col: "))
    game.play(row, col)
    winner = game.get_winner()
    if winner is not None:
        print(winner, "wins")
        game.display_board()
        break
    if game.is_tie():
        print("It's a Tie")
        game.display_board()
        break
