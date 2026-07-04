# Python Notes (100 Days of Code)

> Running reference for Python concepts picked up during the course. Add to it as things come up.

## Loop control: `pass` vs `continue` vs `break`

Three keywords that are easy to mix up. `continue` and `break` live inside loops; `pass` works anywhere a statement is required.

- **`pass`** — does nothing. A placeholder for when Python's syntax needs a statement but you want no action. Execution just falls through and the loop carries on as normal.
- **`continue`** — skips the rest of the current iteration and jumps straight to the next one.
- **`break`** — exits the loop entirely, right now.

```python
for n in [1, 2, 3, 4]:
    if n == 2:
        pass       # does nothing, execution falls through
    if n == 3:
        continue   # skip the rest of THIS iteration, go to next n
    if n == 4:
        break      # leave the loop entirely
    print(n)

# Output:
# 1
# 2
# (3 is skipped by continue before it can print; 4 never prints because break exits first)
```

Rule of thumb: `pass` = "do nothing, keep going", `continue` = "skip to the next lap", `break` = "stop the loop".
