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
