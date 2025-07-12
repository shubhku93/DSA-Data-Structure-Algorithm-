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
### Reverse the original array by 2 pointer Algorithm:

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
- Check if mid is equal to 0 then first swap arr of [low] to arr of [mid] and increases by 1 left and right.If mid is equal to 1 increase mid by 1 and If mid equals to 2 then swap arr of [mid] to [high] and high will decrease by 1.

#### Code 
```
#include <bits/stdc++.h>
using namespace std;

void f(vector<int> &v) {
    int n = v.size();
    // Initialise 3 pointers
   int low=0,mid=0,high=n-1;
    // while mid is less than high
    while(mid<high){
        // Check and swap the the pointers
        if(v[mid]==0){
            swap(v[low],v[mid]);
            low++,mid++;
        }
        else if(v[mid]==1){
            mid++;
        }
        else {
            swap(v[mid],v[high]);
            high--;
        }
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
#### Dry Run
given arr[]={2,0,2,1,1,0};

i=0: low=0,mid=0,high=n-1 : arr={0,0,2,1,1,2}
i=1: low=0,mid=0,high=n-2: arr={0,0,2,1,1,2}
i=2: low=1,mid=0,high=n-2: arr={0,0,1,1,2,2}

#### Complexity Analysis 
Time Complexity: O(N), where N = size of the given array.
Reason: We are using a single loop that can run at most N times.

Space Complexity: O(1) as we are not using any extra space.

### 3. Majority Elements (n/2 times)
#### Find the Majority Element that occurs more than N/2 times

#### Problem Statement: Given an array of N integers, write a program to return an element that occurs more than N/2 times in the given array. You may consider that such an element always exists in the array.

Examples

Example 1:
Input Format: N = 3, nums[] = {3,2,3}
Result: 3
Explanation: When we just count the occurrences of each number and compare with half of the size of the array, you will get 3 for the above solution. 

Example 2:
Input Format:  N = 7, nums[] = {2,2,1,1,1,2,2}

Result: 2

Explanation: After counting the number of times each element appears and comparing it with half of array size, we get 2 as result.

Example 3:
Input Format:  N = 10, nums[] = {4,4,2,4,3,4,4,3,2,4}

Result: 4

#### Brute Force Approach 
#### Approach 
- First we will run a loop say(i) from 0 to n-1
- Initialise count will be 0
- Now run another loop from 0 to n-1
- Check if v[i] is equal to v[j] increase count by 1.
- After completing the loop Check if count is greater than n/2 if yes then return v[i] and if no then return -1.

  #### Dry Run

#### Code
```
#include <bits/stdc++.h>
using namespace std;

int f(vector<int> &v) {
    int n = v.size();
for(int i=0; i<n; i++){
    int cnt=0; 
    for(int j=0; j<n; j++){
        if(v[i]==v[j]){
            cnt++;
        }
    }
    if(cnt>n/2){
        return v[i];
    }
}
    return -1;
}

int main() {
    vector<int> arr = {2, 2, 1, 1, 1, 2,2};
    cout<<f(arr);
    
return 0;
}
```
#### Complexity Analysis 
Time Complexity: O(N2), where N = size of the given array. Reason: For every element of the array the inner loop runs for N times. And there are N elements in the array. So, the total time complexity is O(N2). Space Complexity: O(1) as we use no extra space.

#### Better Approach
#### Approach
- First initialise map
- we will run a loop from 0 to n-1
- Add value in map and count the occurrence.
- After completing loop run an another loop
- If map is greater than n/2 return map of first . Otherwise return -1.
  
#### Dry Run
given arr[]={2,2,1,1,1,2,2}
i=0: map={2:1},
i=1: map={2:2}
i=2: map={2:2,1:1}
i=3: map={2:2,1:2}
i=4: map={2:2,1:3}
i=5: map={2:3,1:3}
i=6: map={2:4,1:3}
here 2 has 4 count and 4>3 so, answer is 2.
#### Code
```
#include <bits/stdc++.h>
using namespace std;

int f(vector<int> &v) {
    int n = v.size();
    map<int,int> mpp;
for(int i=0; i<n; i++){
    mpp[v[i]]++;
}
    for(auto i:mpp){
        if(i.second > n/2){
            return i.first;
        }
    }
    return -1;
}

