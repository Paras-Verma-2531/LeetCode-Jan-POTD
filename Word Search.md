# April-3
##  79. Word Search
```java
class Solution {
    private boolean isPossible(char[][] ch, String word, StringBuilder str, int i, int j) {
    if (word.equals(str.toString())) return true;
    if (i < 0 || i >= ch.length || j < 0 || j >= ch[0].length) return false;
    char temp = ch[i][j];
    if (temp == '#' || temp != word.charAt(str.length())) return false;
    str.append(temp);
    ch[i][j] = '#'; // Mark the cell as visited
    boolean hor = isPossible(ch, word, str, i, j + 1) || isPossible(ch, word, str, i, j - 1);
    boolean vert = isPossible(ch, word, str, i + 1, j) || isPossible(ch, word, str, i - 1, j);
    ch[i][j] = temp; // Restore the original value of the cell
    str.deleteCharAt(str.length() - 1);
    return hor || vert;
}
    public boolean exist(char[][] board, String word) 
    {
       int rows = board.length;
      int cols = board[0].length;

     for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            if (isPossible(board, word, new StringBuilder(""), i, j)) {
                return true;
            }
        }
     }

     return false;
    }
}
