# Maximum XOR of subarray of size K

- arr = [2 5 8 1 1 3] k = 3
- 1st window = 2 5 8
- 2nd window = 5 8 1
- when window is moving forward
- 2 is excluded from window and 1 is included
- 2 is at index i-k = 3-3 = 0 and 1 is at index i=3
- xor 2 again to remove exclude from window
- xor 1 to include into window

```
input n
currXor = 0
for(i = 0 to k) currXor ^= arr[i]
maxXor = currXor
for(i = k to n) {
  currXor = currXor ^ arr[i-k] ^ arr[i]
  maxXor = max(maxXor, currXor)
}
return maxXor
```
