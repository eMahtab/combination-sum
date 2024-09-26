# Combination Sum

Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.

The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the 
frequency
 of at least one of the chosen numbers is different.

The test cases are generated such that the number of unique combinations that sum up to target is less than 150 combinations for the given input.

## https://leetcode.com/problems/combination-sum

```
Example 1:

Input: candidates = [2,3,6,7], target = 7
Output: [[2,2,3],[7]]
Explanation:
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.

Example 2:

Input: candidates = [2,3,5], target = 8
Output: [[2,2,2,2],[2,3,3],[3,5]]

Example 3:

Input: candidates = [2], target = 1
Output: []
```


## Implementation : Find Combination and Backtrack when no solution possible
```java
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> result = new ArrayList<>();
        if(candidates == null || candidates.length == 0)
        return result;
        findCombination(candidates, target, 0, new ArrayList<Integer>(), result);
        return result;
    }
    private void findCombination(int[] candidates, int target, int index, List<Integer> combination,
      List<List<Integer>> result) {
               if(target == 0) {
    	            result.add(new ArrayList<Integer>(combination));
    	            return;
    	        }
    	        for(int i = index; i < candidates.length; i++) {
    	        	if(candidates[i] <= target) {
    	        		combination.add(candidates[i]);
    	        		if(target - candidates[i] >= 0)
    	        			findCombination(candidates, target - candidates[i], i, combination, result);
    	        		combination.remove(combination.size()-1);
    	        	}   
    	        }
    }

}
```
