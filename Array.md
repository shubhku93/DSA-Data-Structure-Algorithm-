# Array 
- Data structure is a structure of our code which store data and algorithms is method or operations performed on data.
- Array is a Data Structure that store different data types but only 1 at a time.It store data in linear form

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
<!--Easy Problem of Array-->
<summary><h3> Easy Problem</h3></summary>
<!-- Find Largest Element-->  
<div><details>
<summary> <h4> Largest Element in a Array </h4></summary>
<h5>Problem Statement: </h5> Given an array you have to find the largest element in the array
<!--Examples-->
<details>
<summary> Examples</summary>
<h5>Example 1:</h5>
Input: arr[] = {2,5,1,3,0};
Output: 5
Explanation: 5 is the largest element in the array. 
  
<h5>Example2:</h5>
Input: arr[] = {8,10,5,7,9};
Output: 10
Explanation: 10 is the largest element in the array.</details>
 <!--Brute Force Approach-->  
<details> <summary>Brute Force Approach </summary>
<!--Approach-->
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
<!--Code-->  
<details>
<summary>Code</summary>
  <code>
    
  </code>
</details>
<!--Complexity Analysis-->
<details>
<summary>Complexity Analysis</summary>
Time Complexity: O(N*log(N))
Space Complexity: O(n)
  </details>
  </details>
  
   <details>
    <summary> Optimise Approach</summary>
    
  <details>
      <summary> Approach/Institution</summary>
    Solution2:Using a max variable
<h3>Intuition: </h3>
We can maintain a max variable that will update whenever the current value is greater than the value in the max variable.  

<h3>Approach:</h3>
Create a max variable and initialize it with arr[0].
Use a for loop and compare it with other elements of the array
If any element is greater than the max value, update max value with the element’s value
Print the max variable.
  </details>
      
  <details>
   <summary> Code</summary>
    <code>
      
    </code>
  </details>

  <details>
  <summary> Complexity Analysis</summary>
    Time Complexity: O(N)

Space Complexity: O(1)
  </details>
  </details>
  </div>
<!-- Second Largest element-->
<div>
  <details>
    <summary>Second Largest Element in a Array without Sorting</summary>
    <h5> Problem Statement: </h5>Given an array, find the second smallest and second largest element in the array. Print ‘-1’ in the event that either of them doesn’t exist.  
    <detail>
      <summary>Examples</summary>
      <h5> Example 1: </h5>
      Input: [1,2,4,7,7,5]
      Output: Second Smallest=2
       Second Largest=5
      Explaination: Element are as follow 1,2,4,5,7,7 and hence the second Largest element of these is 5 and the second Smallest is 2.
    </detail>
    <detail>
      <summary>Brute Force Approach</summary>
      
</div>

<!--Array is sorted or not-->
<div>
<details>
    <summary><h3>Array is sorted or not</h3> </summary>
  
<!--Exlample-->
<details>
    <summary><h5>Examples</h5></summary>
</details>
    
<!--Brute Force Approach-->
<details>
<summary>Brute Force Approach</summary>
  
<!--Approach-->
<details>
<summary>Approach/Intuition</summary>
</details>

<!--Dry Run-->
  <details>
  <summary>Dry Run</summary>
  </details>
  
<!--Code-->
<details>
  <summary>Code</summary>
</details>

<!--Complexity Analysis --><details>
  <summary> Complexity Analysis</summary>
</details>
</details>

<!--Optimise Approach -->
<details>
<summary>Optimization</summary>
  
<!--Approach/Institution--><details>
<summary> Approach/Institution</summary>
 </details>

<!--Dry Run-->
<details>
<summary>
Dry Run</summary>
</details>

<!--Code-->
<details>
  <summary>Code </summary>
</details>

<!--Complexity Analysis-->
<details>
  <summary> Complexity Analysis</summary>
</details>
</details>

<!--Find the largest and second largest element in a array-->
<details>
<summary>
  <h4> Find the largest and second largest element </h4>
</summary>
</details>

<!--Examples-->
<details>
  <summary>Examples</summary>
</details>

<!--Brute Force Approach-->
<details>
<summary>Brute Force Approach</summary>
  
<!--Approach-->
<details>
<summary>Approach/Intuition</summary>
</details>

<!--Dry Run-->
  <details>
  <summary>Dry Run</summary>
  </details>
  
<!--Code-->
<details>
  <summary>Code</summary>
</details>

