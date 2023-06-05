Assignment 5
<br>
<br>
💡 Question 1 Convert 1D Array Into 2D Array <br>

You are given a 0-indexed 1-dimensional (1D) integer array original, and two integers, m and n. You are tasked with creating a 2-dimensional (2D) array with  m rows and n columns using all the elements from original.<br>

The elements from indices 0 to n - 1 (inclusive) of original should form the first row of the constructed 2D array, the elements from indices n to 2 * n - 1 (inclusive) should form the second row of the constructed 2D array, and so on.<br>

Return an m x n *2D array constructed according to the above procedure, or an empty 2D array if it is impossible.<br>

Example 1:<br>

<img src="https://github.com/HardikNarendra/BigData-PPT-Assignments/blob/main/images/ASSIGN-5-Q-1.png" alt="mypic" style="width:500px; height:200px"/><br>

Input: original = [1,2,3,4], m = 2, n = 2<br>

Output: [[1,2],[3,4]]<br>

Explanation: The constructed 2D array should contain 2 rows and 2 columns.<br>

The first group of n=2 elements in original, [1,2], becomes the first row in the constructed 2D array.<br>

The second group of n=2 elements in original, [3,4], becomes the second row in the constructed 2D array.<br>

Solution_code:<br>
```
#question-1
def convert_array(original, m, n):
    if len(original) != m*n: return []
        
    res = [[None for j in range(n)] for i in range(m)]
    k = 0
        
    for i in range(m):
        for j in range(n):
            res[i][j] = original[k]
            k += 1
        
    return res
original = [1,2,3,4]
m = 2
n = 2
print(convert_array(original,m,n))

```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-5> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-5/Assignment/solution.py"
[[1, 2], [3, 4]]
```
<br>
<br>
💡 Question 2  You have n coins and you want to build a staircase with these coins. The staircase consists of k rows where the ith row has exactly i coins. The last row of the staircase may be incomplete.<br>

Given the integer n, return the number of complete rows of the staircase you will build.<br>

Example 1:<br>
<img src="https://github.com/HardikNarendra/BigData-PPT-Assignments/blob/main/images/ASSIGN-5-Q-2.png" alt="mypic" style="width:200px; height:200px"/><br>
Input: n = 5<br>
Output: 2<br>

Explanation: Because the 3rd row is incomplete, we return 2.<br>
Solution_code:<br>
```
#question-2
def arrangeCoins(n):
        completeStairs = 0

        start = 1
        end = (n + 1) // 2
        
        while start <= end:
            mid = start + (end - start) // 2
			# How many coins required to completely fill 'mid' rows?
			# we can use Gauss Summation to find that in O(1) time
            if (mid * ( mid + 1)) // 2 <= n:
                completeStairs = mid
                start = mid + 1
            else:
                end = mid - 1
        return completeStairs
n=5
print(arrangeCoins(n))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-4> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-5/Assignment/solution.py"
2
```
<br>
<br>

💡 Question 3 Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.<br>

Example 1:<br>

Input: nums = [-4,-1,0,3,10]<br>

Output: [0,1,9,16,100]<br>

Explanation: After squaring, the array becomes [16,1,0,9,100].<br>

After sorting, it becomes [0,1,9,16,100].<br>
Solution_code:<br>
```
#question-3
nums = [-4,-1,0,3,10]
for i in range(len(nums)):
    nums[i]=nums[i]**2
nums.sort()
print(nums)
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-4> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-5/Assignment/solution.py"
[0, 1, 9, 16, 100]
```
<br>
<br>

💡 **Question 4**

Given two 0-indexed integer arrays nums1 and nums2, return a list answer of size 2 where:

- answer[0] *is a list of all distinct integers in nums1 which are not present in nums2.
- answer[1] *is a list of all distinct integers in nums2 which are not present in nums1.

Note that the integers in the lists may be returned in any order.

Example 1:

**Input:** nums1 = [1,2,3], nums2 = [2,4,6]

**Output:** [[1,3],[4,6]]

**Explanation:**

For nums1, nums1[1] = 2 is present at index 0 of nums2, whereas nums1[0] = 1 and nums1[2] = 3 are not present in nums2. Therefore, answer[0] = [1,3].

For nums2, nums2[0] = 2 is present at index 1 of nums1, whereas nums2[1] = 4 and nums2[2] = 6 are not present in nums2. Therefore, answer[1] = [4,6].
Solution_code:<br>
```
#question-2
def check_diff(nums1, nums2):
    return list(nums1 - nums2), list(nums2 - nums1)

nums1 = [1, 2, 3] 
nums2 = [2, 4, 6]
ans = []
ans.extend(check_diff(set(nums1), set(nums2)))

# Print the result
print(ans)

```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-5> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-5/Assignment/solution.py"
[[1, 3], [4, 6]]
```
<br>
<br>

💡 **Question 5**

Given two integer arrays arr1 and arr2, and the integer d, *return the distance value between the two arrays*.

The distance value is defined as the number of elements arr1[i] such that there is not any element arr2[j] where |arr1[i]-arr2[j]| <= d.

**Example 1:**

