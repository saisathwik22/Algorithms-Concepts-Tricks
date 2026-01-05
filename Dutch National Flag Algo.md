# Dutch National Flag Algorithm
- used to sort array of 0s 1s 2s without using built-in function

- 3 variables : left, mid, high

- `[0 to low - 1]` : 0s (extreme left)
- `[low to mid - 1]` : 1s
- `[high + 1 to n - 1]` : 2s (extreme right)
- `[mid to high]` : random and unsorted 0s/1s/2s

- here low is boundary for 0s
- mid tracks the current element
- high is boundary for 2s

```
[0....low-1][low....mid-1][mid.....high][high+1......n-1]
```

#### Idea
- at start, since entire array is random and unsorted 0s 1s and 2s
- place mid at 0 and high at n-1
- shrink the window [mid.....high] mid++ and high-- making sure that:
    - 0 to low-1 are all 0s
    - low to mid-1 are all 1s
    - high+1 to n-1 are all 2s
- eventually shrinking the [mid to high] region to 0 (mid = high)

#### Algorithm
```
  low = 0, mid = 0, high = n-1

  while(mid <= high) {
    if a[mid] == 0 {
      swap a[low] and a[mid]
      low++
      mid++
    }
    else if a[mid] == 1, then mid++
    else if a[mid] == 2 {
      swap a[mid] and a[high]
      high--
    }
  }
```

#### Time Complexity : O(n)
#### Space Complexity : O(1)