int main() {
    vector<int> arr = {2, 2, 1, 1, 1, 2,2};
    cout<<f(arr);
    
    return 0;
}
```
#### Optimize Approach 
#### Approach 
- we will a initialise int variable el and count will be 0.
- we will run a loop from 0 to n-1
- inside loop first we check if count is 0 then increase by 1 and el will current element.
- Else Check if v[i] is equal to el then increase count by 1.
- Otherwise decrease count by -1.
- After completing this we take another cnt1 and run an another loop
- Check if v[i]==el increase cnt1 by 1.
- After completing take another check if el>n/2 return el or n-1.

#### Code 
```
#include <bits/stdc++.h>
using namespace std;

int f(vector<int> &v) {
    int n = v.size();
    int cnt= 0;
    int el;
    for(int i=0; i<n; i++){
        // Check if count is 0 than increase count and initialise el 
        if(cnt==0){
            cnt++;
            el= v[i];
        }
            //if el is equal to current element increase count
        else if(v[i]==el){
            cnt++;
        }
            // Otherwise decrease count
        else cnt--;
    }
    // Now count all occurrence of that element which has count
    int count=0;
    for(int i=0;i<n;i++){
        if(v[i]==el){
          count++ ; 
        }
        if(count>n/2) return v[i];
    }
    return -1;
}

int main() {
    vector<int> arr = { 2,2, 1, 1, 1, 2,2};
    cout<<f(arr);
    
    return 0;
}
```
#### Complexity Analysis 
Time Complexity: O(N) + O(N), where N = size of the given array.
Reason: The first O(N) is to calculate the count and find the expected majority element. The second one is to check if the expected element is the majority one or not.

#### 4. Kadane's Algorithm : Maximum Subarray Sum in an Array
#### Problem Statement: Given an integer array arr, find the contiguous subarray (containing at least one number) which
has the largest sum and returns its sum and prints the subarray.

Examples
Example 1:

Input: arr = [-2,1,-3,4,-1,2,1,-5,4] 

Output: 6 

Explanation: [4,-1,2,1] has the largest sum = 6. 

Examples 2: 

Input: arr = [1] 

Output: 1 

Explanation: Array has only one element and which is giving positive sum of 1. 
Disclaimer: Don’t jump directly to the solution, try it out yourself first.
#### Brute Force Approach 
#### Approach 
- First initialise maxi with a value 0 
- We will run a loop from 0 to n-1
- inside loop We set sum with 0
- And run another loop from i to avoid repeated sum to n-1.
- Add v[i] to sum and check if sum greater than maxi then put maxi will be sum.
 
#### Dry Run
![1000034619](https://github.com/user-attachments/assets/16630dfa-e9f8-472f-808f-885b469fa2e0)

#### Code 
```
#include <bits/stdc++.h>
using namespace std;

int f(vector<int> &v) {
    int n = v.size();
    // To store max sum
    int maxi= 0;
    for(int i=0; i<n; i++){
        int sum=0;
        for(int j=i; j<n; j++){
            sum+=v[j];
            // take only max sum 
            maxi= max(maxi,sum);
        }
        
    }
   return maxi;
}

int main() {
    vector<int> arr = { -2,1,-3,4,-1,2,1,-5,4};
    cout<<f(arr);
    
    return 0;
}
```
#### Optimize Approach 
#### Approach 
- First initialise maxi with a value 0 
- We will run a loop from 0 to n-1
- inside loop We set sum with 0
- And run another loop from i to avoid repeated sum to n-1.
- Add v[i] to sum and check if sum greater than maxi then put maxi will be sum.
- To avoid the negative values we use kadane Algorithm.
#### Code
```
#include <bits/stdc++.h>
using namespace std;

int f(vector<int> &v) {
    int n = v.size();
    // To store max sum
    int maxi= 0;
    for(int i=0; i<n; i++){
        int sum=0;
        for(int j=i; j<n; j++){
            sum+=v[j];
            // take only max sum 
            maxi= max(maxi,sum);
        }
        // To avoid negetive value we use kadane Algorithm 
        if(sum<0)
            sum=0;
    }
   return maxi;
}

int main() {
    vector<int> arr = { -2,1,-3,4,-1,2,1,-5,4};
    cout<<f(arr);
    
    return 0;
}
```
### 5.Stock buy and sell
#### Problem Statement: You are given an array of prices where prices[i] is the price of a given stock on an ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock. Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

Examples
Example 1:

Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and 
sell on day 5 (price = 6), profit = 6-1 = 5.

Note: That buying on day 2 and selling on day 1 
is not allowed because you must buy before 
you sell.

Example 2:

Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are 
done and the max profit = 0.

#### Brute Force Approach 
#### Approach 
- Use a for loop of ‘i’ from 0 to n.
- Use another for loop of j from ‘i+1’ to n.
- If arr[j] > arr[i] , take the difference and compare  and store it in the maxPro variable.
- Return maxPro.
#### Dry Run
#### Code
```
#include <bits/stdc++.h>
using namespace std;

