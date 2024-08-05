# Pattern 1 : Sliding Window
## Q 1 : [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

**Solution :**


````Java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int maxLen = 0;
        HashMap<Character, Integer> hmap = new HashMap<>();
        int l = 0, r = 0, n = s.length();
        while(r < n){
            if(hmap.containsKey(s.charAt(r))){
                l = Math.max(l,hmap.get(s.charAt(r))+1); //So that L doesnt move backwards
                // hmap.remove(s.charAt(r));
            }
                hmap.put(s.charAt(r), r);
                maxLen = Math.max(maxLen, r - l + 1);
                r++;
        }
        return maxLen;
    }
}
````

## Q 2 : [Maximum Points You Can Obtain From Cards](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/description/)

**Solution :**

````Java
class Solution {
    public int maxScore(int[] cardPoints, int k) {
        int lSum = 0, rSum = 0, maxSum = 0, n = cardPoints.length;
        for(int i = 0; i < k; i++){
            lSum += cardPoints[i];
        }
        maxSum = lSum;
        for(int i = k - 1; i >= 0; i--){
            lSum -= cardPoints[i];
            rSum += cardPoints[n-1];
            n--;
            maxSum = Math.max(maxSum, lSum + rSum);
        }

        return maxSum;
    }
}
````
## Q 3 : [Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/)

**Solution :**

````Java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int l = 0, r = 0;
        int len = 0, maxLen = 0;
        for(r = 0; r < nums.length; r++){
            if(nums[r] == 0){
                l = r+1;
            }else{
                len = r - l + 1;
            }
            maxLen = Math.max(maxLen, len);
        }
        return maxLen;
    }
}
````

## Q 4 : [Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)

**Solution :**

````Java
class Solution {
    public int longestOnes(int[] nums, int k) {
        int n = nums.length;
        int maxLen = 0, len = 0, zeros = 0;
        int l = 0, r = 0;
        while(r < n){
            if(nums[r] == 0){
                zeros++;
            }
            if(zeros > k){
                if(nums[l] == 0)    zeros--;
                l++;
            }
            if(zeros <= k){
                len = r - l + 1;
                maxLen = Math.max(maxLen, len);
            }

            r++;
        }

        return maxLen;
    }
}
````

## Q 5 : [Longest Substring with at most/equal to k distinct characters](https://www.geeksforgeeks.org/problems/longest-k-unique-characters-substring0853/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card)

**Solution :**

````Java
class Solution {
    public int longestkSubstr(String s, int k) {
        // code here
        int maxLen = 0;
        HashMap<Character, Integer> hmap = new HashMap<>();
        int l = 0, r = 0;
        int n = s.length();
        while(r < n){
            hmap.put(s.charAt(r), hmap.getOrDefault(s.charAt(r),0)+1);
            
            if(hmap.size() > k){
                if(hmap.get(s.charAt(l)) == 1){
                    hmap.remove(s.charAt(l));
                }else{
                   hmap.put(s.charAt(l), hmap.get(s.charAt(l)) - 1);
                }
                l++;
            }
            if(hmap.size() == k)    maxLen = Math.max(maxLen, r - l + 1);
            // maxLen = Math.max(maxLen, r - l + 1);
            r++;
        }
        
        return (maxLen == 0) ? -1 : maxLen;
    }
}
````
