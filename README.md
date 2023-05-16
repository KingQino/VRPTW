# VRPTW
Attempt to run some basic VRPTW samples with the ambition for EVRPTW in multi-graph setting.



## Initialize data

Benchmark: [Solomon's instances](http://web.cba.neu.edu/~msolomon/problems.htm)

* Get data
* Plot the graph



For example, there are two `individuals`.
```python
A = [[9, 8, 4], [5, 6, 7, 1], [3, 2, 10]]
B = [[8, 7], [1, 2, 3, 10, 9], [5, 4, 6]]
```

Remove the __vehicle assignment__ info, and remain the info for recovery.

```python
A = [9, 8, 4, 5, 6, 7, 1, 3, 2, 10]
B = [8, 7, 1, 2, 3, 10, 9, 5, 4, 6]
```

PMX first randomly choose a range called the "mapping section".

```python
A = [9, 8, 4, 5, 6, 7, 1, 3, 2, 10]
             ^        ^
B = [8, 7, 1, 2, 3, 10, 9, 5, 4, 6]
             ^         ^
```

Then the first pair (5 - 2) is swapped, followed by a check to see where the duplicated customers are and swapped accordingly.

```python
A_swapped = [9, 8, 4, 2, 6, 7, 1, 3, 5, 10]
                     ^        ^
B_swapped = [8, 7, 1, 5, 3, 10, 9, 2, 4, 6]
                     ^         ^
```

Then it moves to the next pair (6 - 3) until all the pairs are exhausted in the mapping section.

```python
A_swapped = [9, 8, 4, 2, 3, 10, 1, 6, 5, 7]
                     ^         ^
B_swapped = [8, 10, 1, 5, 6, 7, 9, 2, 4, 3]
                      ^        ^
```

Recover from the PMX sequences

```python
Offspring_01 = [[9, 8, 4], [2, 3, 10, 1], [6, 5, 7]]
Offspring_02 = [[8, 10], [1, 5, 6, 7, 9], [2, 4, 3]]
```


