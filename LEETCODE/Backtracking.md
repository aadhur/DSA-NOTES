# Backtracking

# Letter Case permutation

<aside>
💡

a1b2 → a1b2, A1b2, A1B2, a1B2

</aside>

- O(2^n) (both)
    
    ```powershell
    output = [""]
    for c in s:
    		tmp =[]
    		if c.isalpha():
    				for o in output:
    						tmp.append(o+c.lower())
    						tmp.append(o+c.upper())
    		else:
    				for o in output:
    						tmp.append(o+c)
    		output = tmp
    return tmp
    ```
    
- Rec so space is O(n + 2^n)
    
    ```powershell
    
    ```