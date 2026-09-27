# Max Heap – Student Score Analysis

## Problem Statement

Given the following student scores:

```text
78, 92, 65, 88, 95, 72, 84, 90
```

The objectives are:

- Implement a **Max Heap**
- Insert all scores one by one
- Display the heap after each insertion
- Find the highest score using a **Max Heap**
- Find the highest score using **Linear Search**
- Compare both methods
- Justify which method is better for continuously maintaining the highest score

---

## Max Heap Implementation

A Max Heap is a complete binary tree where every parent node is greater than or equal to its children.

During insertion:

1. The new score is inserted at the end of the heap.
2. It is compared with its parent.
3. If the new score is greater than its parent, they are swapped.
4. This process continues until the Max Heap property is restored.

---

## Heap After Each Insertion

| Insertion | Score | Max Heap | Comparisons |
|---|---:|---|---:|
| 1 | 78 | `78` | 0 |
| 2 | 92 | `92 78` | 1 |
| 3 | 65 | `92 78 65` | 1 |
| 4 | 88 | `92 88 65 78` | 2 |
| 5 | 95 | `95 92 65 78 88` | 2 |
| 6 | 72 | `95 92 65 78 88 72` | 1 |
| 7 | 84 | `95 92 84 78 88 72 65` | 2 |
| 8 | 90 | `95 92 84 90 88 72 65 78` | 2 |

### Final Max Heap

```text
95 92 84 90 88 72 65 78
```

**Total insertion comparisons: 11**

---

## Finding the Maximum Using Max Heap

In a Max Heap, the largest element is always stored at the root.

Therefore:

```text
Maximum = heap[0] = 95
```

No element-to-element comparisons are required after the heap has already been constructed.

**Time Complexity: O(1)**

---

## Finding the Maximum Using Linear Search

In Linear Search, the first score is initially considered the maximum.

Every remaining score is compared with the current maximum.

For 8 scores:

```text
Comparisons = n - 1
            = 8 - 1
            = 7
```

Therefore:

```text
Maximum = 95
Comparisons = 7
```

**Time Complexity: O(n)**

---

## Comparison

| Operation | Max Heap | Linear Search / Unsorted List |
|---|---|---|
| Find Maximum | O(1) | O(n) |
| Insert New Score | O(log n) | O(1) append |
| Maintain Highest Score | Automatically maintained | Requires tracking or searching |
| Space Complexity | O(n) | O(n) |

---

## Analysis

### Finding the Maximum

In a **Max Heap**, the highest score is always stored at the root. Therefore, finding the maximum requires only direct access to the root and takes **O(1)** time.

In **Linear Search**, all scores may need to be checked. Therefore, finding the maximum takes **O(n)** time.

For the given 8 scores, Linear Search requires **7 comparisons**.

### Inserting a New Score

In a Max Heap, a newly inserted score may need to move upward to maintain the heap property. Therefore, insertion has a worst-case time complexity of **O(log n)**.

In an unsorted array, a new score can simply be appended in **O(1)** time. However, the array does not automatically maintain the highest score.

### Increasing Number of Students

As the number of students increases, repeatedly performing Linear Search becomes more expensive because every maximum search requires **O(n)** time.

A Max Heap continues to provide the highest score in **O(1)** time while supporting new insertions in **O(log n)** time.

---

## Justification

A **Max Heap is suitable for continuously maintaining the highest student score**.

This is because:

- The highest score is always available at the root.
- Finding the maximum takes **O(1)** time.
- New scores can be inserted in **O(log n)** time.
- The heap automatically maintains the required Max Heap property.

Linear Search is simple, but finding the highest score requires **O(n)** time whenever the list is scanned.

Therefore, when scores are continuously added and the highest score needs to be accessed frequently, a **Max Heap is an efficient and appropriate data structure**.

---

## Repository Structure

```text
max-heap-student-scores/
├── max_heap.c
├── output_screenshot.png
└── README.md
```

---

## How to Compile and Run

Compile:

```bash
gcc max_heap.c -o max_heap
```

Run:

```bash
./max_heap
```

---

## Output

The program displays:

- Heap after each insertion
- Number of comparisons during insertion
- Final Max Heap
- Highest score using Max Heap
- Highest score using Linear Search
- Number of comparisons for both methods

The highest score obtained using both methods is:

```text
95
```
