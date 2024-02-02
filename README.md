# Task3
    using System;

    class Program
    {
    static void Main()
    {
        PlaceQueens();
    }

    static void PlaceQueens()
    {
        int[,] chessboard = new int[8, 8];
        Random random = new Random();

        for (int i = 0; i < 2; i++)
        {
            int row, col;
            
            do
            {
                row = random.Next(8);
                col = random.Next(8);
            } while (!IsValid(chessboard, row, col));

            chessboard[row, col] = 1; 
            Console.WriteLine($"Queen {i + 1} placed at position: ({row + 1}, {col + 1})");
        }
        
        Console.WriteLine("\nChessboard:");
        for (int i = 0; i < 8; i++)
        {
            for (int j = 0; j < 8; j++)
            {
                Console.Write(chessboard[i, j] + " ");
            }
            Console.WriteLine();
        }
    }

    static bool IsValid(int[,] chessboard, int row, int col)
    {
        for (int i = 0; i < 8; i++)
        {
            if (chessboard[row, i] == 1 || chessboard[i, col] == 1)
                return false;
        }
        
        for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
        {
            if (chessboard[i, j] == 1)
                return false;
        }

        for (int i = row, j = col; i < 8 && j >= 0; i++, j--)
        {
            if (chessboard[i, j] == 1)
                return false;
        }

        return true;
    }
    }