int f(vector<int> &v) {
    int n = v.size();
    // To store max sum
    int profit=0;
    for(int i=0; i<n; i++){
        for(int j=i+1; j<n; j++){
            if(v[j]>v[i]){
                profit= max(profit,v[j]-v[i]);
            }
        }
    }
    return profit;
}

int main() {
    vector<int> arr = {7,1,5,3,6,4};
    cout<<f(arr);
    
    return 0;
}
```
#### Optimize Approach 
#### Approach 
- Create a variable maxPro and store 0 initially.
- Create a variable minPrice and store some larger value(ex: MAX_VALUE) value initially.
- Run a for loop from 0 to n.
- Update the minPrice if it is greater than the current element of the array
- Take the difference of the minPrice with the current element of the array and compare and maintain it in maxPro.
- Return the maxPro.
#### Dry Run
#### Code
```
#include <bits/stdc++.h>
using namespace std;

int f(vector<int> &v) {
    int n = v.size();

    int profit=0;
    int buy=INT_MAX;
    for(int i=0; i<n; i++){
       buy = min(buy,v[i]);
        profit= max(profit,v[i] -buy);
    }
    return profit;
}

int main() {
    vector<int> arr = {7,1,5,3,6,4};
    cout<<f(arr);
    
    return 0;
}
```
### 6. Rearrange 
#### Variety-1
#### Problem Statement:

There’s an array ‘A’ of size ‘N’ with an equal number of positive and negative elements. Without altering the relative order of positive and negative elements, you must return an array of alternately positive and negative values.

Note: Start the array with positive elements.

Examples: 

Example 1:

Input:
arr[] = {1,2,-4,-5}, N = 4
Output:
1 -4 2 -5

Explanation: 

Positive elements = 1,2
Negative elements = -4,-5
To maintain relative ordering, 1 must occur before 2, and -4 must occur before -5.

Example 2:
Input:
arr[] = {1,2,-3,-1,-2,-3}, N = 6
Output:
1 -3 2 -1 3 -2
Explanation: 

Positive elements = 1,2,3
Negative elements = -3,-1,-2
To maintain relative ordering, 1 must occur before 2, and 2 must occur before 3.
Also, -3 should come before -1, and -1 should come before -2.

#### Brute Force Approach 
#### Approach 
In this simple approach, since the number of positive and negative elements are the same, we put positives into an array called “pos” and negatives into an array called “neg”.
After segregating each of the positive and negative elements, we start putting them alternatively back into array A.
Since the array must begin with a positive number and the start index is 0, so all the positive numbers would be placed at even indices (2*i) and negatives at the odd indices (2*i+1), where i is the index of the pos or neg array while traversing them simultaneously.
This approach uses O(N+N/2) of running time due to multiple traversals which we’ll try to optimize in the optimized approach given below.

#### Code
```
#include <bits/stdc++.h>
using namespace std;

vector <int>f(vector<int> &v) {
    int n = v.size();
// Initialise 2 Array pos and neg
    vector<int> pos,neg;
    for(int i=0;i<n;i++){
        if(v[i]>0)
            pos.push_back(v[i]);
        else 
            neg.push_back(v[i]);
    }
    for(int i=0; i<n/2;i++){
        v[i*2]=pos[i];
       v[i*2+1]= neg[i]; 
    }
    return v;
}

int main() {
    vector<int> arr = {1,2,-3,-1,-2,3};
   vector <int> ans = f(arr);
    for(auto i:ans)
        cout<<i<<" ";
    return 0;
}
```
#### Complexity Analysis 
Time Complexity: O(N+N/2) { O(N) for traversing the array once for segregating positives and negatives and another O(N/2) for adding those elements alternatively to the array, where N = size of the array A}.

Space Complexity:  O(N/2 + N/2) = O(N) { N/2 space required for each of the positive and negative element arrays, where N = size of the array A}.
#### Optimize Approach 
#### Approach 
#### Code
```
#include <bits/stdc++.h>
using namespace std;

