#在有序列表中查找target
## 1 Search in rotated sorted array 
### * description
Suppose a sorted array is rotated at some pivot unknown to you beforehand.
(i.e.,               might become              ).
You are given a target value to search. If found in the array return its index, otherwise return -1. You may assume no duplicate exists in the array.  
### *solution  
分析数据：分界点前后数据都是有序的，可以采用二分法进行查找.（_真值表_）判断mid 处于哪部分。

```python
def search(nums,target) :  
    low = 0
    high = len(nums)-1
    while (low <= high) :
        mid = int(math.floor(low + high)/2)
        if nums[mid] == target :
            return mid
        if nums[l] <= nums[mid] :
            if nums[low]> nums[high] and nums[mid] >target:
                high = mid - 1
            else :
                high = mid -1
        else :
            if nums[high] >= nums[mid] :
                if nums[high] >= target and nums[mid] < target :
                    low = mid + 1
                else :
                    high = mid - 1
    return -1
```

## 2 search in rotated array with duplicates nums
### description
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

Write a function to determine if a given target is in the array.

The array may contain duplicates.  
分析数据：如果存在重复数据，那么mid前后就不一定是有序的了。需要进行情况判断。  

- _如果nums[low] < nums[mid],那么 low与mid 之间可做有序查找_
- _如果nums[low] > nums[mid],那么，low与high之间可做有序查找_
- _如果nums[low] = nums[mid],那么，数组后移_

### solution
```python
 def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: bool
        """
        low = 0
        high = len(nums)-1
        while(low <= high) :
            mid = int(math.floor(low + high)/2)
            if nums[mid] == target :
                return True
            
            if nums[low] < nums[mid] :
                if nums[low] <=target and nums[mid] > target :
                    high = mid -1
                else :
                    low = mid + 1
            elif nums[low] > nums[mid] :
                if nums[high] >=target and nums[mid]< target :
                    low = mid + 1
                else :
                    high = mid -1 
            else :
                low = low + 1
                
        return False
```
