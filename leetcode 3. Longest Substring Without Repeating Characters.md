leetcode 3. Longest Substring Without Repeating Characters
==========================================================
## Problem ##
Given a string s, find the length of the longest substring without repeating characters.
* Example 1

        Input: s = "abcabcbb"
        Output: 3
        Explanation: The answer is "abc", with the length of 3.
        
* Example 2

        Input: s = "bbbbb"
        Output: 1
        Explanation: The answer is "b", with the length of 1.
        
* Example 3

        Input: s = "pwwkew"
        Output: 3
        Explanation: The answer is "wke", with the length of 3.
        Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.

## Solution ##
* Solution 1

    The simple method is to use the hashmap to check if there is a repeat letter, start from each letter,
    and finally return the longest length. There will be a for loop inside another for loop, so the time
    complexity should be O(n^2).

        class Solution {
            public int lengthOfLongestSubstring(String s) {
                int len = 0;
                int stringLength =  s.length();
                int answer = 0;
                HashMap<String,Integer> hashMap;
                for (int j = 0; j < stringLength; j ++){
                    int count = 0;
                    hashMap = new HashMap<>();
                    for (int i = j; i < stringLength; i ++){
                        String str =  s.substring(i, i+1);
                        if (hashMap.putIfAbsent(str, 1) != null){
                            break;
                        }
                        count ++;
                        if (count > answer){
                            answer = count;
                        }
                    }
                }
                return answer;
            }
        }

* Solution 2

    Reduce the time complexity from the last solution. Use two pointers instead of a for loop to 
    identify a sub string, so the time complexity will only be O(n) because each letter has been
    used at most twice.

        
