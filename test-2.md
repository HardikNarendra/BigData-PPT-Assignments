##DSA  MOCK TEST-2

Q.1 Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well.<br> 
You must not use any built-in exponent function or operator. 

Solution_code:
```
def fSqrt(x):

	if (x == 0 or x == 1):
		return x
	i = 1
	result = 1
	while (result <= x):

		i += 1
		result = i * i
	return i - 1

x = 8
print(fSqrt(x))

```
Output:
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/test2.py"
2
```

Q-2 You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

Solution_code:
```
class ListNode:
    def __init__(self, val):
        self.val = val
        self.next = None


def addTwoNumbers(l1: ListNode, l2: ListNode) -> ListNode:
 
    head = None
    temp = None
    carry = 0
   
    while l1 is not None or l2 is not None:
        sum_value = carry
        if l1 is not None:
            sum_value += l1.val
            l1 = l1.next
        if l2 is not None:
            sum_value += l2.val
            l2 = l2.next
        node = ListNode(sum_value % 10)
        
        carry = sum_value // 10
       
        if temp is None:
            temp = head = node
        else:
            temp.next = node
            temp = temp.next
    if carry > 0:
        temp.next = ListNode(carry)
    return head


head1 = ListNode(2)
head1.next = ListNode(4)
head1.next.next = ListNode(3)

head2 = ListNode(5)
head2.next = ListNode(6)
head2.next.next = ListNode(4)

result = addTwoNumbers(head1, head2)
while result is not None:
    print(str(result.val), end=" ")
    result = result.next
```

Output:
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/test2.py"
7 0 8 
```

