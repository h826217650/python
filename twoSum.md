##twoSum
思路
```
class Solution:
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        dnum = {}
        length = len(nums)
        i = 0
        while i < length :
            expectNum = target - nums[i]
            if expectNum in dnum :
                return dnum[expectNum], i
            else :
                dnum[nums[i]] = i
            i = i + 1
```