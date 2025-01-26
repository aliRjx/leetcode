# 1) Two Sum

## First submission (1519 ms)

Simply loops through arrays to find out the answer.

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        length = len
        rg = range(len(nums))
        for i in rg:
            secondList = nums[i + 1 :]
            firstNum = nums[i]
            rg2 = range(len(secondList))
            for j in rg2:
                if firstNum + secondList[j] == target:
                    return [i, j + i + 1]
```

## Second submission (0 ms)

By examining others' submissions, I discovered that I could store each number's required pair to find the answer using key-value pairs (where the key is the target minus the current number, and the value is its index). If the result of the subtraction is already in the dictionary, the answer is found; otherwise, the number is added to the dictionary.

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        d = {}
        rg = range(len(nums))
        for i in rg:
            diff = target - nums[i]
            if not diff in d:
                d[nums[i]] = i
            else:
                return [d[diff], i]
```
