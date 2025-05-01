# Recursion 
### Merge Sort
- Merge Sort is a sorting Algorithm which TC is O(n logn) and Sc is O(n).
#### Approach 
- In Recursion merge sort Approach is to break the array in single element and then merge them by sorting.
```
void merge(int arr[],int low,int mid,int high){
  
  int left=low;
  int right=mid+1;
 vector<int> temp;
  // While element in left is less than mid and right is less than high
  while(left<=mid && right<=high){
    
    if(arr[left]<=arr[right]){
      temp.push_back(arr[left]);
      left++;
    }
    else{
      temp.push_back(arr[right]);
      right++;
    }
  }
    // If still elements are left on left side.
    while(left<=mid){
      temp.push_back(arr[left]);
      left++;
    }
     // If still elements are left on right side.
     while(right<=high){
      temp.push_back(arr[right]);
      right++;
    }
  
  //copying the elements from temp to arr.
  for(int i=low;i<=high; i++){
    arr[i]=temp[i-low];
  }
}
void ms(int arr[],int low,int high){
 // Base Case
  if(low==high) return;
  // Divide the array into two parts
  int mid=low+(high-low)/2;
  // Recursion Call on left side
  ms(arr,low,mid);
  // Recursion Call on Right side
  ms(arr,mid+1,high);
  // Merge the two parts in sorted order
  merge(arr,low,mid,high);
  
}
int main(){
  int arr[]={6,4,3,7,8,1,5,2};
  int low=0,high=7;
  cout<<"The sorted array is: ";
  ms(arr,low,high);
  for(int i=0;i<8;i++){
    cout<<arr[i]<<" ";
  }
  cout<<endl;
  return 0;
}
```
### Quick Sort
#### Approach 
```
// partition the array around the pivot element
int partition(vector<int> &arr,int low,int high){
  int pivot=arr[low];
  int i=low,j=high;
  while (i<j){
    while(arr[i]<=pivot && i<high){
    i++;
    }
    while(arr[j]>pivot && j>low){
    j--;
    }
    if(i<j){
      swap(arr[i],arr[j]);
    }
  }
  swap(arr[low],arr[j]);
  return j;
}
void quicksort(vector<int> &arr,int low,int high){
  if(low<high){
    int pindex=partition(arr,low,high);
    quicksort(arr,low,pindex-1);
    quicksort(arr,pindex+1,high);
  }
}
int main(){
  vector<int> arr={4,6,3,1,2,5};
  quicksort(arr,0,arr.size()-1);
  for(int i:arr){
    cout<<i<<" ";
  }
  return 0;
}
```
### N Queen 
#### Approach 
```
void solve(int col, vector<string> &board, vector<vector<string>> &ans, vector<int> &leftRow, vector<int> &upperDiagonal, vector<int> &lowerDiagonal,int n){
  // Base Case
  if(col==n){
    ans.push_back(board);
  }
  // Recursion Case
  for(int row=0; row<n; row++){
    // Check if we can place the queen
    if(leftRow[row]==0 && upperDiagonal[n-1+col-row]==0 && lowerDiagonal[col]==0){
      board[row][col]='Q';
      leftRow[row]=1;
      lowerDiagonal[col]=1;
      upperDiagonal[n-1+col-row]=1;
      solve(col+1,board,ans,leftRow,lowerDiagonal,upperDiagonal,n);
      // Backtracking 
      board[row][col]='.';
      leftRow[row]=0;
      lowerDiagonal[col]=0;
      upperDiagonal[n-1+col-row]=0;
      
    }
  }
}
vector<vector<string>> solveNQueens(int n){
  // Declaration 
  vector<string> board(n);
  string s(n,'.');
  for(int i=0; i<n; i++){
    board[i]=s;
  }
  vector<vector<string>>ans; vector<int>leftRow(n,0),lowerDiagonal(2*n-1,0),upperDiagonal(2*n-1,0);
  // Function Call
solve(0,board,ans,leftRow,lowerDiagonal,upperDiagonal,n);
  return ans;
}
int main(){
  int n =4;
vector<vector<string>>ans=solveNQueens(n);
  cout<<endl;
  for(int i=0; i<ans.size(); i++){
    cout<<"Arrangement "<<i+1<<endl;
    for(auto j:ans[i]){
      cout<<j<<endl;
    }
    cout<<endl;
  } 
  return 0;
}
```
### Sudoku Solver Problem 
- 
#### Approach 
```
bool isSafe(vector<vector<char>>& board, int row, int col, char num) {
    // Horizontal Case
    for(int i = 0; i < 9; i++) {
        if(board[row][i] == num) return false;
    }
    
    // Vertical Case
    for(int i = 0; i < 9; i++) {
        if(board[i][col] == num) return false;
    }
    
    // Grid Cases
    int r = (row/3) * 3;
    int c = (col/3) * 3;
    for(int i = r; i < r+3; i++) {
        for(int j = c; j < c+3; j++) {
            if(board[i][j] == num) return false;
        }
    }
    return true;
}

bool solve(vector<vector<char>>& board) {
    for(int row = 0; row < 9; row++) {
        for(int col = 0; col < 9; col++) {
            if(board[row][col] == '.') {
                for(char num = '1'; num <= '9'; num++) {
                    if(isSafe(board, row, col, num)) {
                        board[row][col] = num;
                        if(solve(board)) return true;
                        board[row][col] = '.';
                    }
                }
                return false;
            }
        }
    }
    return true;
}

int main() {
    vector<vector<char>> board = {
        {'5','3','.','.','7','.','.','.','.'},
        {'6','.','.','1','9','5','.','.','.'},
        {'.','9','8','.','.','.','.','6','.'},
        {'8','.','.','.','6','.','.','.','3'},
        {'4','.','.','8','.','3','.','.','1'},
        {'7','.','.','.','2','.','.','.','6'},
        {'.','6','.','.','.','.','2','8','.'},
        {'.','.','.','4','1','9','.','.','5'},
        {'.','.','.','.','8','.','.','7','9'}
    };
    
    cout << "Original Sudoku:" << endl;
    for(auto& row : board) {
        for(char cell : row) cout << cell << " ";
        cout << endl;
    }
    
    if(solve(board)) {
        cout << "\nSolved Sudoku:" << endl;
        for(auto& row : board) {
            for(char cell : row) cout << cell << " ";
            cout << endl;
        }
    } else {
        cout << "\nNo solution exists" << endl;
    }
    
    return 0;
}

```
### Rat in a Maze
#### Approach 
```
void solve(vector<vector<int>> &maze, int r, int c, string &path, vector<string> &ans) {
    int n = maze.size();
    // Base Case
    if (r < 0 || c < 0 || r >= n || c >= n || maze[r][c] == 0 || maze[r][c] == -1) 
        return;
    // Ans Case
    if (r == n-1 && c == n-1) {
        ans.push_back(path);
        return;
    }
    // Recursive Case
    maze[r][c] = -1; // Mark visited
    
    // Down
    path.push_back('D');
    solve(maze, r+1, c, path, ans);
    path.pop_back();
    
    // Left
    path.push_back('L');
    solve(maze, r, c-1, path, ans);
    path.pop_back();
    
    // Right
    path.push_back('R');
    solve(maze, r, c+1, path, ans);
    path.pop_back();
    
    // Up
    path.push_back('U');
    solve(maze, r-1, c, path, ans);
    path.pop_back();
    
    maze[r][c] = 1; // Backtrack
}

vector<string> findPath(vector<vector<int>> &maze) {
    string path = "";
    vector<string> ans;
    solve(maze, 0, 0, path, ans);
    sort(ans.begin(), ans.end());
    return ans;
}

int main() {
    vector<vector<int>> maze = {
        {1, 0, 0, 0},
        {1, 1, 0, 1},
        {1, 1, 0, 0},
        {0, 1, 1, 1}
    };
    
    vector<string> paths = findPath(maze);
    
    if (paths.empty()) {
        cout << "No path exists!" << endl;
    } else {
        cout << "All possible paths:" << endl;
        for (const string &path : paths) {
            cout << path << endl;
        }
    }
    
    return 0;
}

```