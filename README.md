# N-queens-problem
import java.util.*;

class Solution {
    public List<List<String>> solveNQueens(int n) {
        List<List<String>> result = new ArrayList<>();
        
        char[][] board = new char[n][n];
        for (int i = 0; i < n; i++) {
            Arrays.fill(board[i], '.');
        }
        
        Set<Integer> cols = new HashSet<>();
        Set<Integer> diag1 = new HashSet<>();  // row - col
        Set<Integer> diag2 = new HashSet<>();  // row + col
        
        backtrack(0, n, board, cols, diag1, diag2, result);
        
        return result;
    }
    
    private void backtrack(int row, int n, char[][] board,
                           Set<Integer> cols,
                           Set<Integer> diag1,
                           Set<Integer> diag2,
                           List<List<String>> result) {
        
        if (row == n) {
            List<String> solution = new ArrayList<>();
            for (int i = 0; i < n; i++) {
                solution.add(new String(board[i]));
            }
            result.add(solution);
            return;
        }
        