vector <int>f(vector<int> &v) {
    int n = v.size();
// Initialise 2 int pos and neg and ans 
    vector<int> ans(n);
    int pos= 0, neg= 1;
    for(int i=0;i<n;i++){
        if(v[i]<0){
          ans[neg]=v[i];
            neg+=2;
        }
        else{
       ans[pos]= v[i]; 
            pos+=2;
        }
    }
    return ans;
}


int main() {
    vector<int> arr = {1,2,-3,-1,-2,3};
   vector <int> ans = f(arr);
    for(auto i:ans)
        cout<<i<<" ";
    return 0;
}
```
#### Complexity Analysis 
Time Complexity: O(N) { O(N) for traversing the array once and substituting positives and negatives simultaneously using pointers, where N = size of the array A}.

Space Complexity:  O(N) { Extra Space used to store the rearranged elements separately in an array, where N = size of array A}.

Variety-2
Problem Statement:
There’s an array ‘A’ of size ‘N’ with positive and negative elements (not necessarily equal). Without altering the relative order of positive and negative elements, you must return an array of alternately positive and negative values. The leftover elements should be placed at the very end in the same order as in array A.

Note: Start the array with positive elements.

Examples: 

Example 1:

Input:
arr[] = {1,2,-4,-5,3,4}, N = 6
Output:
1 -4 2 -5 3 4

Explanation: 

Positive elements = 1,2
Negative elements = -4,-5
To maintain relative ordering, 1 must occur before 2, and -4 must occur before -5.
Leftover positive elements are 3 and 4 which are then placed at the end of the array.

Example 2:
Input:
arr[] = {1,2,-3,-1,-2,-3}, N = 6
Output:
1 -3 2 -1 3 -2
Explanation: 

Positive elements = 1,2
Negative elements = -3,-1,-2,-4
To maintain relative ordering, 1 must occur before 2.
Also, -3 should come before -1, and -1 should come before -2.
After alternate ordering, -2 and -4 are left, which would be placed at the end of the ans array.
#### Brute Force Approach 
#### Approach 
- In this problem, first, we create a neg array and a pos array for storing all the negative and positive elements of array A separately.
- Now, similar to the Brute force approach for variety-1, we start putting elements of pos and neg array alternatively back into array A.
- Since the array must begin with a positive number and the start index is 0, so all the positive numbers would be placed at even indices (2*i) and negatives at the odd indices (2*i+1), where i is the index of the pos or neg array while traversing them simultaneously.
- After all the elements are added to the index where positives were equal to the negatives, we now put all the remaining elements ( whether positive or negative) at the last of the array by running a single loop from pos.size() to neg.size() {if positives < negatives} or neg.size() to pos.size() {if negatives < positives}.
- #### Code
```
#include<bits/stdc++.h>
using namespace std;

  vector<int> RearrangebySign(vector<int>A, int n){
    
  // Define 2 vectors, one for storing positive 
  // and other for negative elements of the array.
  vector<int> pos;
  vector<int> neg;
  
  // Segregate the array into positives and negatives.
  for(int i=0;i<n;i++){
      
      if(A[i]>0) pos.push_back(A[i]);
      else neg.push_back(A[i]);
  }
  
  // If positives are lesser than the negatives.
  if(pos.size() < neg.size()){
      
    // First, fill array alternatively till the point 
    // where positives and negatives ar equal in number.
    for(int i=0;i<pos.size();i++){
      
      A[2*i] = pos[i];
      A[2*i+1] = neg[i];
    }
    
    // Fill the remaining negatives at the end of the array.
    int index = pos.size()*2;
    for(int i = pos.size();i<neg.size();i++){
        
        A[index] = neg[i];
        index++;
    }
  }
  
  // If negatives are lesser than the positives.
  else{
      
      // First, fill array alternatively till the point 
      // where positives and negatives ar equal in number.
      for(int i=0;i<neg.size();i++){
      
      A[2*i] = pos[i];
      A[2*i+1] = neg[i];
  }
    
    // Fill the remaining positives at the end of the array.
    int index = neg.size()*2;
    for(int i = neg.size();i<pos.size();i++){
        
        A[index] = pos[i];
        index++;
    }
  }
  return A;
    
}
  ```
#### Complexity Analysis
Time Complexity: O(2*N) { The worst case complexity is O(2*N) which is a combination of O(N) of traversing the array to segregate into neg and pos array and O(N) for adding the elements alternatively to the main array}.

Explanation: The second O(N) is a combination of O(min(pos, neg)) + O(leftover elements). There can be two cases: when only positive or only negative elements are present, O(min(pos, neg)) + O(leftover) = O(0) + O(N), and when equal no. of positive and negative elements are present, O(min(pos, neg)) + O(leftover) = O(N/2) + O(0). So, from these two cases, we can say the worst-case time complexity is O(N) for the second part, and by adding the first part we get the total complexity of O(2*N).

Space Complexity:  O(N/2 + N/2) = O(N) { N/2 space required for each of the positive and negative element arrays, where N = size of the array A}.
### 7. Leaders in an Array
#### Problem Statement: Given an array, print all the elements which are leaders. A Leader is an element that is greater than all of the elements on its right side in the array.
Examples
Example 1:
Input:
 arr = [4, 7, 1, 0]
Output:
 7 1 0
Explanation:
 Rightmost element is always a leader. 7 and 1 are greater than the elements in their right side.
Example 2:
Input:
 arr = [10, 22, 12, 3, 0, 6]
Output:
 22 12 6
Explanation:
 6 is a leader. In addition to that, 12 is greater than all the elements in its right side (3, 0, 6), also 22 is greater than 12, 3, 0, 6.
 #### Brute Force Approach 
 #### Approach 
-  In this brute force approach, we start checking all the elements from the start of the array to the end to see if an element is greater than all the elements on its right (i.e, the leader).
- For this, we will use nested loops where the outer loop will check for each element in the array whether it is a leader or not.
- The inner loop checks if there is any element to the right that is greater than the element currently traversed by the outer loop.
- We start by initializing the outer loop pointer to the start element and setting it as the current leader.
- If any element traversed is found greater than the element currently set as a leader, it will not go to the ans array and we increment the outer loop pointer by 1 and set the next element as the current leader.
- If we don’t find any other element to the right greater than the current element, then we push the current element to the ans array stating that is it the leader element.
#### Code 
```
#include <bits/stdc++.h>
using namespace std;

