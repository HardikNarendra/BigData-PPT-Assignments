Assignment Questions 4<br>
<br>
<br>
💡 Question 1 Given three integer arrays arr1, arr2 and arr3 sorted in strictly increasing order, return a sorted array of only the integers that appeared in all three arrays.<br>
Example 1:<br>
Input: arr1 = [1,2,3,4,5], arr2 = [1,2,5,7,9], arr3 = [1,3,4,5,8]<br>
Output: [1,5]<br>
Explanation: Only 1 and 5 appeared in the three arrays.<br>

Solution_code:<br>
```
#question-1
#using set intersection
def find_com(arr1,arr2,arr3):
    set1=set(arr1)
    set2=set(arr2)
    set3=set(arr3)
    return list(set1 & set2 & set3)

#driver code
arr1 = [1,2,3,4,5]
arr2 = [1,2,5,7,9]
arr3 = [1,3,4,5,8]
print(find_com(arr1,arr2,arr3))

```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-4> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-4/Assignment/solution.py"
[1, 5]
```
<br>
<br>
💡 Question 2  Given two 0-indexed integer arrays nums1 and nums2, return a list answer of size 2 where:<br>
•	answer[0] is a list of all distinct integers in nums1 which are not present in nums2*.*<br>
•	answer[1] is a list of all distinct integers in nums2 which are not present in nums1.<br>
Note that the integers in the lists may be returned in any order.<br>
Example 1:<br>
Input: nums1 = [1,2,3], nums2 = [2,4,6]<br>
Output: [[1,3],[4,6]]<br>
Explanation:<br>
For nums1, nums1[1] = 2 is present at index 0 of nums2, whereas nums1[0] = 1 and nums1[2] = 3 are not present in nums2. Therefore, answer[0] = [1,3].<br>
For nums2, nums2[0] = 2 is present at index 1 of nums1, whereas nums2[1] = 4 and nums2[2] = 6 are not present in nums2. Therefore, answer[1] = [4,6].<br>

Solution_code:<br>
```
#question-2
#we can use set difference
def set_diff(nums1,nums2,answer):
    
    answer.append(list(nums1-nums2))
    answer.append(list(nums2-nums1))
    
    return answer
    
#driver code
nums1 = [1,2,3]
nums2 = [2,4,6]
answer=[]
print(set_diff(set(nums1),set(nums2),answer))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-4> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-4/Assignment/solution.py"
[[1, 3], [4, 6]]
```
<br>
<br>
💡 Question 3 Given a 2D integer array matrix, return the transpose of matrix.<br>
The transpose of a matrix is the matrix flipped over its main diagonal, switching the matrix's row and column indices.<br>
Example 1:<br>
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]<br>
Output: [[1,4,7],[2,5,8],[3,6,9]]<br>

<img src="https://github.com/HardikNarendra/BigData-PPT-Assignments/blob/main/images/ASSIGN-4-Q-3.png" alt="mypic" style="width:500px; height:200px"/><br>

Solution_code:<br>
```
#question-3
#transpose of a matrix
def transpose(matrix,m,n):
    ans = [[None] * m for _ in range(n)]
    for i in range(m):
        for j in range(n):
            ans[i][j]=matrix[j][i]
    return ans
matrix = [[1,2,3],[4,5,6],[7,8,9]]
n=len(matrix[0])
m=len(matrix)
print(transpose(matrix,m,n))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-4> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-4/Assignment/solution.py"
[[1, 4, 7], [2, 5, 8], [3, 6, 9]]
```
<br>
<br>
💡 Question 4 Given an integer array nums of 2n integers, group these integers into n pairs (a1, b1), (a2, b2), ..., (an, bn) such that the sum of min(ai, bi) for all i is maximized. Return the maximized sum.<br>
Example 1:<br>
Input: nums = [1,4,3,2]<br>
Output: 4<br>
Explanation: All possible pairings (ignoring the ordering of elements) are:<br>
1.	(1, 4), (2, 3) -> min(1, 4) + min(2, 3) = 1 + 2 = 3<br>
2.	(1, 3), (2, 4) -> min(1, 3) + min(2, 4) = 1 + 2 = 3<br>
3.	(1, 2), (3, 4) -> min(1, 2) + min(3, 4) = 1 + 3 = 4<br>
So the maximum possible sum is 4.<br>

Solution_code:<br>
```
#question-4
def arrayPairSum(nums):
        nums.sort()
        result = 0
        numsLen = len(nums)
        for i in range(0, numsLen - 1, 2):
            result += nums[i]
        return result
