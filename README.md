# Leetcode---1695
Maximum Erasure Value
//code in java 
import java.util.HashSet;
import java.util.Set;

class Solution {
    public int maximumUniqueSubarray(int[] nums) {
        int ans = 0; // Stores the maximum unique subarray sum found so far
        int currentSum = 0; // Stores the sum of elements in the current unique subarray
        Set<Integer> seen = new HashSet<>(); // Stores unique elements in the current window

        int left = 0; // Left pointer of the sliding window

        // Iterate with the right pointer
        for (int right = 0; right < nums.length; ++right) {
            // While the current element (nums[right]) is already in the 'seen' set,
            // shrink the window from the left
            while (seen.contains(nums[right])) {
                currentSum -= nums[left]; // Remove the element at 'left' from the sum
                seen.remove(nums[left]); // Remove the element from the set
                left++; // Move the left pointer
            }

            // Add the current element (nums[right]) to the window
            currentSum += nums[right];
            seen.add(nums[right]);

            // Update the maximum unique subarray sum
            ans = Math.max(ans, currentSum);
        }

        return ans;
    }
}
