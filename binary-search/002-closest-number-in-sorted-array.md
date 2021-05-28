### cloest number in a sorted array

```java
int cloestNumber (int[]nums, int target) {
	if (nums == null || nums) {
		return -1;
	}

	int start = 0;
	int end = nums.length - 1;

	while (start + 1 < end) {
		int mid = start + (end - start) / 2;

		if (nums[mid] == target) {
			return nums[mid];
		}
		
	}
}
```