## twoSum

【方法一】
> 把list转换为dictionary
>> 获取target与元素差值
>>>从dictionary中判断是否存在该值

```
def twoSum(nums,target):
    num1=[]
    for i in range(len(nums)):
        num1.append(i)
    dnum = dict(zip(nums,num1))
    for key in dnum:
        t = target-key
        if t in dnum:
            return dnum[key],dnum[t]
```

【方法二】
> 先不生成dictionary，依次遍历某个元素
>> 获取某元素与target的差值
>>> 判断差值是否dictionary中
>>>> 如不存在，把某元素及对应index写入dictionary
>>>>>如果存在，则从dict中取该值的索引

 
```
class Solution :
    def twoSum(self, nums, target):
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


【方法三】
>  采用两边逼近的方法 --  必须是有序序列
> > 从第一个与最后一个开始判断：如果和大于target，则后面的元素前移；如果和小于target则前面的元素后移；直到和等于target
> > > 但是要找到排序之前的index，则需要通过通过list来遍历取得排序前list 某值的index，采用 enumerate函数，实现对list的遍历。
>
>  从该题中，需掌握
>> 1 变量的作用阈
>>> 2 循环 or 代码块执行条件的设置
>>>> 3 flag的使用（初始值为-1）

```
def twoSum(nums, target) :
    nums1 = sorted(nums)
        i = 0
        j = len(nums1) - 1
        while(j > i) :
            if nums1[i] + nums1[j] > target :
                j = j - 1
            elif nums1[i] + nums1[j] < target :
                i = i + 1
            else :
                break
                
        if(j > i) :
            index1 = -1
            index2 = -1
            for index, num in enumerate(nums) :
                if num == nums1[i] and index1 == -1 :
                    index1 = index
                    continue
                if num == nums1 [j] and index2 == -1 :
                    index2 = index
            return index1, index2
```

##【总结】
算法题思维：
`1.全面思考问题，scale 数据量、数据范围（数据范围没有说的话要问） `
`2.corner case想清楚（设计测试用例）`
`3.思考所有可能的解法（鼓励在白板上列出）`
`4.分析比较每个解法的优劣（易写程度、时间、空间复杂度）`
