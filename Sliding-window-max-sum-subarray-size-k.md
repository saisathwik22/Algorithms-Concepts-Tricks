# Sliding Window Technique
### Find Maximum Sum Subarray (size k)

- start of window (i) end of window (j)
- track window using i and j starting from 0
- add the element arr[j] to sum as you expand the window from j end
- once the window hits the size k, keep storing max sum
- maintain the window size as k, don't let it increase or decrease
- move the window forward without disturbing its size k
- when window moves forward (start : sum - arr[i]) and (end : sum + arr[j]) with i++ and j++
- window size = j - i + 1
```
  i = 0, j = 0, sum = 0, ans = int-min
  while(j < n)
    sum += arr[j]
    if (j - i + 1 < k) j++
    else if (j - i + 1 == k)
      ans = max(ans, sum)
      sum = sum - arr[i]
      i++; j++
  return ans
```
