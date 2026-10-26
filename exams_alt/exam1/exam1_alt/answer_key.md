# Exam 1 Alternate — instructor answer key

100 points total; four sections of 25 points. Keep this file private.

## Section 1 — Stable Matching (25)

1. (15; 5 each)
   - (a) Yes. h1 prefers s4 to current partner s2; s4 prefers h1 to current partner h2.
   - (b) No. h2 prefers s1 to s4, but s1 prefers current partner h3 to h2.
   - (c) No. (h4,s3) is already a pair in M and cannot be an unstable pair.
2. (10) No stable roommate matching exists. There are exactly three perfect matchings:
   - {Alex–Blair, Casey–Drew}: Blair–Casey blocks.
   - {Alex–Casey, Blair–Drew}: Alex–Blair blocks.
   - {Alex–Drew, Blair–Casey}: Alex–Casey blocks.
   Each named pair mutually prefers one another to their assigned roommates.

## Section 2 — Algorithm Analysis (25)

3. (9; 3 each) Exact doubling ratios:
   - (a) 8.
   - (b) log_3(2n)/log_3(n) = 1 + log_3(2)/log_3(n). Equivalent: 1 + 1/log_2(n).
   - (c) 2^n.
4. (5) A, C, E. Dividing by n² gives 6 + 3/n, which is always at least 6 and decreases toward 6. B fails at n=2; D fails already at n=10.
5. (6) Labels in printed order: 5, 1, 4, 3, 2, 1.
   Growth classes: log n < (log n)² < n < n log n < n^(3/2).
6. (5) C only: Θ(n log n). For each of n outer iterations, j takes values 1,2,4,... up to n, for floor(log_2 n)+1 iterations. No input-dependent branches change this count.

## Section 3 — Recursion (25)

7. (15)
   - (a; 5) Level 0: one node with work n; total n. Level 1: three nodes with work n/3 each; total n. Level 2: nine nodes with work n/9 each; total n.
   - (b; 3) 3^ell (n/3^ell) = n, including the leaf level because T(1)=1.
   - (c; 2) The same.
   - (d; 3) log_3(n)+1 levels, counting root and leaves.
   - (e; 2) Θ(n log n). The exact solution is n(log_3(n)+1), but an exact solution is not required.
8. (10) For wow, T(1)=Theta(1) (or 1 under the normalized model), and
   T(n)=3T(n/3)+Theta(n^2). The three recursive calls each process one third
   of the array; the nested loops perform n^2 constant-time iterations.
   The two recurrence blanks are 3T(n/3) and Theta(n^2).

## Section 4 — 1D Dynamic Programming (25)

9. (8)
   - (a; 2) 5: 1111, 112, 121, 211, 22.
   - (b; 6) Ways(0)=1, Ways(1)=1, Ways(i)=Ways(i-1)+Ways(i-2) for i>=2. The empty move sequence counts once. Also accept Ways(i)=0 for i<0, Ways(0)=1, and the recurrence for i>0.
10. (9)
    - (a; 2) Left to right: dependencies i-1 and i-3 are smaller indices.
    - (b; 7)

```text
TabulatedWut(H[1..n]):
    allocate M[1..n]
    M[1] = 2
    M[2] = H[2]
    M[3] = -1
    for i = 4 to n:
        M[i] = max(H[i] + M[i-1], 2*M[i-3])
    return M[n]
```

For n=3 the loop is empty and the base-case answer is returned.

11. (8)
    - (a; 2) 5: a|a|a|a, a|a|aa, a|aa|a, aa|a|a, aa|aa.
    - (b; 6) One recursive implementation:

```text
CountSplits(i):
    if i > n:
        return 1
    count = 0
    for j = i to n:
        if IsWord(A[i..j]):
            count = count + CountSplits(j+1)
    return count
```

The empty suffix contributes one partition (choose no words). An impossible
suffix contributes zero. Sum all successful first-word choices rather than
returning on the first success. Each partition has a unique first-word endpoint,
so this does not double count. No memoization is required.

## Source/style notes

Reviewed the public exams/exam1/collected_problems/main.tex, prac_1/main.tex,
prac_2/main.tex, and exam_1/main.tex. Retained the original exam's four 25-point
sections, handwritten answer format, notecard policy, typography, and recursion-tree
layout. Used new preference lists, functions, and algorithm instances. The roommate,
first-occurrence search, staircase, and word-splitting prompts are newly written.
