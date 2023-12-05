find a path through a matrix from (0,0) to (n-1, n-1) and you can  go only where there is 1 and 0 is prohibited.

```C++
bool hasPathHelper(int **input, int n, int **solution, int x, int y)
{
    if (x == n - 1 && y == n - 1)
    {
        return true;
    }
    if (x < 0 || y < 0 || x >= n || y >= n || input[x][y] == 0 || solution[x][y] == 1)
    {
        return false;
    }
  
    solution[x][y] = 1; // mark he current loction
    
    if (hasPathHelper(input, n, solution, x - 1, y))
    {
        return true;
    }
    if (hasPathHelper(input, n, solution, x + 1, y))
    {
        return true;
    }
    if (hasPathHelper(input, n, solution, x, y - 1))
    {
        return true;
    }
    if (hasPathHelper(input, n, solution, x, y + 1))
    {
        return true;
    }
    solution[x][y] = 0; // if the path is not found on that, then set to 0.

    return false;       // none returned true, so no path available;
}

bool hasPath(int **arr, int n)
{
    int **solution = new int *[n];
    for (int i = 0; i < n; i++)
    {
        solution[i] = new int[n];
        for (int j = 0; j < n; j++)
        {
            solution[i][j] = 0;
        }
    }
    return hasPathHelper(arr, n, solution, 0, 0);
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
    cout << hasPath(arr, n) << endl;
    
    return 0;
}
```

