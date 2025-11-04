# Path finder
This is a path finder on a grid that goes like this:
## Grid Cell Values

The cells of the grid can take the following values:

- **T** – starting cell. There is exactly **one** such cell on the grid.  
- **"-"** – empty/free cell  
- **X** – obstacle  
- **C** – a hexadecimal number greater than 0, representing a combination of the following bit masks (combined using the OR `|` operator):

| Bit Mask | Hex | Meaning |
|---------:|----:|---------|
| `0001₂` | `1₁₆` | the cell is open from the **right** |
| `0010₂` | `2₁₆` | the cell is open from the **top** |
| `0100₂` | `4₁₆` | the cell is open from the **left** |
| `1000₂` | `8₁₆` | the cell is open from the **bottom** |

### Example

A cell open **from the left and from the bottom**: 0100₂ (left)
| 1000₂ (bottom)
= 1100₂ = C₁₆ (left-bottom)

## Path Rules
Starting from the **T** cell, find the **sum of the shortest path lengths** to each **C** cell, with the following constraints:

- The path **cannot cross**:
  - obstacle cells (`X`)
  - any other `C` cell
- Movement is allowed **only horizontally and vertically** (no diagonal moves)
- Paths may **cross each other**, but may **not** pass through other `C` cells

The algorithm should return a **single number**:  
the **sum of the shortest T → C path lengths**.

If a `C` cell is **not reachable** from `T`, then its path length counts as **0**.

The distance is defined as the number of **free (`-`) cells** between the `T` and `C` cells.  
Therefore, if `T` and `C` are adjacent, the distance is **0**.

## Input and Output
The application receives its input from **standard input (stdin)**.

- The first two lines of the input contain the values **M** and **N**.
- The following **M** lines each contain **N** cells representing the grid.

The program must print the resulting sum to **standard output (stdout)**.

## Example 
**Input:**
```
7
33
---------------------------------
--T----3-X---------X-----A-------
-------------------------X-------
---X---X------X-------------3----
------------------X------4---X---
---1--X-------C-X--------X-------
---X-----------------------------
```

**Output:**
```105```
