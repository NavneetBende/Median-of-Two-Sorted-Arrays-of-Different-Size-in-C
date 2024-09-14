Median of Two Sorted Arrays of Different Size in C
Here, in this page we will discuss the program to find the Median of two sorted arrays of different size i n C+programming language. We are given with two sorted arrays say a[] and b[] of size n and m respectively. We need to find the median of these two sorted arrays.

Median of Two Sorted Arrays of Different Size in C
Different Cases :
Case 1 : If (n +m) is odd then the median will be (n+m)/2-th element .
Case 2 :If (n+m) is even, then median will be the average of the ((n+m/2)-1)-th and (n+m)/2-th element.
Method 1 :
Create another array say arr3[] of size n+m.
Now, store the elements of arr1[] and arr2[] in arr3[].
Sort the arr3[]
Now, print the median : if (n+m) is odd then median is arr3[(n+m)/2]
Otherwise, median is ((arr3[(n+m)/2])+(arr3[(n+m)/2-1]))/2.
Time and Space Complexities :
Time-Complexity : O((n+m)(n+m))
Space-Complexity : O(n+m)
Method 1 : Code in C
Run
#include <stdio.h>

int main(){

  int arr1[]={2, 6, 7, 8};
  int n = sizeof(arr1)/sizeof(arr1[0]);
  
  int arr2[]={10, 12, 17, 18, 90, 91};
  int m = sizeof(arr2)/sizeof(arr2[0]);

  int arr3[n+m];

  for(int i=0; i<n; i++)
  arr3[i]=arr1[i];

  int j=n;
  for(int i=0; i<m; i++)
  arr3[j++]=arr2[i];
  
  
  //sort arr3
  for(int i=0; i<(n+m); i++){
      for(int j=i+1; j<(n+m); j++){ if(arr3[i]>arr3[j]){
                int temp = arr3[i];
                arr3[i] = arr3[j];
                arr3[j] = temp;
          }
          
      }
  }
  
  int median;

  if((n+m)%2==0)
  median = (arr3[(n+m)/2] + arr3[(n+m)/2-1])/2;

  else 
  median = arr3[(n+m)/2];

  printf("%d ", median);
}
Output:
11
Related Pages
Given an array which consists of only 0, 1 and 2

Find the “Kth” max and min element of an array

Find the Union and Intersection of the two sorted arrays

Find Largest sum contiguous Subarray

Minimize the maximum difference between heights 

Method 2 :
Create a variable count to have a count of elements in the output array.
Now, to merge both arrays, declare two indices i and j initially assigned to 0. Compare the ith index of 1st array and jth index of second, increase the index of the smallest element and increase the count.
Now, take two variables say m1 and m2 and store (n+m)/2 and (n+m)/2-1 in these two variables respectively.
Check if the count = (m+n) / 2.
And if (m+n) is odd return m1,
Otherwise, return (m1+m2)/2.
Time and Space Complexities :
Time-Complexity : O((n+m))
Space-Complexity : O(1)
Method 2 : Code in C
Run
#include <stdio.h>

int main(){

  int arr1[]={2, 6, 7, 8};
  int n = sizeof(arr1)/sizeof(arr1[0]);
  
  int arr2[]={10, 12, 17, 18, 90, 91};
  int m = sizeof(arr2)/sizeof(arr2[0]);

  int i = 0, j=0, count =0, m1=-1, m2=-1; 

  for (; count <= (n + m)/2; count++) 
  { 
      m2=m1; 
      if(i != n && j != m) 
      { 
          m1 = (arr1[i] > arr2[j]) ? arr2[j++] : arr1[i++];
    }
    else if(i < n)
    {
       m1 = arr1[i++];
    }
    else
    {
       m1 = arr2[j++];
    }
  }

  if((n + m) % 2 == 1)
    printf("%d ", m1);

  else
    printf("%d ", (m1+m2)/2);
}
Output:
11
