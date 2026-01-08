## Number of Subarrays with K Odd numbers ("Nice" Subarrays)

- [7, 1, 2, 3, 5] k = 3
- count = 0
- i = 0, 7 is odd, count = 1
- i = 1, 1 is odd, count = 2
- i = 2, 2 is even, count = 2
- i = 3, 3 is odd, count = 3
  ```
  (count-k) = (3-3) = 0
  count = 0 existed initially
  so, this subarray [7,1,2,3] is "Nice"
  ```
- i = 4, 5 is odd, count = 4
  ```
  (count-k) = (4-3) = 1
  count = 1 existed at i = 0 (7)
  there are 3 odd numbers from i=1 to i=4
  they are [1,3,5]
  so, the subarray [1,2,3,5] is "Nice"
  ```
#### This is same as Subarray having sum K !!!

## Map Approach
```
  unordered map <int, int> mp
  oddCount = 0, ans = 0
  mp[0] = 1 // store initial oddCount 0 
  for(i = 0 to n) {
    if arr[i] is odd, then oddCount++
    // check whether oddCount-k already exists in map
    if mp.count(oddCount - k) {
      ans += mp[oddCount - k]
    }
    mp[oddCount]++;
  }
  return ans;
```

## Sliding Window Technique

```
oddCount = 0, prevCount = 0, ans = 0
i = 0, j = 0

while(j < n) {
  if arr[j] is odd {
    oddCount++
    prevCount = 0
  }
  while(oddCount == k){
    prevCount++
    if i < n && arr[i] is odd, then oddCount--
    i++
  }
  ans += prevCount;
  j++;
}
return ans;
```
