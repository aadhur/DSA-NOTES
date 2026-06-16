# Queues

Number: 3

# Implement stack as queue - 225

from LIFO TO FIFO (only pop differs; pops first element in queues)

- Sol
    
    ```powershell
    class MyStack:
    
        def __init__(self):
            self.queue = deque()
            
    
        def push(self, x: int) -> None:
            self.queue.append(x)
            
    
        def pop(self) -> int:
            for _ in range(len(self.queue)-1):
                self.queue.append(self.queue.popleft())
            return self.queue.popleft()
            
    
        def top(self) -> int:
            return self.queue[-1]
            
    
        def empty(self) -> bool:
            return len(self.queue)==0
    ```
    

# Time needed to buy tickets - 2073

<aside>
💡

[2,3,2], k=2 → 6 

NOTE: k is index

</aside>

- Sol
    
    ```powershell
    ans = 0
    for i,x in enumerate(tickets):
    		ans += min(x, tickets[k] if i<=k else tickets[k]-1)
    return ans
    ```
    

# Reverse first K elements of Queue using Stack

 

<aside>
💡

[10,20,30,40,50,60,70,80,90], K=5 → [50,40,30,20,10,60,70,80,90]

</aside>

- O(N)/O(k)
    
    ```powershell
    stk = []
    for _ in range(k):
    		stk.append(q.popleft()) #stk=[10,20,30,40,50]
    while stk:
    		q.append(stk.pop()) #q=[60,70,80,90,50,40,30,20,10]
    for _ in range(len(q)-k):
    		q.append(q.popleft()) #q=[50,40,30,20,10,60,70,80,90]
    return q
    ```
    

TC: O(k) + O(k) + O(N-k) → O(N)