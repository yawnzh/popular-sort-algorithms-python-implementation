# popular-sort-algorithms-python-implementation
## Simple Sort
1. Bubble sort
```python
def bubbleSort(nums):
    for i in range(len(nums)):
        changed=False
        for j in range(i+1,len(nums)):
            if nums[i]>nums[j]:
                nums[i],nums[j]=nums[j],nums[i]
                changed=True
        if not changed:
            break
    return nums
```
2. Insertion sort
```python
def insertionSort(nums):
    for i in range(len(nums)):
        target=nums[i]
        j=i-1
        while j>=0 and nums[j]>=target:
            nums[j+1]=nums[j]
            j-=1
        nums[j+1]=target
    return nums
```
3. Selction sort
```python
def selectSort(nums):
    for i in range(len(nums)):
        j=min(range(i,len(nums)),key=lambda x:nums[x])
        nums[i],nums[j]=nums[j],nums[i]
    return nums
```
## Efficient Sort
1. Merge sort
```
def mergeSort(nums):
    if len(nums) <= 1:
        return nums
    mid = len(nums) // 2
    left = mergeSort(nums[:mid])
    right = mergeSort(nums[mid:])
    return merge(left, right)

def merge(*list_of_nums):
    n = sum(map(len, list_of_nums))
    res = [None]*n
    while n > 0:
        x = max((x for x in list_of_nums),key=lambda x:x[-1] if x else -float('inf'))
        res[n-1]=x.pop()
        n -= 1
    return res
```
2. Heap sort
```
def heapSort(nums):
    end=len(nums)-1
    heapify(nums,end)
    while end>0:
        nums[0],nums[end]=nums[end],nums[0]
        end-=1
        siftDown(nums,0,end)

def heapify(nums,end):
    start=iParent(end)
    for i in range(start,-1,-1):
        siftDown(nums,i,end)

def siftDown(nums,start,end):
    root=start
    while iLeft(root)<=end:
        child=iLeft(root)
        swap=root
        if nums[swap]<nums[child]:
            swap=child
        if child+1<=end and nums[child+1]>nums[swap]:
            swap=child+1
        if swap==root:
            return
        else:
            nums[swap],nums[root]=nums[root],nums[swap]
            root=swap

def iParent(i):
    return (i+1)//2-1

def iLeft(i):
    return 2*i+1
```
3. Quick sort
```python
def quickSort(nums):
    _quickSort(nums,0,len(nums)-1)
    return nums
    
def _quickSort(nums,start,end):
    if start>=end:
        return
    pi=random.randint(start,end)
    nums[start],nums[pi]=nums[pi],nums[start]
    i=start+1
    j=end
    while i<=j:
        if nums[i]>nums[start]:
            nums[i],nums[j]=nums[j],nums[i]
            j-=1
        else:
            i+=1
    nums[start],nums[i-1]=nums[i-1],nums[start]
    _quickSort(nums,start,i-2)
    _quickSort(nums,i,end)
```
    
                
