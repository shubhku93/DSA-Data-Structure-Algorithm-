# Array 
- Data structure is a structure of our code which store data and algorithms is method or operations performed on data.

### Array Syntex 
int (variable name) [size] ={num,num};
it store only same type of data.

### Loop in Array
```
int arr [5] = {2,4,6,2,8};
  int size = 5;
 for(int i=0; i<size; i++){
   cout<<arr[i]<<" "<<endl;
 }
```
## Sorting Algorithm 

1. Bubble Sort Algorithm 

#### Problem Statement: 
Given an array of N integers, write a program to implement the Bubble Sorting algorithm.
Find the smallest number in array 

- Example :-
- Input : N= 5, array [] ={3,2,5,1,4}
- Output : 1,2,3,4,5.
- Explain : 
##### Solution :-

###### Approach :

 The Algorithm steps are follow:

- First, we will select the range of the unsorted array using loop (say i=0) indicate range from 0 to n-1. Similarly (say i=1) start range from 1 to n-1.
- we will iterate each element and check if adjacent element smaller than swap them.

- Dry Run :
Iteration 1 : 


```
// Bubble Sort
void bubblesort(vector<int> &v){
  int n= v.size();
    // Outer loop to iterate each element
  for(int i=0; i<n; i++){
      // Inner Loop compare each with adjacent element 
    for(int j=0; j<n; j++){
    // Check if adjacent element is smaller than swap them.
      if(v[j]>v[j+1])
        swap(v[j],v[j+1]);
    }
  }
  for(int i=0; i<n; i++){
    cout<<v[i];
  }
}
```
2. Selection Sort Algorithm 

```
void select (vector<int> &v,int n){
    for(int i=0; i<n; i++){
       // Assign ith element as smallest in min
        int min=i;
        for(int j=i+1; j<n; j++){
            // check if jth element is smaller than min assign jth index to min
           if(v[j]<v[min]){
               min=j;
           }   
            }
        // Then Swap ith element with min index.
        swap(v[i],v[min]);
            }
    for(int i: v){
        cout<< i;
    }
    }
```
3. Insertion Sort Algorithm 

```
void insert(vector<int> &v,int n){
    // Loop start from second element 
    for(int i=1; i<n; i++){
        // Store the current element as curr
        int curr= v[i];
        // take first element as sorted array 
        int prev= i-1;
        // Check if prev is greter or equal to 0 and compare prev element is greater than curr then swift the prev element to next position until prev is less than curr or prev is less than 0
        while(prev>=0 && v[prev]>curr){
            v[prev+1]= v[prev];
            prev--;
        }
        // Insert the curr element at the correct position.
        v[prev+1]= curr;
    }
    for(int i: v) cout<<i<<" ";
}

```
4. Quick Sort Algorithm 
```
int partition(vector<int> &v, int st, int end) {
    // This function takes last element as pivot and places the pivot element at its correct position in sorted array, and places all smaller to the left of pivot and all greater element to the right of pivot
    int pivot = v[end];
    int i = st - 1;//Index of the smaller element 
    // Traverse through all elements 
    for (int j = st; j < end; j++) {
       // If element smaller than pivot is found, swap it with 
        if (v[j] <= pivot) {
            i++;
            swap(v[i], v[j]);
        }
    }
    swap(v[i + 1], v[end]);
    return i + 1;
}

void quicksort(vector<int> &v, int st, int end) {
    if (st < end) {
        int part = partition (v, st, end);
        quicksort(v, st, part - 1);
        quicksort(v, part + 1, end);
    }
}

```
5. Merge Sort Algorithm 
```
void merge(vector<int> &v, int st, int mid, int end) {
    vector<int> temp;
    int left = st, right = mid + 1;
    
    while (left <= mid && right <= end) {
        if (v[left] <= v[right]) {
            temp.push_back(v[left++]);
        } else {
         temp.push_back(v[right++]);
        }
    }
    
    while (left <= mid) {
        temp.push_back(v[left++]);
while (right <= end) {
        temp.push_back(v[right++]);
    }
    
    for (int i = 0; i < temp.size(); i++) {
        v[st + i] = temp[i];
    }
}

void mergesort(vector<int> &v, int st, int end) {
    if (st >= end) return;
    
    int mid = st + (end - st) / 2;
    mergesort(v, st, mid);
    mergesort(v, mid + 1, end);
    merge(v, st, mid, end);
}
```
```
#include <iostream>
using namespace std;
int main(){
  int arr [5] = {-145,4,6,2,8};
  int size = 5;
  int smallest=arr[0];
 for(int i=0; i<size; i++){
   if(arr[i]<smallest){
     smallest= arr[i];
   }
   //second way to find small number 
  // smallest=min(smallest,arr[i]);
   
 }
  cout<<smallest;
  return 0;
}
```
<details>
  <summary><h3> Easy Problem</h3></summary>
  
