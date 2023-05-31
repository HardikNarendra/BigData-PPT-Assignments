
💡 Q1. Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.<br>

You may assume that each input would have exactly one solution, and you may not use the same element twice.<br>

You can return the answer in any order.<br>
<br>
<br>
Example:<br>
Input: nums = [2,7,11,15], target = 9<br>
Output0 [0,1]<br>

Explanation: Because nums[0] + nums[1] == 9, we return [0, 1]<br>

Solution:<br>
```
#  Question-1
arr=[2,7,11,15]
target=9
n=len(arr)
def two_sum(arr,target,n):
    for i in range(0,n):
        for j in range(i+1,n):
            sumation = arr[i] + arr[j]
            if sumation == target:
                loc1 = i
                loc2 = j
                return [loc1,loc2]
print(two_sum(arr,target,n))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-1\Assignment-1> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-1/Assignment-1/solution-code.py"
[0, 1]
```
<br>
<br>
💡 Q2. Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.<br>
Consider the number of elements in nums which are not equal to val be k, to get accepted, you need to do the following things:<br>
•	Change the array nums such that the first k elements of nums contain the elements which are not equal to val. The remaining elements of nums are not important as well as the size of nums.<br>
•	Return k.<br>
Example : Input: nums = [3,2,2,3], val = 3 Output: 2, nums = [2,2,*,*]<br>
Explanation: Your function should return k = 2, with the first two elements of nums being 2. It does not matter what you leave beyond the returned k (hence they are underscores)<br>

Solution:<br>
```
#Question2
nums = [3,2,2,3]
val = 3
# function to remove element
def remove_element(nums,val):
    k=0
    # for loop to count the number of elements not equal to val 
    for i in range(len(nums)):
        if nums[i] != val:
            nums[k]=nums[i]
            k += 1
    
    #for loop for putting underscore for the rest of the elements in nums
    for i in range(k,len(nums)):
        nums[i]='_'

    return k,nums

k,new_nums = remove_element(nums,val)
print("k: ",k)
print("nums: ",nums)
```

Output:<br>
```
/OneDrive/Desktop/PPT program/lecture-1/Assignment-1/solution-code.py"
k:  2
nums:  [2, 2, '_', '_']
```
<br>
<br>
💡 Q3. Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.<br>
You must write an algorithm with O(log n) runtime complexity.<br>

Example 1: Input: nums = [1,3,5,6], target = 5 <br>
Output: 2

Solution:<br>
```
# function to find the position of target
def find_element_index(nums, target):
 
    # set the Lower and upper bounds
    n=len(nums)
    start = 0
    end = n - 1
 
    # traversing
    while start<= end:
 
        mid =(start + end)//2
 
        if nums[mid] == target:
            return mid
 
        elif nums[mid] < target:
            start = mid + 1
        else:
            end = mid-1
 
    # Return the insert position
    return end + 1
 
# Driver Code
nums = [1, 3, 5, 6]
target = 5
print(find_element_index(nums, target))
```

Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-1\Assignment-1> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-1/Assignment-1/solution-code.py"
2
```
<br>
<br>
💡 Q4. You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.<br>
Increment the large integer by one and return the resulting array of digits.<br>
Example 1: Input: digits = [1,2,3] <br>
Output: [1,2,4]<br>
Explanation: The array represents the integer 123.<br>
Incrementing by one gives 123 + 1 = 124. Thus, the result should be [1,2,4]<br>

Solution:<br>
```
# Question-4 
digits = [1,2,3]
str1=str()

for i in digits:
    str1 += str(i) 

add=int(str1)+1
list1=[int(i) for i in str(add)]
print(list1)
```

Output:<br>
```
/OneDrive/Desktop/PPT program/lecture-1/Assignment-1/solution-code.py"
[1, 2, 4]
```
<br>
<br>
💡 Q5. You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.<br>
Merge nums1 and nums2 into a single array sorted in non-decreasing order.<br>
The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.<br>
Example 1: Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3 <br>
Output: [1,2,2,3,5,6]<br>
Explanation: The arrays we are merging are [1,2,3] and [2,5,6]. The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.<br>

Solution:<br>
```
def merge(nums1, m, nums2, n):
    i = m - 1
    j = n - 1
    k = m + n - 1
        
    while j >= 0:
        if i >= 0 and nums1[i] > nums2[j]:
            nums1[k] = nums1[i]
            i -= 1
        else:
            nums1[k] = nums2[j]
            j -= 1
        k -= 1
    return nums1
nums1 = [1,2,3,0,0,0]
m = 3
nums2 = [2,5,6]
n = 3
print(merge(nums1, m, nums2, n))
```
Output:<br>
```
Desktop/PPT program/lecture-1/Assignment-1/solution-code.py"
[1, 2, 2, 3, 5, 6]
```
<br>
<br>
Q6. Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.<br>
Example 1: Input: nums = [1,2,3,1]<br>
Output: true<br>

Solution:<br>
```
#using set
set1=set()
nums = [1,2,3,1]
for i in nums:
    if i in set1:
        print('true')
        break
    else:
        set1.add(i)
if len(set1) == len(nums):
    print('false')
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-1\Assignment-1> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-1/Assignment-1/solution-code.py"
true
```
<br>
<br>
Q7. Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the nonzero elements.
Note that you must do this in-place without making a copy of the array.<br>
Example 1: <br>
Input: nums = [0,1,0,3,12] <br>
Output: [1,3,12,0,0]<br>

Solution:<br>
```
#Question-7
nums = [0,1,0,3,12]
j=0
for i in range(len(nums)):
    if nums[i] != 0:
       nums[i],nums[j]=nums[j],nums[i]
       j+=1
print(nums)
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-1\Assignment-1> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-1/Assignment-1/solution-code.py"
[1, 3, 12, 0, 0]
```
<br>
<br>
Q8. You have a set of integers s, which originally contains all the numbers from 1 to n. Unfortunately, due to some error, one of the numbers in s got duplicated to another number in the set, which results in repetition of one number and loss of another number.
You are given an integer array nums representing the data status of this set after the error.<br>
Find the number that occurs twice and the number that is missing and return them in the form of an array.<br>
Example 1:<br>
 Input: nums = [1,2,2,4] <br>
Output: [2,3]<br>

Solution:<br>
```
def findErrorNums(nums):
    s,n=set(nums),len(nums)
    for i in range(1,n+1):
        if i not in s:
            t=i
            break
    s1=sum(nums)
    s2=(n*(n+1))//2
    d=s2-s1
    return t-d,t
nums = [1,2,2,4]
print(list(findErrorNums(nums)))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-1\Assignment-1> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-1/Assignment-1/solution-code.py"
[2, 3]
```

