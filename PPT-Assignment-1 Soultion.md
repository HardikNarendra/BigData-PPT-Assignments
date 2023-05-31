
💡 Q1. Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.<br>

You may assume that each input would have exactly one solution, and you may not use the same element twice.<br>

You can return the answer in any order.<br>

Example:<br>
Input: nums = [2,7,11,15], target = 9<br>
Output0 [0,1]<br>

Explanation: Because nums[0] + nums[1] == 9, we return [0, 1]<br>

Solution_Code:<br>
```
# Question-1
arr=[2,7,11,15]
target=23
flag = False
n=len(arr)
for i in range(0,n):
    for j in range(i+1,n):
        sumation = arr[i] + arr[j]
        if sumation == target:
            loc1 = i
            loc2 = j
            flag = True
if flag:
    print(loc1,",",loc2)
```
Output:</br>
```
PS C:\Users\Dell> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/Ineuron Big Data Bootcamp/Python Assignment/Assignment-1/Q1-Solution.py"
1 , 2
```


