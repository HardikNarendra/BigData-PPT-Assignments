Assignment Questions 2
<br>
<br>
💡 Question 1 Given an integer array nums of 2n integers, group these integers into n pairs (a1, b1), (a2, b2),..., (an, bn) such that the sum of min(ai, bi) for all i is maximized. Return the maximized sum.<br>
Example 1: Input: nums = [1,4,3,2]<br>
 Output: 4<br>
Explanation: All possible pairings (ignoring the ordering of elements) are:<br>
1.	(1, 4), (2, 3) -> min(1, 4) + min(2, 3) = 1 + 2 = 3
2.	(1, 3), (2, 4) -> min(1, 3) + min(2, 4) = 1 + 2 = 3
3.	(1, 2), (3, 4) -> min(1, 2) + min(3, 4) = 1 + 3 = 4 <br>
So the maximum possible sum is 4 <br>

Solution:<br>
```
nums=[1,4,3,2]
max_sum=0
nums.sort()
for i,n in enumerate(nums):
    if i%2 == 0:
        max_sum += n
print(max_sum)
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-2> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-2/Assignment-2/solution.py"
4
```
<br>
<br>
💡 Question 2 Alice has n candies, where the ith candy is of type candyType[i]. Alice noticed that she started to gain weight, so she visited a doctor.<br>
The doctor advised Alice to only eat n / 2 of the candies she has (n is always even). Alice likes her candies very much, and she wants to eat the maximum number of different types of candies while still following the doctor's advice.<br>
Given the integer array candyType of length n, return the maximum number of different types of candies she can eat if she only eats n / 2 of them.<br>
Example 1: Input: candyType = [1,1,2,2,3,3] <br>
Output: 3<br>
Explanation: Alice can only eat 6 / 2 = 3 candies. Since there are only 3 types, she can eat one of each type.<br>

Solution:<br>
```
#question-2
#we can use hashset
candyType=[1,1,2,2,3,3]
hash=set(candyType)
uniq_candies=len(hash)
print(min(uniq_candies,len(candyType)//2))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-2> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-2/Assignment-2/solution.py"
3
```
<br>
<br>
💡 Question 3 We define a harmonious array as an array where the difference between its maximum value and its minimum value is exactly 1.<br>
Given an integer array nums, return the length of its longest harmonious subsequence among all its possible subsequences.<br>
A subsequence of an array is a sequence that can be derived from the array by deleting some or no elements without changing the order of the remaining elements.<br>
Example 1: Input: nums = [1,3,2,2,5,2,3,7]<br>
 Output: 5<br>
Explanation: The longest harmonious subsequence is [3,2,2,2,3].<br>

Solution:<br>
```
# question-3
nums=[1,3,2,2,5,2,3,7]
freq = {}
for num in nums:
    freq[num] = freq.get(num, 0) + 1
max_length = 0
for num in freq:
    if num + 1 in freq:
        max_length = max(max_length, freq[num] + freq[num + 1])
print(max_length)

```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-2> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-2/Assignment-2/solution.py"
5
```
<br>
<br>
💡 Question 4 You have a long flowerbed in which some of the plots are planted, and some are not. However, flowers cannot be planted in adjacent plots. Given an integer  array flowerbed containing 0's and 1's, where 0 means empty and 1 means not empty, and an integer n, return true if n new flowers can be planted in the flowerbed without violating the no-adjacent-flowers rule and false otherwise.<br>
Example 1: Input: flowerbed = [1,0,0,0,1], n = 1<br>
 Output: true<br>

Solution:<br>
```
# question-4
flowerbed = [1,0,0,0,1]
n=1
def place_flower(flowerbed,n):
    count = 0
    i = 0
    while i < len(flowerbed):
        if flowerbed[i] == 0 and (i == 0 or flowerbed[i-1] == 0) and (i == len(flowerbed)-1 or flowerbed[i+1] == 0):
            flowerbed[i] = 1
            count += 1
        if count >= n:
            return True
        i += 1
    return False
print(place_flower(flowerbed,n))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-2> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-2/Assignment-2/solution.py"
True
```
<br>
<br>
💡 Question 5 Given an integer array nums, find three numbers whose product is maximum and return the maximum product.<br>
Example 1: Input: nums = [1,2,3] <br>
           Output: 6<br>

Solution:<br>
```
#question-5
nums = [1,2,3] 
nums.sort()
print(max(nums[0]*nums[1]*nums[-1],nums[-1]*nums[-2]*nums[-3]))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-2> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-2/Assignment-2/solution.py"
6
```
<br>
<br>
💡 Question 6 Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.<br>
You must write an algorithm with O(log n) runtime complexity.<br>
Input: nums = [-1,0,3,5,9,12], target = 9 <br>
Output: 4<br>
Explanation: 9 exists in nums and its index is 4<br>

Solution:<br>
```
#question-6
#use binary search
def binary_search(nums,target):
    left = 0
    right = len(nums)-1
    
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

nums=[-1,0,3,5,9,12]
target = 9 
print(binary_search(nums,target))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-2> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-2/Assignment-2/solution.py"
4
```
<br>
<br>
💡 Question 7 An array is monotonic if it is either monotone increasing or monotone decreasing.<br>
An array nums is monotone increasing if for all i <= j, nums[i] <= nums[j]. An array nums is monotone decreasing if for all i <= j, nums[i] >= nums[j].<br>
Given an integer array nums, return true if the given array is monotonic, or false otherwise.<br>
Example 1: Input: nums = [1,2,2,3] <br>
Output: true<br>

Solution:<br>
```
#question-7
def isMonotonic(nums):
    inc = True
    dec = True
    for i in range(len(nums)-1):
        if nums[i] > nums[i+1]:
            inc = False
                
        if nums[i] < nums[i+1]:
            dec = False
    return inc or dec
nums = [1,2,2,3] 
print(isMonotonic(nums))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-2> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-2/Assignment-2/solution.py"
True
```
<br>
<br>
💡 Question 8 You are given an integer array nums and an integer k.<br>
In one operation, you can choose any index i where 0 <= i < nums.length and change nums[i] to nums[i] + x where x is an integer from the range [-k, k]. You can apply this operation at most once for each index i.<br>
The score of nums is the difference between the maximum and minimum elements in nums.<br>
Return the minimum score of nums after applying the mentioned operation at most once for each index in it.<br>
Example 1: Input: nums = [1], k = 0 <br>
Output: 0<br>
Explanation: The score is max(nums) - min(nums) = 1 - 1 = 0.<br>

Solution:<br>
```
#question-8
def max_min(nums,k):
    return max(0, max(nums) - min(nums) - 2 * k)
nums = [1]
k = 0 
print(max_min(nums,k))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-2> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-2/Assignment-2/solution.py"
0
```
<br>
<br>

