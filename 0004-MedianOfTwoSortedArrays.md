# 4) Median of Two Sorted Arrays

## First submission (0 ms)

Use a binary search-like algorithm on the smaller array until you find the position where <b>last elements</b> (`maxLeftA` and `maxLeftB`) of the `leftPartitionA` and `leftPartitionB` meets the conditions (`maxLeftB <= minRightA` and `maxLeftA <= minRightB`).

```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        if len(nums1) > len(nums2):
            return self.findMedianSortedArrays(nums2, nums1)

        m, n = len(nums1), len(nums2)
        left, right = 0, m
        mid = (m + n + 1) // 2

        while left <= right:
            partitionA = (left + right) // 2
            partitionB = mid - partitionA

            minRightA = float("inf") if partitionA == m else nums1[partitionA]
            minRightB = float("inf") if partitionB == n else nums2[partitionB]

            maxLeftA = float("-inf") if partitionA == 0 else nums1[partitionA - 1]
            maxLeftB = float("-inf") if partitionB == 0 else nums2[partitionB - 1]

            if maxLeftA <= minRightB and maxLeftB <= minRightA:
                if (m + n) % 2 == 0:
                    return (max(maxLeftA, maxLeftB) + min(minRightA, minRightB)) / 2
                else:
                    return max(maxLeftA, maxLeftB)
            elif maxLeftA > minRightB:
                right = partitionA - 1
            else:
                left = partitionA + 1
```