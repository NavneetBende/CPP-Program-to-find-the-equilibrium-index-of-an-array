Equilibrium index of an array
Here,  in this section we will learn about the C++ program to find the equilibrium index of an array. Equilibrium index of an array is an index such that the sum of elements at lower indexes is equal to the sum of elements at higher indexes.

Equilibrium index of an array
While loop in C
Method Discussed :
Method 1 : Using Nested loops.
Method 2 : Using single for loop
Method 3 : Using Binary search concept.
Method 1 :
Run a loop from index 0 to n.
Create a variable say left_sum =0, to find the left indexed value sum.
Run a loop from index 0 to i to find left_sum.
Similarly, declare right_sum = 0,
Run a loop from index i to n, and find right_sum.
If left_sum == right_sum, return i.
Method 1 : Code in C++
#include<bits/stdc++.h>
using namespace std;

void find (int arr[], int n)
{
  int result = -1;
  
  for(int i=0; i<n; i++){
    
    int left_sum =0;
    for(int j=0; j<i; j++)
       left_sum += arr[i];
    int right_sum =0;
    for(int j=i+1; j<n; j++)
       right_sum += arr[i];
    
    if(right_sum == left_sum)
    result = i;
      
  }
  
    cout<<"First Point of equilibrium is at index = "<<result;
    return;
  
}

int main ()
{
  int arr[]={4, -2, 0, 6, -4};
  int n = sizeof(arr)/sizeof(arr[0]);

  find (arr, n);
  return 0;
}
Output
Equilibrium index : 3
Method 2 :
In this method we will use single loop to find the equilibrium point in the array.

Time-Complexity : O(n)
Space – Complexity : O(1)
Method 2 : Code in C++
#include <bits/stdc++.h>
using namespace std;
 
int equilibrium(int arr[], int n)
{
    int sum = 0; 
    int leftsum = 0; 
 
    /* Find sum of the whole array */
    for (int i = 0; i < n; ++i)
        sum += arr[i];
 
    for (int i = 0; i < n; ++i)
    {
        sum -= arr[i]; 
 
        if (leftsum == sum)
            return i;
 
        leftsum += arr[i];
    }
 
    /* If no equilibrium index found, then return 0 */
    return -1;
}
 
// Driver code
int main()
{
    int arr[] = { -7, 1, 5, 2, -4, 3, 0 };
    int arr_size = sizeof(arr) / sizeof(arr[0]);
    cout << "Equilibrium index : " << equilibrium(arr, arr_size);
    return 0;
}
Output
Equilibrium index : 3
Method 3 :
In this method we will discuss the binary search concept to find the equilibrium index.

Method 3 : Code in C++
#include<bits/stdc++.h>
using namespace std;

void find (int arr[], int n)
{
  int mid = n / 2;
  int leftSum = 0, rightSum = 0;

  //calculation sum to left of mid
  for (int i = 0; i < mid; i++){ 
   leftSum += arr[i];
   } 
  //calculating sum to right of mid 
  for (int i = n - 1; i > mid; i--){
    rightSum += arr[i];
  }

  //if rightsum > leftsum
  if (rightSum > leftSum){
    //we keep moving right until rightSum become equal or less than leftSum
    while (rightSum > leftSum && mid < n - 1){ 
     rightSum -= arr[mid + 1];
     leftSum += arr[mid]; 
     mid++;
    }
   }
  else{ 
   //we keep moving right until leftSum become equal or less than RightSum 
   while (leftSum > rightSum && mid > 0){
	rightSum += arr[mid];
	leftSum -= arr[mid - 1];
	mid--;
    }
  }

  //check if both sum become equal
  if (rightSum == leftSum){
    cout<<"First Point of equilibrium is at index = "<< mid;
    return;
  }

  cout<<"First Point of equilibrium is at index = -1 ";
}

int main ()
{
  int arr[]={4, -2, 0, 6, -4};
  int n = sizeof(arr)/sizeof(arr[0]);

  find (arr, n);
  return 0;
}
Output
First Point of equilibrium is at index = 2
