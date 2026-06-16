# Stacks

Number: 4

# Min Stack - 155

<aside>
💡

```
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]] -> [null,null,null,null,-3,null,0,-2]
```

</aside>

- Sol
    
    ```powershell
    
      def __init__(self):
    		  self.stack=[]
          
    
      def push(self, value: int) -> None:
          if not self.stack:
              min_val = value
          else:
              min_val = min(value, self.stack[-1][1])
          self.stack.append((value, min_val))
          
    
      def pop(self) -> None:
          self.stack.pop()
          
    
      def top(self) -> int:
          return self.stack[-1][0]
    
      def getMin(self) -> int:
          return self.stack[-1][1]
    ```
    

# Valid Parentheses - 20

<aside>
💡

([]) → True

([)] → False

</aside>

- O(n)/O(n)
    
    ```powershell
    stk = []
    hashmap = { ')':'(', '}':'{', ']':'['}
    for element in s:
    		if stk and (element in hashmap and stk[-1]==hashmap[element]):
    				stk.pop()
    		else:
    				stk.append(element)
    return not stack #return true if stack doesn't exist
    ```
    

Lookup is dicts are O(1) AND better than dict.keys() → creates a view of keys for O(1) and O(n) to iterate and find the key

# Evaluate Reverse Polish Notation - 150

<aside>
💡

[”2”,”1”,”+”,”3”,“*”] → 9 

EXP: (2+1)*3 = 9

</aside>

- O(n)/O(n)
    
    ```powershell
    stk = []
    for token in tokens:
        if token not in "+-*/":
            stk.append(int(token))
        else:
            r, l = stk.pop(), stk.pop()
            if token == "+":
                stk.append(r+l)
            elif token == "-":
                stk.append(l-r)
            elif token == "*":
                stk.append(r*l)
            else:
                stk.append(int(l/r))
    return stk.pop()
    ```
    

# Stack Sorting

<aside>
💡

[34,3,14,29,0] → [0,3,14,29,34] or [34,29,14,3,0]

</aside>

- O(n^2)/O(n)
    
    ```powershell
    stk = [34, 3, 14, 29, 0]
    
    ans = []
    while stk:
        element = stk.pop()
        while ans and ans[-1]>element:
            popped = ans.pop()
            stk.append(popped)
        ans.append(element)
    print(ans)
    
    # ans[-1]<element for descending order
    ```
    
- recursive
    
    ```powershell
    stk = [34, 3, 14, 29, 0]
    
    def sortStack(stk):
        if  len(stk)==0:
            return stk
        top = stk.pop()
        sortStack(stk)
        IncOrder(stk,top)
        return stk
    
    def IncOrder(stk, val):
        if len(stk)==0 or  stk[-1]<=val:
            stk.append(val)
            return
        top = stk.pop()
        IncOrder(stk, val)
        stk.append(top)
    
    ```