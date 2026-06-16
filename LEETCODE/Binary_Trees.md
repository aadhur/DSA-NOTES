# Binary Trees

Number: 10

# Average of Levels in BT - 637

<aside>
💡

[3,9,20,null,null,15,7] → [3, 14.5, 11]

![image.png](image%205.png)

</aside>

- O(N)
    
    ```powershell
    results = []
    lev = deque([root])
    while lev:
    		values = []
    		for _ in range(len(lev)):
    				node = lev.popleft()
    				values.append(node.val)
    				if node.left: lev.append(node.left)
    				if node.right: lev.append(node.right)
    		results.append((sum(values)/len(values))
    return results
    ```
    

# Minimum depth of BT

<aside>
💡

[3,9,20,null,null,15,7]→2

![image.png](image%206.png)

</aside>

- Sol
    
    ```powershell
    if not root:
        return 0
    queue = deque([(root, 1)])
    while queue:
        node, level = queue.popleft()
        if not node.left and not node.right:
            return level
        if node.left: queue.append((node.left, level+1))
        if node.right: queue.append((node.right, level+1))
    return 0
    ```
    

# Maximum depth of BT - 104

<aside>
💡

[3,9,20,null,null,15,7]→3

</aside>

- My sol (ineff)
    
    ```powershell
    if not root:
        return 0
    ans = []
    maxdepth = 1
    level = deque([(root, maxdepth)])
    def find(level):
        while level:
            node, maxdp = level.pop()
            if not node.left and not node.right:
                ans.append(maxdp)
            if node.left:
                level.append((node.left, maxdp+1))
                find(level)
            if node.right:
                level.append((node.right, maxdp+1))
                find(level)
        return ans.append(0)
    find(level)
    return max(ans)
    ```
    
- Actual Sol - O(N)
    
    ```powershell
    if not root:
        return 0
    queue = deque([(root, 1)])
    while queue:
        node, level = queue.popleft()
        if node.left: queue.append((node.left, level+1))
        if node.right: queue.append((node.right, level+1))
    return level
    ```
    
- 1 line/ recursive O(N)
    
    ```powershell
    if not root:
        return 0
    return max(self.maxDepth(root.left), self.maxDepth(root.right))+1
    ```
    

# Max/Min node in BT

NOTE: BT is not in order like in BST (like left=low, right=high)

- Sol
    
    ```powershell
    queue = deque([root])
    max_node = 0
    min_node = float('inf')
    while queue:
    		node = queue.popleft()
    		if node.left: queue.append(node.left)
    		if node.right: queue.append(node.right)
    		if node.val > max_node:
    				max_node = node.val
    		if node.val < min_node:
    				min_node = node.val
    return max_node, min_node
    ```
    

# BT level order traversal - 102

<aside>
💡

[3,9,20,null,null,15,7] → [[3], [9,20],[15,7]]

</aside>

- O(N)/O(N)
    
    ```powershell
    if not root:
        return []
    order = []
    queue = deque([root])
    while queue:
        level =[]
        for _ in range(len(queue)):
            node = queue.popleft()
            if node.left: queue.append(node.left)
            if node.right: queue.append(node.right)
            level.append(node.val)
        order.append(level)
    return order
    ```
    

# Same tree - 100

<aside>
💡

p=[1,2,3],q=[1,2,3] → True

p=[1,2], q=[1,null,2] → False

</aside>

- O(N)/O(N)
    
    ```powershell
    queue = deque([(p,q)])
    while queue:
        node1, node2 = queue.popleft()
        if not node1 and not node2:
            continue
        if None in [node1,node2] or node1.val!=node2.val:
            return False
        queue.append((node1.left, node2.left))
        queue.append((node1.right, node2.right))
    return True
    ```
    

# Path sum - 112

<aside>
💡

root=[1,2,3], target = 5 → False

![image.png](image%207.png)

`root = [5,4,8,11,null,13,4,7,2,null,null,null,1], targetSum = 22 -> True`

![image.png](image%208.png)

</aside>

