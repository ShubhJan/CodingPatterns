# Pattern 1 : Sliding Window
## Q 1 : [Longest Substring Without Repeating Characters]( https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

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
