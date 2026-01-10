## Substrings with K Unique Characters
## Subarray with K Unique Integers
- Algorithm same for both questions

- counting exactly "K" is hard

#### TRICK:
  ```
  Exactly K distinct = (At most K distinct) - (At most K-1 distinct)

  At most K = 1,2,3, ......., k-1, k
  At most K-1 = 1,2,3, ......., k-1
  Subtract : K
  ```
### Idea:
- maintain window [l...r]
- expand window from r side
- when condition reaches k, shrink the window from l side
- while shrinking the window, decrease the frequency of l element
- ans = (r - l + 1)



- Algorithm for substring and subarray is same
- just the difference is in hashing the elements
- hash character : freq[s[r] - 'a']++;
- hash number : freq[a[r]]++;
- freq[elementR] : freq[element at index r]
- freq[elementL] : freq[element at index l]

### Count of subarray/substring with At Most K distinct elements:
- countAtMostK(input, k)
  ```
  n = size of input
  l = 0, ans = 0
  vector freq to hash the elements
  distinct = 0

  for(r = 0 to n) {
    if freq[elementR] == 0, distinct++
    freq[elementR]++;

    while(distinct > k) {
      // SHRINK from Left side
      freq[elementL]--;
      if freq[elementL] == 0, distinct--
      l++
    }
    ans += (r - l + 1);
  }
  ```
### Count of subtring/subarray with exactly K distinct elements
- return countAtMostK(input, k) - countAtMostK(input, k - 1)


#### TC : O(N)
#### SC : O(hash space)
