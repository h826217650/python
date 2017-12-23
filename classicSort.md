
#排序算法
## *常见的排序算法及复杂度
![]( /Users/huxiaoyan/Desktop/排序算法.png)

[算法实现](http://wiki.jikexueyuan.com/project/data-structure-sorting/quick-sort.html)
## *归并排序
```python
    
def mergeSort(nums) :
    
	 def mergeSortList(nums1,nums2) :
        i = 0
        j = 0
        nums = []
        while i<len(nums1) and j<len(nums2) :
            if nums[i] < nums[j] :
                nums.append(nums1[i])
                i = i + 1
            else :
                nums.append(nums2[j])
                j = j + 1
        while i < len(nums1) :
            nums.append(nums1[i])
            i = i + 1
        while j < len(nums2) :
            nums.append(nums2[j])
        return nums

	if len(nums) <= 1 :
	    return nums
	k = int(math.floor(l/2))
	left = mergeSort(nums[:k])
	right = mergeSort(nums[k:])
	return MergeSortList(left,right)
```
## *快速排序
分析：  
>_1.选择基准 target = nums[i]_
_2.i=low,j=high. 从j向前找到第一个比target小的值，交互nums[j]与target的位置（nums[i]）_  
_3.i++,向后找第一个比target大的值，交换nums[i]与当前target的位置（nums[j])_   
_4.j--,向前找第二个比target小的值，交换nums[j]与当前target的位置nums[i]_   
_5.i++ 向后找第二个比target大的值....._   
_直到一趟排序后，target前都是比它小的，target后都是比它大的，此时nums[i]就是target的确定位置_。

> * 当一次排序找到一个值后，可分为前后两个部分接着采用上面的方法查找，直到i=j

```python
def FastSort(nums):
    def quickSort(nums,i,j) :
	    target = nums[i] 
	    while i<j :
           if nums[j] < target :
               nums[i],nums[j] = nums[j],nums[i] 
               i = i + 1
           else :
               j = j - 1
           if nums[i] < target :
	            nums[i],nums[j] = nums[j],nums[i]
	            j = j -1
	        else :
	            i = i + 1
	     nums[i] = target // 一次排序后基准值找到确定的位置
	     return i
	       
    int target
    low = 1
    high = len(nums)-1
    if len(nums) <= 1 :
        return nums
    if low < high :
        #对[left,right]进行划分
        target = quickSort(nums,low,high)
        quickSort(nums,low,target-1)
        qucikSort(nums,target+1,high)
    return nums
   
```

## *选择排序
## *堆排序
## *冒泡排序


