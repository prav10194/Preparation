<h1>🐍 Backtracking in Python – Quick Guide</h1>

Backtracking is just DFS with undo.
Most NeetCode problems (subsets, permutations, combinations, N-Queens, etc.) follow the same pattern.

<h2>✅ 1. Correct State Management (Path + Choices)</h2>

Backtracking works like this:

1. Choose an option (add to path / mark visited).

2. Explore deeper (dfs(...)).

3. Un-choose (remove from path / unmark) before trying the next option.

<h2>🔑 Key Tips</h2>

Use a mutable list for the current path and append / pop in-place to avoid unnecessary copies.

Only copy when adding a complete solution:

```python

res.append(path[:])   # make a snapshot

```
Pass state as function parameters when possible to avoid globals.

<h2>Mini Pattern</h2>

```python

def backtrack(start):
    if base_condition:          # Exit condition
        res.append(path[:])     # Record a copy of path
        return
    for i in range(start, n):
        path.append(nums[i])    # Choose
        backtrack(i + 1)        # Explore
        path.pop()              # Un-choose

```
<h2>✅ 2. Clear Base / Exit Condition</h2>

Every problem needs a precise stopping rule:

| Problem Type	 | Base Condition Example |
|------|------------|
| Combination Sum	 | stop when target == 0 (or prune if < 0)      |
| Permutations| stop when len(path) == n       |
| N-Queens| stop when row == n       |

```python

def backtrack(start, path):
    # ✅ base condition
    if <finish_condition>:
        res.append(path[:])
        return

    for i in range(start, len(nums)):
        # ✅ choose
        path.append(nums[i])

        # ✅ explore
        backtrack(i + 1, path)  # or backtrack(0, path) if repeats allowed

        # ✅ un-choose
        path.pop()

res = []
backtrack(0, [])
return res

```
<h2>🎯 Takeaway</h2>

The two most important things are:

State Management – Correctly add/remove from path or mark/unmark visited nodes so recursion never leaks previous choices.

Base Condition – A precise exit rule to stop or record solutions and avoid infinite loops.

If these are clean, pruning and deduplication are just optimizations.

💡 Pro Tip:
Start with the template above, fill in the base condition, and focus on undoing every choice.
A clean state and a clear stopping rule solve 90% of NeetCode backtracking problems.
