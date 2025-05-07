# Tic-Toc-Toe
The Tic Tac Toe project in Core Java is a simple two-player game that demonstrates basic concepts of object-oriented
programming and control structures. It provides a console-based interface for players to take turns, check for winners, and display
the game board after each move.
# Program
```python
package TicTacToe;

import java.util.Scanner;

public class Main {
	private static char[][] c = new char[3][3];
	private static char user;
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner scan = new Scanner(System.in);
		gameBoard();
		user = 'X';
		int moves = 0;
		boolean gameWon = false;
		while(moves < 9 && !gameWon)
		{
			printBoard();
			System.out.printf("Player %c, enter your move(row & column): ",user);
			int row = scan.nextInt();
			int column = scan.nextInt();
			
			if(isValidMove(row, column))
			{
				c[row][column]=user;
				moves++;
				if(checkWin(row, column))
				{
					gameWon = true;
					printBoard();
					System.out.printf("Player %c Wins....!!%n",user);
				}
				else
				{
					user = (user=='X') ? 'O' : 'X';
				}
			}
			else
			{
				System.out.println("Invalid Move. Try again.!!!");
			}
		}
		if(!gameWon)
		{
			printBoard();
			System.out.println("Game Draw...!!!");
		}
		scan.close();

	}
	
	private static boolean checkWin(int row, int column) {
		// TODO Auto-generated method stub
		return checkRow(row) || checkColumn(column) || checkDiagonals();
	}

	private static boolean checkDiagonals() {
		// TODO Auto-generated method stub
		boolean diag1 = true , diag2 = true;
		for(int i=0;i<3;i++)
		{
			if(c[i][i] != user)
			{
				return false;
			}
			if(c[i][3-i-1] != user)
			{
				return false;
			}
		}
		return diag1 || diag2;
	}

	private static boolean checkColumn(int column) {
		// TODO Auto-generated method stub
		for(int row=0;row<3;row++)
		{
			if(c[row][column] != user)
			{
				return false;
			}
		}
		return true;
		
	}

	private static boolean checkRow(int row) {
		// TODO Auto-generated method stub
		for(int col=0;col<3;col++)
		{
			if(c[row][col] != user)
			{
				return false;
			}
		}
		return true;
	}

	private static boolean isValidMove(int row, int column) {
		// TODO Auto-generated method stub
		return (row>=0 && row<3) && (column>=0 && column<3) && c[row][column]=='_';
	}

	private static void gameBoard(int i1, int j1) {
		// TODO Auto-generated method stub
		for(int i=0;i<3;i++)
		{
			for(int j=0;j<3;j++)
			{
				c[i1][j1] = 'X';
			}
		}
	}

	public static void gameBoard()
	{
		for(int i=0;i<3;i++)
		{
			for(int j=0;j<3;j++)
			{
				c[i][j] = '_';
			}
		}
	}
	
	public static void printBoard()
	{
		for(int i=0;i<3;i++)
		{
			for(int j=0;j<3;j++)
			{
				System.out.print(c[i][j]+" "); 
			}
			System.out.println();
		}
	}

}

```
# Output
![Screenshot 2025-05-07 232252](https://github.com/user-attachments/assets/e7c6a65c-4b6f-4e67-bd01-47f88a533c7d)

