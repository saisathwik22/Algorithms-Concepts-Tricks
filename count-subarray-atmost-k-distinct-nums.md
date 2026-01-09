## Count Subarrays with atmost K distinct Integers

- a = [1,2,2,3] k = 2
  ```
  Subarrays
  [1] [2] [3] [1,2] [2,2] [2,3]
  [1,2,2] [2,2,3] [3] [1,2,2,3]
  ```
- there are 9 subarrays with at most 2 distinct integers

## Sliding Window Approach using map
- fix pointers l and r at 0
- expand the window towards right using r
- find largest window [l....r] that has atmost K distinct elements
- then all subarrays in window [l....r] are valid
  ```
  Count of valid subarrays = (r - l + 1)
  ```
- TC : O(n) SC : O(k)

### Code
l = 0, r = 0, ans = 0
map<int, int> mp;
for(r = 0 to n) {
  mp[a[r]]++;
  while(mp.size() > k) {
    mp[a[l]]--;
    if(mp[a[l]] == 0) mp.erase(a[l]);
    l++;
  }
  ans += (r - l + 1);
}
return ans;

### Dry Run
- a = [1,2,2,3] k = 2
- fix l and r at index 0
- maintain a map and distinct variable and answer variable
- iterate over the array using r

- r = 0, push 1 into map, distinct = 1 (<=k)
- subarrays ending at r is [1] | count = (0-0+1) = 1
- ans = 1

- r = 1, push 2 into map, distinct = 2 (<=k)
- subarrays ending at r are [1,2] [2] | count = (1-0+1) = 2
- ans = 1 + 2 = 3

- r = 2, 2 already exists in map, so mp[2]++, distinct = 2 (<=k)
- subarrays ending at r are [2] [2,2] [1,2,2] | count = (2-0+1) = 3
- ans = 3 + 3 = 6

- r = 3, push 3 into map, distinct = 3 (>k)
- shrink the window by removing a[l] from map and distinct--
- l = 1, distinct = 2(<=k)
- subarrays [1...3] are [3] [2,3] [2,2,3]
- count = (3-1+1) = 3
- ans = 6 + 3 = 9