<!--Complexity Analysis --><details>
  <summary> Complexity Analysis</summary>
</details>
</details>
</div>
</details>

## Midium Problem

### 1. 2Sum Problem
### Two Sum : Check if a pair with given sum exists in Array

#### Problem Statement: Given an array of integers arr[] and an integer target.

1st variant: Return YES if there exist two numbers such that their sum is equal to the target. Otherwise, return NO.

2nd variant: Return indices of the two numbers such that their sum is equal to the target. Otherwise, we will return {-1, -1}.

Note: You are not allowed to use the same element twice. Example: If the target is equal to 6 and num[1] = 3, then nums[1] + nums[1] = target is not a solution.

Examples:

Example 1:
Input Format: N = 5, arr[] = {2,6,5,8,11}, target = 14
Result: YES (for 1st variant)
       [1, 3] (for 2nd variant)
Explanation: arr[1] + arr[3] = 14. So, the answer is “YES” for the first variant and [1, 3] for 2nd variant.

Example 2:
Input Format: N = 5, arr[] = {2,6,5,8,11}, target = 15
Result: NO (for 1st variant)
	[-1, -1] (for 2nd variant)
Explanation: There exist no such two numbers whose sum is equal to the target.

#### Brute Force Approach

##### Approach (variant 1)
- We will run a loop(say i) to select each element from 0 to n-1.
- Initialise Sum with a value 0.
- Now we will run another loop(say j) from i+1 to n-1.
- if the sum of arr[i]+arr[j] equal to target.
- return yes
  
#### Dry Run
Given array, nums = [2,1,3,4], target = 4
i=0: sum=3,5,6
i=1: sum=4,5
i=2: sum=7
#### Code
```
#include <bits/stdc++.h>
using namespace std;
string f(vector<int> &v,int k){
  for(int i=0; i<v.size(); i++){
   int sum= 0;
    for(int j=i+1; j<v.size(); j++){
      sum= v[i]+v[j];
      if(sum==k) return "yes";
    }  
  }
  return "no";
} 
int main(){

  vector<int> arr1 = {2,6,5,8,11};
  vector<int> arr2 = {2, 3, 4, 4, 5, 11, 12};
  cout<<f(arr1,8);

  return 0;
}
```
#### Complexity Analysis
- Time Complexity : O(n²)
- Space Complexity : O(1)
  
#### Approach (variant 2)
-We will run a loop(say i) to select each element from 0 to n-1.
- Initialise Sum with a value 0.
- Now we will run another loop(say j) from i+1 to n-1.
- if the sum of arr[i]+arr[j] equal to target.

#### Code
```
#include <bits/stdc++.h>
using namespace std;
vector<int> f(vector<int>&v,int k){
  int n=v.size();
  vector<int> ans;
  for(int i=0; i<n; i++){
    int sum=0;
    for(int j=i+1; j<n; j++){
      sum= v[i]+v[j];
      if(sum==k){
       ans.push_back(i);
        ans.push_back(j);
        return ans;
      }
    }
  }
  return {-1,-1};
}
int main(){
  vector<int> v={2,1,3,4};
vector<int> ans=f(v,4);
  for(int i:ans)
    cout<<i;
  return 0;
}
```

#### Complexity Analysis
Time Complexity: O(n²)
Space Complexity: O(n)

#### Better Approach (using Hashing)

#### Approach (variant 1)
- First we will initialise map of int type.
- Now we will run a loop(say i) from 0 to n-1.
- inside the loop we will store current element in variable.
- Subtract the current sum with target.
- if that sum exists in map return yes
- Otherwise no

#### Dry Run
Given array, nums = [2,1,3,4], target = 4
i=0: sum= 4-2: mpp: empty
i=1; sum= 4-1: mpp; 3,

#### Code
```
#include <bits/stdc++.h>
using namespace std;
string f(vector<int>&v,int k){
  int n=v.size();
  map<int,int> mpp;
  for(int i=0; i<n; i++){
    int num= v[i];
    int sum= k-num;
    if(mpp.find(sum)!=mpp.end()){
      return "yes";
    }
    mpp[num]= i;
  }
  return "no";
}
int main(){
  vector<int> v={2,1,3,4};
cout<< f(v,4);
  
  return 0;
}
```

#### Approach (variant 2)
- we will initialise hashMap of int and int.
- We run a loop from 0 to n-1
- In this we will take current element into a  variable num.
- From the target we will subtract num to get rest part of element
- if the rest part exists return yes or 

