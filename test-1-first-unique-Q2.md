** Q-2 First Unique**
<br>
<br>
Solution_code:<br>
```
#find first unique character
# i will using hashmap/dictionary for counting the frequency of elements
def first_unique(s):
    frequency = {}
    
    # Calculate the frequency of each character in the string
    for char in s:
        if char not in frequency:
            frequency[char] = 1
        else:
            frequency[char] += 1

    # Find the first unique character and return its index
    for i in range(len(s)):
        if frequency[s[i]] == 1:
            return i
    
    return -1

s = "loveleetcode"
print(first_unique(s))

```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/test-1solution.py"
2
```