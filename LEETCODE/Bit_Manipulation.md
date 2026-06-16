# Bit Manipulation

Number: 1

Bit: Binary Digit

# Single Number - 136

similar to the one with missing number

<aside>
💡

[4,2,1,2,1] → 4

</aside>

- O(n)
    
    ```python
    arr = [2,2,1,2,1]
    xor = 0
    for num in arr:
        xor^=num
    print(xor)
    ```
    
    HashMap → **SC** becomes O(n) but bit gives O(1)