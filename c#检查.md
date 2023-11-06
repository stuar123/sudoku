public class SudokuSolver  
{  
    private int[,] _grid;  
  
    public SudokuSolver(int[,] grid)  
    {  
        _grid = grid;  
    }  
  
    public bool CheckSudoku()  
    {  
        for (int i = 0; i < 9; i++)  
        {  
            for (int j = 0; j < 9; j++)  
            {  
                if (_grid[i, j] == 0)  
                    return CheckRow(i, j) && CheckColumn(i, j) && CheckBox(i, j);  
            }  
        }  
        return true;  
    }  
  
    private bool CheckRow(int row, int col)  
    {  
        for (int i = 0; i < 9; i++)  
        {  
            if (i != col && _grid[row, i] == _grid[row, col])  
                return false;  
        }  
        return true;  
    }  
  
    private bool CheckColumn(int row, int col)  
    {  
        for (int i = 0; i < 9; i++)  
        {  
            if (i != row && _grid[i, col] == _grid[row, col])  
                return false;  
        }  
        return true;  
    }  
  
    private bool CheckBox(int row, int col)  
    {  
        int startRow = row - row % 3;  
        int startCol = col - col % 3;  
        for (int i = startRow; i < startRow + 3; i++)  
        {  
            for (int j = startCol; j < startCol + 3; j++)  
            {  
                if (i != row && j != col && _grid[i, j] == _grid[row, col])  
                    return false;  
            }  
        }  
        return true;  
    }  
}
