## Minimum Window Subsequence
- given string s1 and s2
- find smallest substring in s1
- s2 should appear as a subsequence in that substring
  - characters of s2 should appear in same sequence
  - if multiple such substrings of same minimum window length are there:
    - then return the one that appears first in s1
- if no substring exists, return " " string

#### Example
- s1 = "geeksforgeeks" s2 = "eksrg"
- output : "eksforg"

### Approach
#### Forward Scanning
- ` find index i where s2 is ending as subsequence in s1`
- i = 0 and j = 0
- move i through s1 and j through s2
- if s1[i] == s2[j], then i++ and j++
- if s1[i] != s2[j], then i++
- when j hits s2.length, it means i is found
  ```
  i  = 0 1 2 3 4 5 6 7 8 9 10  11  12
  s1 = g e e k s f o r g e  e   k   s

  j  = 0 1 2 3 4
  s2 = e k s r g

  s2 ends as subsequence at index i = 8 in s1
  ```
#### Backward Scanning
- say k = i (end point of s2 in s1)
- index j is at last element of s2
- now iterate backwards from point k in s1 and from point j in s2
- if s1[k] == s2[j], then j-- and k--
- if s1[k] != s2[j], then k--
  ```
  start k from index 8 and iterate backwards
  k  = 0 1 2 3 4 5 6 7 8....
  s1 = g e e k s f o r g e e k s

  j  = 0 1 2 3 4
  s2 = e k s r g
  ```
- when j hits less than 0, stop the iteration
- we obtain an index k in s1, which is the start point of substring
- start = k = 2 | end = i = 8
- return s1.substring(2, 8) = eksforg

#### This Approach fails to extract minimum length substring as per requirement
#### So even after doing One Pass of Forward and backward scans,
#### We need to do multiple forward scans to find minimum length window

## Algorithm : 2 Pointer + Use Greedy to find smaller substring
```
string s1 (length m), s2 (length n)
int minLen = Int_max, startIdx = -1
int i = 0, j = 0

while(i < m) {
  k = i, j = 0;
  // FORWARD SCAN
  while(k < m && j < n) {
    if s1[k] == s2[j], then k++ and j++
    else only k++
  }
  // can't match further
  if j < n then return ""
  // end point : k
  int end = k - 1
  j = n - 1
  int p = end; // to back iterate
  while(p >= i && j >= 0) {
    if s1[p] == s2[j], then p--; j--;
    else only p--
  }
  start = p + 1
  len = end - start + 1; // WINDOW LENGTH
  if len < minLen {
    minLen = len
    startIdx = start;
  }
  i = start + 1;
  // do FORWARD SCAN again from index i
}
if startIdx == -1 then return ""
else return s1.substr(startIdx, minLen)

```
