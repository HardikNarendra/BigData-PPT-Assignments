 **Q-1 Move Zeroes**
<br>
<br>
 Solution_code:<br>
 ```
 #move zeroes
def move_zeroes(nums,n):
   
    i = 0
    counter = 0
    #iterating and deleting zero if occurs and appending it to the list
    while i < n - counter:
        if nums[i] == 0:
            del nums[i]
            nums.append(0)
            counter += 1
        else:
            i += 1

    return nums

nums = [0, 1, 0, 3, 12]
n = len(nums)
print(move_zeroes(nums,n))
 ```
 Output:
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/test-1solution.py"
[1, 3, 12, 0, 0]
```
