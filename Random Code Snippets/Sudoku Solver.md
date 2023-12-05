```C++
#include <bits/stdc++.h>
using namespace std;

bool isSafe(int row, int col, int **board, int value, int n)
{
    for (int i = 0; i < n; i++)
    {
        // row check
        if (board[row][i] == value || board[i][col] == value)
            return false;
        // 3x3 matrix check
        if (board[3 * (row / 3) + i / 3][3 * (col / 3) + i % 3] == value)
            return false;
    }
    return true;
}

bool solve(int **board)
{
    int n = board.size();

    for (int row = 0; row < n; row++)
    {
        for (int col = 0; col < n; col++)
        {
	        // empty or not???
            if (board[row][col] == 0)
            {
                for (int val = 1; val <= 9; val++)
                {
                    if (isSafe(row, col, board, val, n))
                    {
                        board[row][col] = val;
                        // recursive call
                        bool rest = solve(board);
                        if (rest)
                        {
                            return true;
                        }
                        else
                        {
                            // backtrack
                            board[row][col] = 0;
                        }
                    }
                }
                return false;
            }
        }
    }
    return true;
}

int main()
{
    int **arr;
    int n;
    cin >> n;
    arr = new int *[n];
    for (int i = 0; i < n; i++)
    {
        arr[i] = new int[n];
        for (int j = 0; j < n; j++)
        {
            cin >> arr[i][j];
        }
    }
    cout << solve(arr) << endl;

    return 0;
}
```