**Input:** arr1 = [4,5,8], arr2 = [10,9,1,8], d = 2

**Output:** 2

**Explanation:**

For arr1[0]=4 we have:

|4-10|=6 > d=2

|4-9|=5 > d=2

|4-1|=3 > d=2

|4-8|=4 > d=2

For arr1[1]=5 we have:

|5-10|=5 > d=2

|5-9|=4 > d=2

|5-1|=4 > d=2

|5-8|=3 > d=2

For arr1[2]=8 we have:

**|8-10|=2 <= d=2**

**|8-9|=1 <= d=2**

|8-1|=7 > d=2

**|8-8|=0 <= d=2**

Solution_code:<br>
```
# question-5
def findTheDistanceValue( arr1, arr2, d):
    arr2.sort()
    distance = len(arr1)
    for num in arr1:
        start = 0
        end = len(arr2) - 1
        while start <= end:
            mid = (start+end)//2
            if abs(num- arr2[mid]) <= d:
                distance -= 1
                break
            elif arr2[mid] > num :
                end = mid-1
            elif arr2[mid] < num :
                start = mid+1
    return distance
arr1 = [4,5,8] 
arr2 = [10,9,1,8]
d = 2
print(findTheDistanceValue(arr1,arr2,d))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-5> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-5/Assignment/solution.py"
2
```
<br>
<br>


💡 **Question 6**

Given an integer array nums of length n where all the integers of nums are in the range [1, n] and each integer appears **once** or **twice**, return *an array of all the integers that appears **twice***.

You must write an algorithm that runs in O(n) time and uses only constant extra space.

**Example 1:**

**Input:** nums = [4,3,2,7,8,2,3,1]

**Output:**

[2,3]

Solution_code:<br>
```
#question-6
def findDuplicates(nums):
    output = []
    for num in nums:
        if nums[abs(num) - 1] < 0:
            output.append(abs(num))
        else:
            nums[abs(num) - 1] *= -1
    return output
nums = [4,3,2,7,8,2,3,1]
print(findDuplicates(nums))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-5> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-5/Assignment/solution.py"
[2, 3]
```
<br>
<br>


💡 **Question 7**

Suppose an array of length n sorted in ascending order is **rotated** between 1 and n times. For example, the array nums = [0,1,2,4,5,6,7] might become:

- [4,5,6,7,0,1,2] if it was rotated 4 times.
- [0,1,2,4,5,6,7] if it was rotated 7 times.

Notice that **rotating** an array [a[0], a[1], a[2], ..., a[n-1]] 1 time results in the array [a[n-1], a[0], a[1], a[2], ..., a[n-2]].

Given the sorted rotated array nums of **unique** elements, return *the minimum element of this array*.

You must write an algorithm that runs in O(log n) time.

**Example 1:**

**Input:** nums = [3,4,5,1,2]

**Output:** 1

**Explanation:**

The original array was [1,2,3,4,5] rotated 3 times.

Solution_code:<br>
```
#question-7
def findMin(nums):
    left, right = 0, len(nums) - 1
    while left < right:
        mid = left + (right - left) // 2
        if nums[mid] > nums[right]:
            left = mid + 1
        else:
            right = mid
    return nums[left]
nums = [3,4,5,1,2]
print(findMin(nums))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-5> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-5/Assignment/solution.py"
1
```
<br>
<br>


💡 **Question 8**

An integer array original is transformed into a **doubled** array changed by appending **twice the value** of every element in original, and then randomly **shuffling** the resulting array.

Given an array changed, return original *if* changed *is a **doubled** array. If* changed *is not a **doubled** array, return an empty array. The elements in* original *may be returned in **any** order*.

**Example 1:**

**Input:** changed = [1,3,4,2,6,8]

**Output:** [1,3,4]

**Explanation:** One possible original array could be [1,3,4]:

- Twice the value of 1 is 1 * 2 = 2.
- Twice the value of 3 is 3 * 2 = 6.
- Twice the value of 4 is 4 * 2 = 8.

Other original arrays could be [4,3,1] or [3,1,4].

Solution_code:<br>
```
#question-8
from collections import Counter
def findOriginalArray(nums):
        ans = [] 
		#answer storing array
        vacans = [] 
		#when we need to return vacant array
        if len(nums)%2:
                return ans
				#when we will have odd number of integer in our input(double array can't be in odd number)
    
        nums.sort()
		#sorting 
        temp = Counter(nums)
		#storing the frequencies
        for i in nums:    
            if temp[i] == 0:  
			#if we have already decreased it's value when we were checking y/2 value, like 2,4 we will remove 4 also when we will check 2 but our iteration will come again on 4.
      
                continue
            else:
                if temp.get(2*i,0) >= 1:
				#if we have both y and y*2, store in our ans array
                    ans.append(i)
					#decrease the frequency of y and y*2
                    temp[2*i] -= 1
                    temp[i] -= 1
                else:        
                    return vacans
        return ans
changed = [1,3,4,2,6,8]
print(findOriginalArray(changed))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-5> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-5/Assignment/solution.py"
[1, 3, 4]
```
<br>
<br>



