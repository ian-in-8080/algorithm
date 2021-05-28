# Sliding Window Problems

### Sliding Window Maximum
Given an array of n integer with duplicate number, and a moving window(size k), move the window at each iteration from the start of the array, find the maximum number inside the window at each moving.

```
    public List<Integer> maxSlidingWindow(int[] nums, int k) {
        // write your code here
        
        List<Integer> maxNums = new ArrayList<>();
        Deque<Integer> windowMax = new ArrayDeque<>();
        
        if (nums.length == 0) return maxNums;
        
        for (int i = 0; i < k - 1; i++) {
            inDeque(windowMax, nums[i]);
        }
        
        for (int i = k - 1; i < nums.length; i++) {
            inDeque(windowMax, nums[i]);
            maxNums.add(windowMax.peekFirst());
            outDeque(windowMax, nums[i - k + 1]);
        }
        
        return maxNums;
        
    }
    
    private void inDeque(Deque<Integer> windowMax, int num) {
        while (!windowMax.isEmpty() && windowMax.peekLast() < num) {
            windowMax.pollLast();
        }
        windowMax.offer(num);
    }
    
    private void outDeque(Deque<Integer> windowMax, int num) {
        if (!windowMax.isEmpty() && windowMax.peekFirst() == num) {
            windowMax.pollFirst();
        }
    }
```
