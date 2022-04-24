# Leetcode
C Language Practice

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


https://replit.com/@exo881222/single-number#main.c
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

