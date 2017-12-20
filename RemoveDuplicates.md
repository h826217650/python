# Remove from sorted array
## 1 Remove Duplicates from Sorted Array

### *description
Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.Do not allocate extra space for another array, you must do this in place with constant memory.For example, Given input array            ,Your function should return length = 2, and A is now 
### * solution
```
 def removeElement(nums) :  
  	l = 1  
  	if len(nums) <1 :  
  	   return -1
  	
  	for i in range(len(nums)-1) :  
  		if nums[i]!=nums[i+1] :  
  			nums[l]= nums[i+1]
  			l = l + 1  
  			
  	return l
```
## 2 Remove Duplicates from Sorted Array
### *description
Follow up for ”Remove Duplicates”: What if duplicates are allowed at most twice? For example, Given sorted array                  ,Your function should return length = 5, and A is now            ### *solution  
使用count来标识元素出现的次数，如果count=1，则出现一次写入nums[l] ; 否则跳过。如果没有重复性的数值同样写入nums[l]。如果是未排序的数组，需引入hashmap 记录出现的次数。

```
def removeElement()


def removeElement(nums) :
	count = 0
	l = 1
	for i in range(len(nums)-1) :
		if nums[i] == nums[i+1] :
			coount = count +1
			if count == 1	:
				nums[l] = nums[i+1]
		else :
			count = 0
			nums[l] = nums[i+1]
			l = l + 1
	return l
			
``` 



  	
  		
  	
  	
  	 
  	