nums = [1,4,3,2]
print(arrayPairSum(nums))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-4> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-4/Assignment/solution.py"
4
```
<br>
<br>

💡 Question 5 You have n coins and you want to build a staircase with these coins. The staircase consists of k rows where the ith  row has exactly i coins. The last row of the staircase may be incomplete.<br>
Given the integer n, return the number of complete rows of the staircase you will build.<br>
Example 1:<br>
<img src="https://github.com/HardikNarendra/BigData-PPT-Assignments/blob/main/images/ASSIGN-4-Q-5.jpg" alt="mypic" style="width:200px; height:200px"/><br>
Input: n = 5<br>
Output: 2<br>
Explanation: Because the 3rd row is incomplete, we return 2.<br>

Solution_code:<br>
```
#question-5
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
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-4> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-4/Assignment/solution.py"
2
```
<br>
<br>
💡 Question 6 Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.<br>
Example 1:<br>
Input: nums = [-4,-1,0,3,10]<br>
Output: [0,1,9,16,100]<br>
Explanation: After squaring, the array becomes [16,1,0,9,100]. After sorting, it becomes [0,1,9,16,100]<br>

Solution_code:<br>
```
#question-6
nums = [-4,-1,0,3,10]
for i in range(len(nums)):
    nums[i]=nums[i]**2
nums.sort()
print(nums)
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-4> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-4/Assignment/solution.py"
[0, 1, 9, 16, 100]
```
<br>
<br>
💡 Question 7 You are given an m x n matrix M initialized with all 0's and an array of operations ops, where ops[i] = [ai, bi] means M[x][y] should be incremented by one for all 0 <= x < ai and 0 <= y < bi.<br>
Count and return the number of maximum integers in the matrix after performing all the operations<br>
Example 1:<br>
<img src="https://github.com/HardikNarendra/BigData-PPT-Assignments/blob/main/images/ASSIGN-4-Q-7.jpg" alt="mypic" style="width:700px; height:200px"/><br>
Input: m = 3, n = 3, ops = [[2,2],[3,3]]<br>
Output: 4<br>
Explanation: The maximum integer in M is 2, and there are four of it in M. So return 4.<br>

Solution_code:<br>
```
#question-7
def maxCount( m, n, ops):
        for r,c in ops:
            # expand and shrink the matrix size (bottom-right boundry of matrix) based on the current operation
            m = min(m,r)
            n = min(c,n)
        # total number of elements will be multiplication of bottom and right boundry asssming left and top boundry is 0,0
        return m*n
m=3
n=3
ops=[[2,2],[3,3]]
print(maxCount(m,n,ops))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-4> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-4/Assignment/solution.py"
4
```
<br>
<br>
💡 Question 8<br>
Given the array nums consisting of 2n elements in the form [x1,x2,...,xn,y1,y2,...,yn].<br>
Return the array in the form [x1,y1,x2,y2,...,xn,yn].<br>
Example 1:<br>
Input: nums = [2,5,1,3,4,7], n = 3<br>
Output: [2,3,5,4,1,7]<br>
Explanation: Since x1=2, x2=5, x3=1, y1=3, y2=4, y3=7 then the answer is [2,3,5,4,1,7].<br>

Solution_code:<br>
```
#question-8
def shuffle(nums, n):
    lst = []
    for i in range(n):
        lst.append(nums[i])
        lst.append(nums[n+i])
    return lst
nums = [2,5,1,3,4,7]
n = 3
print(shuffle(nums,n))
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program\lecture-4> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/lecture-4/Assignment/solution.py"
[2, 3, 5, 4, 1, 7]
```