vector <int>f(vector<int> &v) {
    int n= v.size();
    vector<int> ans;
    for(int i=0; i<n; i++){
        bool leader=true;
       for(int j= i+1; j<n; j++){
           if(v[j]>v[i]){
               leader= false;
               break;
           }
       }
        if(leader){
            ans.push_back(v[i]);
        }
    }
    return ans;
}


int main() {
    vector<int> arr = {4, 7, 1, 0};
   vector <int> ans = f(arr);
    for(auto i:ans)
        cout<<i<<" ";
    return 0;
}
```
#### Complexity Analysis 
Time Complexity: O(N^2) { Since there are nested loops being used, at the worst case n^2 time would be consumed }.

Space Complexity: O(N) { There is no extra space being used in this approach. But, a O(N) of space for ans array will be used in the worst case }.
#### Optimize Approach 
#### Approach 
#### Code
```
#include <bits/stdc++.h>
using namespace std;

vector <int>f(vector<int> &v) {
    int n= v.size();
    vector<int> ans;
    int max=v[n-1];
    ans.push_back(v[n-1]);
    for(int i=n-2; i>0; i--){
        if(v[i]>max){
            ans.push_back(v[i]);
            max=ans[i];
        }
    }
    return ans;
}


int main() {
    vector<int> arr = {4, 7, 1, 0};
   vector <int> ans = f(arr);
    for(int i= ans.size()-1; i>=0;i--)
        cout<<ans[i]<<" ";
    return 0;
}
```
#### Complexity Analysis 
Time Complexity: O(N) { Since the array is traversed single time back to front, it will consume O(N) of time where N = size of the array }.
Space Complexity: O(N) { There is no extra space being used in this approach. But, a O(N) of space for ans array will be used in the worst case }.

### 8. Longest Consecutive Sequence in an Array

Mark as Completed

538


Problem Statement: You are given an array of ‘N’ integers. You need to find the length of the longest sequence which contains the consecutive elements.

Examples

Example 1:

Input: [100, 200, 1, 3, 2, 4]

Output: 4

Explanation: The longest consecutive subsequence is 1, 2, 3, and 4.

Input: [3, 8, 5, 7, 6]

Output: 4

Explanation: The longest consecutive subsequence is 5, 6, 7, and 8.

#### Brute Force Approach 
#### Approach 
- To begin, we will utilize a loop to iterate through each element one by one.
- Next, for every element x, we will try to find the consecutive elements like x+1, x+2, x+3, and so on using the linear search algorithm in the given array.
- Within a loop, our objective is to locate the next consecutive element x+1. 
- If this element is found, we increment x by 1 and continue the search for x+2. 
- Furthermore, we increment the length of the current sequence (cnt) by 1.
#### Code
```
#include <bits/stdc++.h>
using namespace std;
bool search(vector<int>&v,int num){
    int n= v.size();
    for(int i=0; i<n; i++){
        if(v[i]==num) return true;
    }
    return false;
}
int f(vector<int> &v){
    int n= v.size();
    int longest=1;
    for(int i=0; i<n; i++){
        int x= v[i];
        int cnt=1;
        while(search(v,x+1)==true){
            x+=1;
            cnt+=1;
        }
        longest= max(longest,cnt);
    }
   return longest;
}
int main() {
    
    vector<int> a = {100, 200, 1, 2, 3, 4};
    cout<<f(a);
    return 0;
}
```
#### Complexity Analysis 
Complexity Analysis

Time Complexity: O(N2), N = size of the given array.
Reason: We are using nested loops each running for approximately N times.

Space Complexity: O(1), as we are not using any extra space to solve this problem.

#### Better Approach 
#### Approach 
- We will consider 3 variables, 
‘lastSmaller’ →(to store the last included element of the current sequence), 
‘cnt’ → (to store the length of the current sequence), 
‘longest’ → (to store the maximum length).
- Initialize ‘lastSmaller’ with ‘INT_MIN’, ‘cnt’ with 0, and ‘longest’ with 1(as the minimum length of the sequence is 1).
The steps are as follows:

- First, we will sort the entire array.
- To begin, we will utilize a loop(say i) to iterate through each element one by one.
- For every element, we will check if this can be a part of the current sequence like the following:
- If arr[i]-1 == lastSmaller: The last element in our sequence is labeled as 'lastSmaller' and the current element 'arr[i]' is exactly 'lastSmaller'+1. It indicates that 'arr[i]' is the next consecutive element. To incorporate it into the sequence, we update 'lastSmaller' with the value of 'arr[i]' and increment the length of the current sequence, denoted as 'cnt', by 1.
- If arr[i] == lastSmaller: If the current element, arr[i], matches the last element of the sequence (represented by 'lastSmaller'), we can skip it since we have already included it before.
- Otherwise, if lastSmaller != arr[i]: On satisfying this condition, we can conclude that the current element, arr[i] > lastSmaller+1. It indicates that arr[i] cannot be a part of the current sequence. So, we will start a new sequence from arr[i] by updating ‘lastSmaller’ with the value of arr[i]. And we will set the length of the current sequence(cnt) to 1.
- Every time, inside the loop, we will compare ‘cnt’ and ‘longest’ and update ‘longest’ with the maximum value. longest = max(longest, cnt)
- Finally, once the iteration is complete, we will have the answer stored in the variable ‘longest’.

#### Code
```
#include <bits/stdc++.h>
using namespace std;
int f(vector<int> &v){
  int n= v.size();
    if(n==0) return 0;
    int last=INT_MIN;
    int longest = 1,cnt=0;
    sort(v.begin(),v.end());
    for(int i=0; i<n; i++){
        if(v[i]-1==last){
            cnt+=1;
            last= v[i];
        }
        else if(v[i]!=last){
            cnt=1;
            last= v[i];
        }
        longest= max(longest,cnt);
    }
    return longest;
    
}
int main() {
    
    vector<int> a = {100, 200, 1, 2, 3, 4};
    cout<<f(a);
    return 0;
}
```
#### Complexity Analysis 
Time Complexity: O(NlogN) + O(N), N = size of the given array.
Reason: O(NlogN) for sorting the array. To find the longest sequence, we are using a loop that results in O(N).

Space Complexity: O(1), as we are not using any extra space to solve this problem.

#### Optimize Approach 
#### Approach 
#### Code
```

```
### Print Pascal Triangle 
```
int bino(int n,int k){
    int res=1;
    if(k>n-k) k= n-k;
    for(int i=0; i<k; i++){
        res*= n-i;
        res/= i+1;
    }
    return res;
}
void ma(int r){
    int n= r;
    
    for(int i=0; i<n; i++){
        for(int j=0; j<=i; j++){
           cout<<" "<< bino(i,j); 
            
        }cout<<endl;
    }
}


int main() {
    vector<int> arr = {4, 7, 1, 0};
  // vector <int> ans = f(arr);
    
     ma(7);
    
    return 0;
}
```
