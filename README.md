[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/cm6PS4yt)
# Week 1 Homework: Evidence Desk Patterns

## Student Name

Dipesh Chaulagain

## Summary

This homework practices four core data structure patterns used in Python:

- Frequency counting with dictionaries to count how often each item appears
- Duplicate detection with sets to find the first repeated value efficiently
- Stack matching with lists to check whether opening and closing brackets are balanced
- Lookup tables with dictionaries to retrieve a value instantly by key

Each problem maps to a real interview pattern. Solving them builds intuition for choosing the right data structure based on what the problem needs.

## How to Run Tests

From the repository root, run:

```bash
pytest -q
```

To run one test file:

```bash
pytest -q tests/test_challenges.py
```

## Required Problems

Complete these functions in `src/challenges.py`:

1. `count_evidence`
2. `first_repeated_id`
3. `valid_tags`
4. `lookup_alias`

## Optional Challenges

These are extra practice unless your instructor tells you otherwise:

1. `process_reports`
2. `largest_time_gap`

Optional tests are no longer skipped — I completed both optional challenges.

---

# Problem Notes

## 1. Evidence Counter

### Pattern

Frequency counting

### Data Structure

Dictionary

### Approach

- Step 1: Create an empty dictionary called `counts`.
- Step 2: Loop through every item in the evidence list.
- Step 3: If the item is already a key in `counts`, add 1 to it. If not, set it to 1. Return `counts`.

### Complexity

- Time: `O(n)`
- Space: `O(n)`

Each item in the list is visited exactly once, so time scales linearly with the list length. In the worst case, every item is unique, so the dictionary could grow to the same size as the list.

### Edge Cases Checked

- [x] Empty list → returns `{}`
- [x] One item → returns that item with count 1
- [x] Repeated items → count is updated correctly
- [x] Different labels → each label tracked separately
- [x] Case sensitive → `"phone"` and `"Phone"` are counted separately

---

## 2. Repeat Suspect ID

### Pattern

Seen before

### Data Structure

Set

### Approach

- Step 1: Create an empty set called `seen`.
- Step 2: Loop through each ID in the list.
- Step 3: If the ID is already in `seen`, return it immediately. Otherwise add it to `seen`. After the loop, return `None`.

### Complexity

- Time: `O(n)`
- Space: `O(n)`

Each ID is checked and potentially added once. Set lookup and insertion are both O(1) on average, so the full loop is O(n). The set can hold at most n items.

### Edge Cases Checked

- [x] Empty list → returns `None`
- [x] No repeated IDs → returns `None`
- [x] First two IDs match → returns the first ID immediately
- [x] Multiple repeated IDs → returns the one that repeats first

---

## 3. Evidence Tag Validator

### Pattern

Stack matching

### Data Structure

List used as a stack

### Approach

- Step 1: Create an empty list called `stack` and a dictionary `matching` that maps each closing bracket to its expected opening bracket: `)` → `(`, `]` → `[`, `}` → `{`.
- Step 2: Loop through each character in the string. If it is an opening bracket, push it onto the stack. If it is a closing bracket, check whether the top of the stack matches — if the stack is empty or the top does not match, return `False`, otherwise pop the top.
- Step 3: After the loop, return `True` only if the stack is empty (every opening bracket was closed).

### Complexity

- Time: `O(n)`
- Space: `O(n)`

Every character is visited once. In the worst case (all opening brackets), the stack holds n items.

### Edge Cases Checked

- [x] Empty string → returns `True` (no brackets to check)
- [x] Correctly nested tags → returns `True`
- [x] Mismatched tags like `{[(])}` → returns `False`
- [x] Closing tag before opening tag like `)(` → returns `False`
- [x] Unclosed opening tag like `(()` → returns `False`
- [x] Non-bracket characters → ignored correctly

---

## 4. Alias Directory

### Pattern

Lookup table

### Data Structure

Dictionary

### Approach

- Step 1: Use `dict.get(alias, None)` to look up the alias key in the dictionary.
- Step 2: This returns the real name if found, or `None` if the alias does not exist. No loop is needed.

### Complexity

- Time: `O(1)`
- Space: `O(1)`

Dictionary lookup by key is O(1) on average. No extra space is used beyond the input.

### Edge Cases Checked

- [x] Known alias → returns the correct real name
- [x] Unknown alias → returns `None`
- [x] Empty dictionary → returns `None`

---

# Assistance & Sources

## AI Used?

- [x] Yes

## If yes, what did AI help with?

- Explaining how to set up the project and run pytest for the first time
- Reviewing the overall approach for each problem
- Helping fill in the README template with accurate complexity explanations

## Other Sources

- Python documentation: https://docs.python.org/3/library/stdtypes.html#dict
- Python documentation: https://docs.python.org/3/library/stdtypes.html#set
- Python documentation: https://docs.python.org/3/library/collections.html#collections.deque