# Linked List

Number: 7

# Middle of the linked list - 876

<aside>
💡

[1,2,3,4,5] → [3,4,5] (just return node, it gets passed as linked by lc)

[1,2,3,4] → [3,4] (second middle for even)

</aside>

- O(n) and C space
    
    ```powershell
    slow = fast = head
    while fast and fast.next:
    		slow = slow.next
    		fast = fast.next.next
    return slow
    ```
    

![image.png](image%202.png)

# Linked list cycle -141

<aside>
💡

![image.png](image%203.png)

[3,2,0,-4], pos=1 → true [NOTE: pos is not given as parameter]

</aside>

- O(n)/O(1)
    
    ```powershell
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    
        if slow == fast:
            return True
    return False
    ```
    

# Reverse LL - 206

<aside>
💡

[1,2,3,4,5] → [5,4,3,2,1]

</aside>

- O(n)/O(1)
    
    ```powershell
    curr = head
    prev = None
    
    while (curr != None):
    		nextnode = curr.next
    		curr.next = prev
    		prev = curr
    		curr = nextnode
    head = prev
    return head
    ```
    

# Remove LL elements - 203

<aside>
💡

[1,2,6,3,4,5,6], 6 → [1,2,3,4,5] 

NOTE: return listnode as head, not a list so becomes tricky

</aside>

- O(n)/O(1)
    
    ```powershell
    dummy = ListNode(-1)
    dummy.next = head
    curr = dummy
    while curr.next != None:
        if curr.next.val == val:
            curr.next = curr.next.next
        else:
            curr = curr.next
    return dummy.next
    
    ```
    

# Reverse LL II - 92

<aside>
💡

[1,2,3,4,5], left=2,right=4 → [1,4,3,2,5]

</aside>

- O(n)/O(1)
    
    ```powershell
    dummy = ListNode(-1, head)
    before_rev = dummy
    for _ in range(left-1):
    		before_rev = before_rev.next
    first_rev = before_rev.next
    prev = before_rev
    curr = first_rev
    
    for _ in range(right-left+1):
    		tmp = curr.next
    		curr.next = prev
    		prev = curr
    		curr = tmp
    before_rev.next = prev
    first_rev.next = curr
    return dummy.next
    ```
    

# Palindrome LL - 234

<aside>
💡

[1,2,2,1] → True

</aside>

- O(n)/O(1)
    
    ```powershell
    slow = fast = head
    #1. Find middle
    while fast and fast.next:
    		slow = slow.next
    		fast = fast.next.next
    #2. Reverse from middle
    rev = slow
    prev = None
    while rev!= None:
    		tmp = rev.next
    		rev.next = prev
    		prev = rev
    		rev = tmp
    #3. Compare
    left = head
    right = prev
    while right!= None:
    		if (left.val != right.val):
    				return False
    		left = left.next
    		right = right.next
    return True
    
    ```
    
1. Find the middle element
2. reverse the second half, starting from the middle pointing to None
3. Use the None as constraint and compare from head as left to right (till right reaches None)

# Merge Two Sorted Lists - 21

<aside>
💡

[1,2,4], [1,3,4] → [1,1,2,3,4,4]

![image.png](image%204.png)

</aside>

- O(n)/O(1)
    
    ```powershell
    dummy = cur = ListNode()
    while list1 and list2:
        if list1.val < list2.val:
            cur.next = list1
            list1, cur = list1.next, list1
        else:
            cur.next = list2
            list2, cur = list2.next, list2
    if list1 or list2:
        cur.next = list1 if list1 else list2
    return dummy.next
    ```
    

NOTE: Find why dummy is req, why not just cur