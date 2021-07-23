# Coursera_course
1)Maximum Subarray Sum
i/p=[-1,2,3,4,-2,6,-8,3]
o/p=13

code:
#include<vector>
using namespace std;

int maxSubarraySum(vector<int> arr){
    //Complete this function, your function should return the maximum subarray sum
    int n = arr.size();
    
    int max = 0, sum = 0;
    for(int i=0;i<arr.size();i++) {
        sum += arr[i];
        if(sum>max) {
            max = sum;
        }
        if(sum<0) {
            sum = 0;
        }
    }
    
    return max;
    
}
                  
2)Minimum Difference
i/p
a=[23,5,10,17,30]
b=[26,134,135,14,19]
o/p=(17,19)

code:
#include<vector>
#include<algorithm>
#include<climits>
#include<iostream>
using namespace std;


pair<int,int> minDifference(vector<int> a,vector<int> b){
    //Complete this method
    //two pointer -> two sum 
    // [23,5,10,17,30] -> [5,10,17,23,30] -> nlogn
    // [26,134,135,14,19] -> [14,19,26,134,135] -> nlogn
    // min = 9
    
    // i=0,j=0 -> base condition 
    // for(i,n)
    //     5  -> 14 -9, 19-14,26-21,134-129,135-130,
    //     10 -> 14-4,19-9,26-16,134,124,135-125,
    //     17 -> 14-3,19-2,26-9,134-117,135-118,
    //     23 -> 14 -9,19 -4,26-3,134-111,135-112
    //     30 -> 14-16,19-11,26-4,134-104,135-105
    sort(a.begin(),a.end());
    sort(b.begin(),b.end());
    //int n=a.size();
    int min=INT_MAX;
    int first = -1, second = -1;
    int i=0,j=0;
    
        int diff=0;
        while(i<a.size() && j<b.size())
        {
            diff=abs(a[i]-b[j]);
            if(abs(diff)<min){
                min=diff;
                first = a[i];
                second = b[j];
            }
            
            if(a[i]<b[j])
            {
                i++;
            }
            else
            {
                j++;
            }
            
            
        
    }
    return make_pair(first,second);
    
    
    
}
  
  
3)Array product without using division operation

i/p=[1,2,3,4,5]
o/p=[120,60,40,30,24]

code:
#include<vector>
using namespace std;

//Expected Complexity O(N)
vector<int> productArray(vector<int> arr){
    
    //Create an output Array
    int n = arr.size();
    vector<int> output(n,1);
    
    //update the output array and return
    //complete the code
    
    //sort -> 
    //bineary search
    //two pointer
    //previos and next value
    //memoriazation -> 
    //bit manupulation
    
    
    // [1,2,3,4,5]
    //left - [1,1,2,6,24] , right - [120,60,20,5,1]
    // [120,60,40,30,24]
    
    //log101 + log102 +..//sum- 2.07918124605
    //
    vector<int> left(n,1);
    vector<int> right(n,1);
    // a*b=c ->  120 
    //a = c/b = c * b^-1 => 120 * 
   
    //o(n)
    for(int i=1;i<n;i++)
    {
        left[i]=arr[i-1]*left[i-1];
    }
    //o(n)
    for(int j=n-2;j>=0;j--)
    {
        right[j]=arr[j+1]*right[j+1];
    }
    //o(n)
    for(int i=0;i<n;i++)
    {
        output[i]=left[i]*right[i];
    }
    
    
    
    return output;
}
 
4)Wavr array
  Given an array of integers,  sort the array into a wave like array and return it, 

In other words, arrange the elements into a sequence such that  a1 >= a2 <= a3 >= a4 <= a5.....

Example

Given [1, 2, 3, 4]

One possible answer : [2, 1, 4, 3]
Another possible answer : [4, 1, 3, 2]
                                                                                              
 Code:
   public class Solution {
    public ArrayList<Integer> wave(ArrayList<Integer> A) {
        int n=A.size();
        Collections.sort(A);
        for(int i=0;i<n;i=i+2)
        {
            //System.out.println(i+" "+ (i+1) );
            //System.out.println(A);
            if(i+1 <n){
                int temp=A.get(i);
                A.set(i,A.get(i+1));
                A.set(i+1,temp);
            }
        }
        return A;
    }
}

    
                     
                         
