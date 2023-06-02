Assignment 3 Questions <br>

💡 Question 1 Given an integer array nums of length n and an integer target, find three integers in nums such that the sum is closest to the target. Return the sum of the three integers.<br>
You may assume that each input would have exactly one solution.<br>
Example 1: Input: nums = [-1,2,1,-4], target = 1 <br>
Output: 2<br>
Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).<br>

Solution:<br>
```
#question-1 3Sum problem using 2 pointers approach
def threeSumClosest(nums, target):
    nums.sort()
    n=len(nums)
    closest_sum=nums[0]+nums[1]+nums[2]
    for i in range(0,n-2):
        left = i+1
        right = n-1
        while left < right:
            sum = nums[i] + nums[left] + nums[right]
            if sum== target:
                return sum
            elif sum < target:
                left += 1
            else:
                right -=1
            if abs(sum - target) < abs(closest_sum - target):
                closest_sum = sum
    return closest_sum

nums = [-1,2,1,-4]
target = 1 
print(threeSumClosest(nums,target))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-3> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-3/Assignment/solution.py"
2
```
<br>
<br>
💡 Question 2 Given an array nums of n integers, return an array of all the unique quadruplets [nums[a], nums[b], nums[c], nums[d]] such that:<br>
● 0 <= a, b, c, d < n <br>
● a, b, c, and d are distinct. <br>
● nums[a] + nums[b] + nums[c] + nums[d] == target<br>
You may return the answer in any order.<br>
Example 1: Input: nums = [1,0,-1,0,-2,2], target = 0<br>
 Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]<br>

Solution:<br>
```
#question-2
# Store the pair of indices
class Pair:
	def __init__(self, x, y):
		self.index1 = x
		self.index2 = y

# Function to find the all the unique quadruplets
# with the elements at different indices
def GetQuadruplets(nums, target):
	# Store the sum mapped to a list of pair indices
	map = {}

	# Generate all possible pairs for the map
	for i in range(len(nums) - 1):
		for j in range(i + 1, len(nums)):
			# Find the sum of pairs of elements
			sum = nums[i] + nums[j]

			# If the sum doesn't exist then update with the new pairs
			if sum not in map:
				map[sum] = [Pair(i, j)]
			# Otherwise, add the new pair of indices to the current sum
			else:
				map[sum].append(Pair(i, j))

	# Store all the Quadruplets
	ans = set()

	for i in range(len(nums) - 1):
		for j in range(i + 1, len(nums)):
			lookUp = target - (nums[i] + nums[j])

			# If the sum with value (K - sum) exists
			if lookUp in map:
				# Get the pair of indices of sum
				temp = map[lookUp]

				for pair in temp:
					# Check if i, j, k and l are distinct or not
					if pair.index1 != i and pair.index1 != j and pair.index2 != i and pair.index2 != j:
						l1 = [nums[pair.index1], nums[pair.index2], nums[i], nums[j]]
						
						# Sort the list to avoid duplicacy
						l1.sort()
						
						# Update the set
						ans.add(tuple(l1))

	# Print all the Quadruplets
	print(*reversed(list(ans)), sep = '\n')

# Driver Code
arr = [1, 0, -1, 0, -2, 2]
K = 0
GetQuadruplets(arr, K)

```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-3> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-3/Assignment/solution.py"
(-2, 0, 0, 2)
(-1, 0, 0, 1)
(-2, -1, 1, 2)
```
<br>
<br>
💡 Question 3 A permutation of an array of integers is an arrangement of its members into a sequence or linear order.<br>
For example, for arr = [1,2,3], the following are all the permutations of arr: [1,2,3], [1,3,2], [2, 1, 3], [2, 3, 1], [3,1,2], [3,2,1].<br>
The next permutation of an array of integers is the next lexicographically greater permutation of its integer. More formally, if all the permutations of the array are sorted in one container according to their lexicographical order, then the next permutation of that array is the permutation that follows it in the sorted container.
If such an arrangement is not possible, the array must be rearranged as the lowest possible order (i.e., sorted in ascending order).<br>
● For example, the next permutation of arr = [1,2,3] is [1,3,2].<br>
 ● Similarly, the next permutation of arr = [2,3,1] is [3,1,2]. <br>
● While the next permutation of arr = [3,2,1] is [1,2,3] because [3,2,1] does not have a lexicographical larger rearrangement.<br>
Given an array of integers nums, find the next permutation of nums. The replacement must be in place and use only constant extra memory.<br>
Example 1: <br>
Input: nums = [1,2,3] <br>
Output: [1,3,2]<br>

Solution:<br>
```
#question-3
def nextPermutation(nums):
        for i in range(len(nums)-1, 0, -1):
            # find the index of the last peak
            if nums[i - 1] < nums[i]:
                nums[i:] = sorted(nums[i:])
                
                # get the index before the last peak
                j = i - 1
                
                # swap the pre-last peak index with the value just large than it
                for k in range(i, len(nums)):
                    if nums[j] < nums[k]:
                        nums[k], nums[j] = nums[j], nums[k]
                        return nums
        return nums.reverse()
