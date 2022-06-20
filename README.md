# C Language Practice

#面試考題：

##Two sum
##Longest Substring Without Repeating Characters
##Longest Palindromic Substring
##Valid Parenttheses
##Move Zeros
##Merge intevals
## Single Number

int singleNumber(int* nums, int numsSize)
{
    for(int i=0;i<numsSize;i++){
        printf("%d\n",nums[i]);
        int count=0;
        for(int j=0;j<numsSize;j++){
            if(nums[i]==nums[j]){
                count++;
            }   
            }
            if(count==1){
                return nums[i];
        }           
    }
    return 0 ;    
}


or 


#include <stdio.h>

int singleNumber(int* nums, int numsSize)
{
    int n=nums[0] ;
    for(int i=1;i<numsSize;i++){
      n^=nums[i];
    }
  return n;
}
int main(void) {
  int input[3]={2,2,1};
  printf("%d\n",singleNumber(input,3));
  return 0;
}


## Happy Number

int next_t(int n){
    int r=0;
    while (n!=0){
        int d=n%10;
        n/=10;
        r+=d*d;
    }
    return r;
}
bool contains(int* history, int size,int n){//檢查n是否在history中出現過
    for(int i=0;i<size;i++){
        if(history[i]==n){
            return true;
    }
    }
    return false;
}

bool isHappy(int n){
    int history[10000];//我們去過哪裡
    int size=0;//總共有幾個地方
    
    while (!contains(history,size,n)){
        history[size]=n;
        size++;
        n=next_t(n);
    }
    return n==1;
}




## Maximum subarray
int maxSubArray(int* nums, int numsSize){
    int max=INT_MIN;//目前為止最大值
    //選擇一個起點
    for(int i=0;i<numsSize;i++){
        //選擇一個終點
        for(int j=i;j<numsSize;j++){
            //計算從起點到終點的和
            int sum=0;
            for(int k=i;k<=j;k++){//k=1,3,4,j
                sum+=nums[k];
            }
            //如果比原本的最大值大，就換掉
            if(sum>max){
                max=sum;
            }
            //sum==nums[i]+...+nums[j];//i<=j
    printf("%d %d : %d\n",i,j,sum);
        
    }
    }
    return max;
}

## First Bad Version
// The API isBadVersion is defined for you.
// bool isBadVersion(int version);
long long  binarySearch(long long first,long long last){
    
    long long  mid=first+(last-first)/2;//length:last-first
    if(isBadVersion(mid)&&!isBadVersion(mid-1)){
        return mid;
    }
    if(!isBadVersion(mid)){
        return binarySearch(mid+1,last);
    }
        
        return binarySearch(first,mid);
}
int firstBadVersion(int n) {
    //[1,2,3,4,5,6,7..., n]
    // G G G G G G B B B B
    //ans:
    return binarySearch(1,(long long)1+n);
   
}