<div>
  <details>
    <summary> <h4> Largest Element in a Array </h4></summary>
    
<h5>Problem Statement: </h5> Given an array you have to find the largest element in the array 
    
<details>
 <summary> Examples</summary>
  <h5>Example 1:</h5>
Input: arr[] = {2,5,1,3,0};
Output: 5
Explanation: 5 is the largest element in the array. 
<br>
<h5>Example2:</h5>
Input: arr[] = {8,10,5,7,9};
Output: 10
Explanation: 10 is the largest element in the array. 
    </details>
    
<details> <summary>Brute Force Approach </summary>
  
  <details> 
    <summary> Approach</summary>
    Solution1: Sorting
<h3> Intuition:</h3>
We can sort the array in ascending order, hence the largest element will be at the last index of the array. 

<h3>Approach: </h3>
Sort the array in ascending order.
Print the (size of the array -1)th index.
DryRun: 
Before sorting: arr[] = {2,5,1,3,0};

After sorting: arr[] = {0,1,2,3,5};

Hence answer : arr[sizeofthearray-1] =5
  </details>
  
<details>
<summary>Code</summary>
  <code>
    
  </code>
</details>
  
  <details>
  <summary>Complexity Analysis</summary>
    Time Complexity: O(N*log(N))

Space Complexity: O(n)
  </details>
  </details>
  
   <details>
    <summary> Recursive Approach</summary>
    
  <details>
      <summary> Approach/Institution</summary>
  </details>
      
  <details>
   <summary> Code</summary>
  </details>

  <details>
  <summary> Complexity Analysis</summary>
  </details>
  </details>
  </div>
</details>
#### Reverse the original array by 2 pointer Algorithm:

```
int main(){
  int arr[] = {1,2,3,4,5,6,7};
 int sz =7;
  int start=0,end= 6;
  while(start<=end){
    swap(arr[start],arr[end]);
    start++;
    end--;
  }
  for(int i=0;i<sz;i++){
    cout<<arr[i]<<" ";
  }
  return 0;
}
```
### Linear search Algorithm Questions : Given a array with a target we have to search that target in the array.

### Find the largest and second largest element.

```
// Find the Largest element and second largest element 
void le(int arr[]){
  // Initialise the largest element and second largest element as int min
  int maxi=INT_MIN;
  int smaxi=INT_MIN;
  // Loop for finding the largest element
  for(int i=0; i<5; i++){
    if(arr[i]>maxi){
      maxi=arr[i];
    }
  }
  //Loop for finding the second largest element. I think we can use the same loop for finding the second largest element but we can't use because largest element is not calculated.
  for(int i=0; i<5; i++){
    if(arr[i]>smaxi && arr[i]!=maxi){
     smaxi=arr[i];
    }
  }
  cout<<maxi<<endl;
  cout<<smaxi;
}
int main(){
  int arr[5]={12, 35, 1, 10, 3};
  le(arr);
  return 0;
}

```
