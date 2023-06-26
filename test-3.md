Q1.Implement a stack using a list in Python. Include the necessary methods such as push, pop, and isEmpty.<br>
Solution_code:<br>
```
#stack implementation using list in python

#push method
def push(stack,data):
    stack.append(data)
    print(data,"pushed onto stack")

#pop  method
def pop(stack):
    l=len(stack)
    data=stack[l-1]
    stack.pop()
    print(data,"removed from the stack")

#is empty method
def isEmpty(stack):
    if len(stack) == 0:
        #if stack is empty return true
        return "Stack is empty"
    else:
        #if stack is not empty return false
        return "Stack is not empty"
    
stack=[]
push(stack,1)
push(stack,10)
push(stack,48)
push(stack,5)
push(stack,100)
pop(stack)
pop(stack)
print(isEmpty(stack))
print("Stack is:",stack)
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/test-3.py"
1 pushed onto stack
10 pushed onto stack
48 pushed onto stack
5 pushed onto stack
100 pushed onto stack
100 removed from the stack
5 removed from the stack
Stack is not empty
Stack is: [1, 10, 48]
```
Q2.Implement a queue using a list in Python. Include the necessary methods such as enqueue, dequeue, and isEmpty.<br>
Solution:<br>
```
#implementing a queue using a list in python

#enque method
def enqueue(queue,data):
    if len(queue)==size:
        print("Queue is full")
    else:
        queue.append(data)
        print(data,"inserted in queue")

#deque  method
def dequeue(queue):
    if len(queue)==0:
        print("Queue is empty")
    else:
        data=queue[0]
        queue.pop(0)
        print(data,"removed from the queue")

#is empty method
def isEmpty(queue):
    if len(queue) == 0:
        #if stack is empty return true
        return "Queue is empty"
    else:
        #if stack is not empty return false
        return "Queue is not empty"
    
size=input("Enter the size of the queue:")
queue=[]
enqueue(queue,1)
enqueue(queue,56)
enqueue(queue,25)
enqueue(queue,100)
enqueue(queue,85)
enqueue(queue,74)
dequeue(queue)
dequeue(queue)
dequeue(queue)
print(isEmpty(queue))
print("Queue is:",queue)
```
Output:<br>
```
PS C:\Users\Dell\OneDrive\Desktop\PPT program> & C:/Users/Dell/AppData/Local/Programs/Python/Python311/python.exe "c:/Users/Dell/OneDrive/Desktop/PPT program/test-3.py"
1 inserted in queue
56 inserted in queue
25 inserted in queue
100 inserted in queue
85 inserted in queue
74 inserted in queue
1 removed from the queue
56 removed from the queue
25 removed from the queue
Queue is not empty
Queue is: [100, 85, 74]
```