nums = [1,2,3] 
print(nextPermutation(nums))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-3> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-3/Assignment/solution.py"
[1, 3, 2]
```
<br>
<br>
💡 Question 4 Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.<br>
You must write an algorithm with O(log n) runtime complexity.<br>
Example 1:<br>
 Input: nums = [1,3,5,6], target = 5<br>
 Output: 2<br>

Solution:<br>
```
#question-4
def searchInsert(nums, target):
    l = 0
    r = len(nums) - 1
    while l <= r:
        mid = (l + r) // 2
        if nums[mid] < target:
            l = mid + 1
        elif nums[mid] > target:
            r = mid - 1
        else:
            return mid
    return l
        
nums = [1,3,5,6]
target = 5
print(searchInsert(nums,target))

```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-3> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-3/Assignment/solution.py"

2
```
<br>
<br>
💡 Question-5 You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.<br>
Increment the large integer by one and return the resulting array of digits.<br>
Example 1: Input: digits = [1,2,3] <br>
Output: [1,2,4]<br>
Explanation: The array represents the integer 123. Incrementing by one gives 123 + 1 = 124. Thus, the result should be [1,2,4].<br>

Solution:<br>
```
# Question-5
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
/OneDrive/Desktop/PPT program/lecture-3/Assignment-3/solution-code.py"
[1, 2, 4]
```
<br>
<br>
💡 Question 6 Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.<br>
You must implement a solution with a linear runtime complexity and use only constant extra space.<br>
Example 1: <br>
Input: nums = [2,2,1] <br>
Output: 1

Solution:<br>
```
#question-6
# Python code to find the array element that appears only once
def findSingle(A, ar_size):
	
	# iterate over every element
	for i in range(ar_size):
		
		# Initialize count to 0
		count = 0
		for j in range(ar_size):
			
			# Count the frequency
			# of the element
			if(A[i] == A[j]):
				count += 1

		# If the frequency of
		# the element is one
		if(count == 1):
			return A[i]
			
	# If no element exist
	# at most once
	return -1

nums = [2,2,1]
n = len(nums)

print(findSingle(nums, n))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-3> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-3/Assignment/solution.py"

1
```
<br>
<br>
💡 Question 7 You are given an inclusive range [lower, upper] and a sorted unique integer array nums, where all elements are within the inclusive range.
A number x is considered missing if x is in the range [lower, upper] and x is not in nums.
Return the shortest sorted list of ranges that exactly covers all the missing numbers. That is, no element of nums is included in any of the ranges, and each missing number is covered by one of the ranges.
Example 1:
 Input: nums = [0,1,3,50,75], lower = 0, upper = 99 
Output: [[2,2],[4,49],[51,74],[76,99]]
Explanation: The ranges are:
 [2,2]
 [4,49] 
[51,74] 
[76,99]

Solution:<br>
```
#question-7
from itertools import pairwise


def findMissingRanges( nums, lower, upper):
    def f(a, b):
         return str(a) if a == b else f'{a}->{b}'

    n = len(nums)
    if n == 0:
        return [f(lower, upper)]
    ans = []
    if nums[0] > lower:
        ans.append(f(lower, nums[0] - 1))
    for a, b in pairwise(nums):
        if b - a > 1:
            ans.append(f(a + 1, b - 1))
    if nums[-1] < upper:
        ans.append(f(nums[-1] + 1, upper))
    return ans
nums = [0,1,3,50,75]
lower = 0
upper = 99
print(findMissingRanges(nums,lower,upper))

```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-3> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-3/Assignment/solution.py"

['2', '4->49', '51->74', '76->99']
```
<br>
<br>
💡 Question 8 Given an array of meeting time intervals where intervals[i] = [starti, endi], determine if a person could attend all meetings.<br>
Example 1:<br>
 Input: intervals = [[0,30],[5,10],[15,20]]<br>
 Output: false<br>

 Solution:<br>
 ```
 #question-8
def canAttendMeetings(intervals):
        
    intervals.sort(key=lambda a: a[1])
    for i in range(len(intervals)-1):
        if intervals[i][1] > intervals[i+1][0]:
            return False
    return True
intervals = [[0,30],[5,10],[15,20]]
print(canAttendMeetings(intervals))
 ```
 Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-3> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-3/Assignment/solution.py"

False
```

