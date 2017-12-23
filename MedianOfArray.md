# 1 Median of Two Sorted Arrays
## *description
There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

## solution1
分析: 把两个有序列表合并后，进行第k个值的查找

```python

def findMediaFromArrays(nums1,nums2) :  

    i = 0
    j = 0
    nums =[]
    k = int((len(nums1) + len(nums2))/2)
    while(i < len(nums1) and j < len(nums2)) :
        if nums1[i] < nums2[j] :
            nums.append(nums1[i])
            i = i + 1
        else :
            nums.append(nums2[j])
            j = j + 1
    while(i < len(nums1)) :
        nums.append(nums1[i])
        i = i + 1
    while(j < len(nums2)) :
        nums.append(nums2[j])
        j = j + 1
    if ((len(nums1) + len(nums2)) & 0x1) :
        media = float((nums[mid] + nums[mid - 1])/2)
    else :
    	  media = float(nums[mid])
    return media
```
## solution2
分析：上面解法的时间复杂度为O(m+n),空间复杂度为 m+n.可以进第一步优化空间复杂度为o(1)
不借助第三方list，通过count判断是否是第k个数即可。

## solution3
分析：上面解法的时间复杂度为O(m+n),空间复杂度为m+n
题要求时间负责度为O(log(m+n)),所以可以采用“二分舍弃”的方法实现。要求找的是第K个数，那么如果每次都可以删除一定在第K个之前的元素，那么只需要比较K次。当nums1 nums2有序时，可以利用类似二分查找的方法。找第K个数，可以进行nums1[k/2-1] 与 nums2[k/2-1] 进行比较。  
_1. 如果nums1[k/2-1] < nums2[k/2-1],则第k个数一定不在nums1[0:k/2-1]里面，可舍弃该部分_
_2. 如果nums1[k/2-1] > nums2[k/2-1],则第k个数一定不在nums2[0:k/2-1]里面，可舍弃该部分_
_3. 如果nums1[k/2-1] = nums2[k/2-1],则直接返回nums1[k/2-1] or nums2[k/2-1]_



```python
def findMedianSortedArrays(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: float
        """
        m = len(nums1)
        n = len(nums2)
        k = int(math.floor((m + n) / 2))
        def findK(A, startA, m, B, startB, n, k) :
            if (m > n) :
                return findK(B, startB, n, A, startA, m, k)
            if (m == 0) :
                return B[startB + k -1]
            if (k == 1) :
                return min(A[startA], B[startB])


            lenA = min(int(k / 2), m)
            lenB = k - lenA
            if (A[startA + lenA - 1] < B[startB + lenB - 1]) :
                return findK(A, startA + lenA, m - lenA,B, startB, n, k - lenA)
            elif (A[startA + lenA - 1] > B[startB + lenB - 1]) :
                return findK(A, startA, m, B, startB + lenB,n -lenB, k - lenB)
            else :
                return A[lenA - 1]


        if ((m + n) & 0x1) :
            return float(findK(nums1, 0, m, nums2, 0, n, k+1 ))
        else :
            return float(findK(nums1, 0, m, nums2, 0, n, k ) + findK(nums1, 0, m, nums2, 0,n, k + 1) )/ 2
        
	
```  
⚠️ if((m + n) &0x1) 即长度为奇数时，中位数是第k+1个。否则，中位数是第k 与第k+1的均值 

# 2 递归

 





