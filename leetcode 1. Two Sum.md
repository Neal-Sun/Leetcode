leetcode 1. Two Sum
======================
## Problem ##
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.

*  Example 1

        Input: nums = [2,7,11,15], target = 9    
        Output: [0,1]
        Output: Because nums[0] + nums[1] == 9, we return [0, 1].
   
* Example 2

        Input: nums = [3,2,4], target = 6
        Output: [1,2]
  
* Example 3

        Input: nums = [3,3], target = 6
        Output: [0,1]
  
## Solution ##


* solution 1

    Use the brute force method with two for loops, to check if any two numbers' sum 
    will mathch the target answer, the complexity will be O(n^2). The brute force is
    too easy and I won't show the code.

* solution 2

    The second method is to use the hashTable to reduce the complexity. First we can
    add each node into the hashTable as "key: number, value: index", then we can loop
    over the int array, for each value, we check if there is another value equals to 
    target minus current value. If so, then we find our answer and return. The complexity 
    should be O(n).
    
      class Solution {
         public int[] twoSum(int[] nums, int target) {
            HashMap<Integer, Integer> map = new HashMap<>();
            for (int i =0; i < nums.length; i ++){
                  map.put(nums[i], i);
            }
            for (int i = 0; i < nums.length; i ++){
                  int temp = target - nums[i];
                if (map.containsKey(temp) && map.get(temp) != i){
                     return new int[]{i, map.get(temp)};
                }
             }
             return new int[]{0,0};
          }
      }