```
#include <bits/stdc++.h>
using namespace std;
vector <int> f(vector<int>&v,int k){
  int n=v.size();
  map<int,int> mpp;
  for(int i=0; i<n; i++){
    int num= v[i];
    int sum= k-num;
    if(mpp.find(sum)!=mpp.end()){
      return {mpp[sum],i};
      
    }
    mpp[num]= i;
  }
  return {-1,-1};
}
int main(){
  vector<int> v={2,1,3,4};
vector<int>ans=f(v,4);
  for(int i:ans)
    cout<<i;
  return 0;
}
```
#### Complexity Analysis 

### 2.Sort 0s,1s and 2s
### Sort an array of 0s, 1s and 2s

### Problem Statement: Given an array consisting of only 0s, 1s, and 2s. Write a program to in-place sort the array without using inbuilt sort functions. ( Expected: Single pass-O(N) and constant space)

Examples
Input: nums = [2,0,2,1,1,0]
Output: [0,0,1,1,2,2]

Input: nums = [2,0,1]
Output: [0,1,2]

Input: nums = [0]
Output: [0]

#### Brute Force Approach 

#### Approach 
- First initialise three variables cnt0, cnt1 and cnt2.
- we will run a loop to select the element from 0 to n-1
- check if current element is 1 increase cnt1 by 1.Else If  current element is 0 increase cnt0 by 1 and if current element is 2 increase by 1.
- We will run another loop sort the array
- Now first loop start from 0 to cnt0 put 0 to arr[i].
- second loop start from cnt0 to cnt0+cnt1 in which we put 1 till last.
- Third loop start from cnt0+cnt1 to n-1 in which we put 2 to arr[i].

#### Dry Run
given arr[]= {2,0,2,1,1,0};
i= 0:cnt0=0,cnt1=0,cnt2=1;
i= 1:cnt0=1,cnt1=0,cnt2=1;
i= 2:cnt0=1,cnt1=0,cnt2=2;
i= 3:cnt0=1,cnt1=1,cnt2=2;
i= 4:cnt0=1,cnt1=2,cnt2=2;
i= 5:cnt0=2,cnt1=2,cnt2=2;
then,
from 0 to cnt0
i=0:arr[]={0};
i=1:arr[]={0,0};

from cnt0 to cnt0+cnt1
i=2:arr[]={0,0,1};
i=3:arr[]={0,0,1,1};

from cnt0+cnt1 to n
i=4:arr[]={0,0,1,1,2};
i=5:arr[]={0,0,1,1,2,2};

#### Code
```
#include <bits/stdc++.h>
using namespace std;

void f(vector<int> &v) {
    int n = v.size();
    // Initialise three counts for 0, 1, and 2.
    int cnt0 = 0, cnt1 = 0, cnt2 = 0;
    for (int i = 0; i < n; i++) {
        // Count the occurrences of 0s, 1s, and 2s
        if (v[i] == 0) cnt0++;
        else if (v[i] == 1) cnt1++;
        else if (v[i] == 2) cnt2++;
    }
    // Now Arrange them in array 
    for (int i = 0; i < cnt0; i++) {
        v[i] = 0;
    }
    for (int i = cnt0; i < cnt0 + cnt1; i++) {
        v[i] = 1;
    }
    for (int i = cnt0 + cnt1; i < cnt0 + cnt1 + cnt2; i++) {
        v[i] = 2;
    }
}

int main() {
    vector<int> arr = {2, 0, 2, 1, 1, 0};
    f(arr);
    for (int i : arr) {
        cout << i;
    }
    return 0;
}
```
#### Optimize Approach 
### Approach 
- First initialise three pointer left and mid with a value 0 and high with n-1.
- Now run while loop until mid is less high.
- Check if mid is equal to 0 then first swap arr of [low] to arr of [mid] and increases by 1.If mid is equal to 1;

#### Reverse the original array by 2 pointer Algorithm:

```
int main(){
  int arr[] = {1,2,3,4,5,6,7};
 int sz =
7;
  int start=0,end= 6;
  while(start<=end){
    swap(arr[start],arr[end]);
    start++;
    end--;
  }
  for(int i=0;i<sz;i++){
    cout<<arr[i]<<" ";
  }
  return 0;l
}
```
### Linear search Algorithm Questions : Given a array with a target we have to search that target in the array.

.

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
