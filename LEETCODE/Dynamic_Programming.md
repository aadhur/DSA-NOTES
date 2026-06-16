# Dynamic Programming

# Counting Bits

<aside>
💡

2 → [0,1,1]

</aside>

- Sol - O(n)
    
    ```powershell
    res = [0]*n+1
    for i in range (1,n+1):
    		res[i] = res[i//2] + (i%2)
    return res
    ```
    

Logic: multiples of 2 for a number → same number of 1s

For example: 2,4,8,16,32,64 → one 1

so we down floor divide to its parent (which potentilly has the same 1s) but if it happens to be odd with no clear parent, we add 1

For example: 5 → 5//2+1 → res[2]+1

# Fibonacci - 509

- Sol-rec - O(2^n)
    
    ```powershell
    if n == 0:
        return 0
    if n == 1:
        return 1
    return self.fib(n-1)+self.fib(n-2)
    ```
    

# Coin Change - 322

<aside>
💡

[1,2,5], 11 → 3 i.e. 5+5+1

</aside>

# Climbing stairs - 70

<aside>
💡

3 → 3 i.e. 3 ways: 1+1+1,2+1,1+2 steps (O(n))

</aside>