- Sol
    
    ```powershell
    if not root:
        return False
    queue = deque([(root, root.val)])
    sum =[]
    while queue:
        node, sum = queue.pop()
        if not node.left and not node.right:
            if sum == targetSum:
                return True
            continue
        if node.left: 
            queue.append((node.left, sum+node.left.val))
        if node.right: 
            queue.append((node.right, sum+node.right.val))
    return False
    ```
    

# Diameter of a BT - 543

<aside>
💡

![image.png](image%209.png)

root = [1,2,3,4,5] → 3 (4-2-5 or 2-1-3)

NOTE: Doesn’t always need to include root

</aside>

- O(N)/O(N) - Iterative
    
    ```powershell
    if not root:
        return 0
    stack = [(root, False)]
    max_height = {}
    diameter = 0
    while stack:
        node, visited = stack.pop()
        if not visited:
            stack.append((node, True))
            if node.left:
                stack.append((node.left, False))
            if node.right:
                stack.append((node.right, False))
        else:
            if node.left is None:
                left_height = 0
            else:
                left_height = max_height.pop(node.left)
            if node.right is None:
                right_height = 0
            else:
                right_height = max_height.pop(node.right)
            diameter = max(diameter, left_height + right_height)
            max_height[node] = max(left_height, right_height)+1
    return diameter
    ```
    
- O(N)/O(N) - Recursive
    
    ```powershell
    self.diameter = 0
    def depth(root):
        if not root:
            return 0
        left_depth = depth(root.left)
        right_depth = depth(root.right)
        self.diameter = max(self.diameter, left_depth+right_depth)
        return 1 + max(left_depth, right_depth)
    depth(root)
    return self.diameter
    
    ```
    

# Invert BT - 226

<aside>
💡

![image.png](image%2010.png)

[4,2,7,1,3,6,9] → [4,7,2,9,6,3,1]

</aside>

- DFS stack
    
    ```powershell
    if not root:
        return None
    stack = [root]
    while stack:
        curr = stack.pop()
        if curr:
            curr.left, curr.right = curr.right, curr.left
            stack.extend([curr.right, curr.left])
    return root
    ```
    
- DFS recursive
    
    ```powershell
    if not root:
        return None
    root.left, root.right = self.invertTree(root.right), self.invertTree(root.left)
    return root
    ```
    

Both O(N)/O(N)

# **Lowest Common Ancestor of a Binary Tree - 236**

<aside>
💡

![image.png](image%2011.png)

`[3,5,1,6,2,0,8,null,null,7,4]`

p=5, q=1 → 3

p=5, q=2 → 5

</aside>

- BFS queue (w/ set) O(N)/O(N)
    
    ```powershell
    parent = {root:None}
    queue = deque([root])
    while queue:
        node = queue.popleft() #popleft for BFS
        if node.left:
            queue.append(node.left)
            parent[node.left] = node
        if node.right:
            queue.append(node.right)
            parent[node.right] = node            
        if p in parent and q in parent:
            break
    ancestors = set()
    while p:
        ancestors.add(p)
        p = parent[p]
    while q:
        if q in ancestors:
            return q
        q = parent[q]
    ```
    
- BFS queue with pointer )O(N)/O(N) but O(1) in pointer path
    
    ```powershell
    parent = {root:None}
    queue = deque([root])
    while queue:
        node = queue.popleft() #popleft for BFS
        if node.left:
            queue.append(node.left)
            parent[node.left] = node
        if node.right:
            queue.append(node.right)
            parent[node.right] = node            
        if p in parent and q in parent:
            break
    pointer1, pointer2 = p, q
    while pointer1 != pointer2:
        pointer1 = parent[pointer1] if pointer1 else q
        pointer2 = parent[pointer2] if pointer2 else p
    return pointer1
    
    ```
    
- Recursive
    
    ```powershell
    if root == None or p == root or q == root:
        return root
    left = self.lowestCommonAncestor(root.left, p,q)
    right = self.lowestCommonAncestor(root.right,p,q)
    if left != None and right != None:
        return root
    if left != None:
        return left
    return right
    ```
    

NOTE: write down understanding of pointer method + recursive later