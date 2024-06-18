#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Function to generate a random number within a range
int random_number(int min, int max) {
    return rand() % (max - min + 1) + min;
}

// Function to display the game board
void display_board(int board[3][3]) {
    printf("-------------+\n");
    for (int i = 0; i < 3; i++) {
        printf("| %d | %d | %d |\n", board[i][0], board[i][1], board[i][2]);
        printf("-------------+\n");
    }
}

// Function to check if the game is over
int game_over(int board[3][3], int player) {
    // Check rows
    for (int i = 0; i < 3; i++) {
        if (board[i][0] == board[i][1] && board[i][1] == board[i][2] && board[i][0] != 0) {
            return player;
        }
    }

    // Check columns
    for (int i = 0; i < 3; i++) {
        if (board[0][i] == board[1][i] && board[1][i] == board[2][i] && board[0][i] != 0) {
            return player;
        }
    }

    // Check diagonals
    if (board[0][0] == board[1][1] && board[1][1] == board[2][2] && board[0][0] != 0) {
        return player;
    }
    if (board[0][2] == board[1][1] && board[1][1] == board[2][0] && board[0][2] != 0) {
        return player;
    }

    // Check if the board is full
    int count = 0;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if (board[i][j] != 0) {
                count++;
            }
        }
    }
    if (count == 9) {
        return 0; // Draw
    }

    return -1; // Game not over
}

int main() {
    // Initialize random seed
    srand(time(NULL));

    // Game variables
    int board[3][3] = {0};
    int player = 1; // 1 for Player 1, 2 for Player 2
    int row, col;

    // Start the game
    printf("Welcome to Tic-Tac-Toe!\n");
    printf("Player 1: X\n");
    printf("Player 2: O\n\n");

    while (1) {
        display_board(board);
        printf("Player %d's turn:\n", player);
        printf("Enter row (1-3): ");
        scanf("%d", &row);
        printf("Enter column (1-3): ");
        scanf("%d", &col);

        // Check if the entered position is valid
        if (row < 1 || row > 3 || col < 1 || col > 3 || board[row - 1][col - 1] != 0) {
            printf("Invalid move. Try again.\n");
            continue;
        }

        // Update the board
        board[row - 1][col - 1] = player;

        // Check if the game is over
        int result = game_over(board, player);
        if (result == 1) {
            display_board(board);
            printf("Player 1 wins!\n");
            break;
        } else if (result == 2) {
            display_board(board);
            printf("Player 2 wins!\n");
            break;
        } else if (result == 0) {
            display_board(board);
            printf("It's a draw!\n");
            break;
        }

        // Switch players
        player = (player == 1) ? 2 : 1;
    }

    return 0;
}
