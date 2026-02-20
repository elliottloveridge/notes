## Dynamic Programming
### Grid Walker

```
Question: Say that you are a traveler on a 2D grid. You begin in the top-left corner and your goal is to travel to the bottom-right corner. You may only move down or right.

How many unqiue paths can you take?
```

You have a grid, with its size defined by $m \times n$

Before implementing, it is important to understand how this question is working.

Say you had the function call `gridTraveler(2, 3)`, the **three** possible paths could be defined by;

![[gridwalk.png]]

If you think of a simple example, a $1 \times 1$ grid would have a path equal to 1 (no move needed)

For a dimension of **zero** you should return 0 (no grid)

- These base cases can be used to reconstruct a larger answer.

Say you wanted the answer for a $3 \times 3$ grid;
- As you move, you effectively reduce the dimensions of the grid where you can possible move (as you can only move down or right)
- This can therefore be modeled again as a tree (below)

![[grid-tree.png]]
 
```python
def gridTraveler(m, n):
    if m == 1 and n == 1:
        return 1
    # no way to travel on the grid
    elif m == 0 or n == 0:
        return 0
    else:
        return gridTraveler(m - 1, n) + gridTraveler(m, n - 1)
```

