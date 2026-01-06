### Palindrome:

- for a string to be a palindrome
  ```
  Count of odd frequency letters = 0 or 1 only
  at most 1 odd frequency letter
  ```

- consider letters a, b, c, d
##### Case 1 : when all occurences are even (0 odd frequency letters)
- say a frequency = 6
- b frequency = 4
- c frequency = 4
- d frequency = 2
- place the letters in below order
  ```
  a a a b b c c d | d c c b b a a a
  ```

##### Case 2 : when count odd letter frequency is 1
- say new letter e with frequency 3
- letter placement look like
  ```
  a a a b b c c d e | e | e d c c b b a a a
  ```

##### Case 3 : when count of odd letter frequency is 2
- say new letters e with frequency 3 and f with frequency 3
- the issue occurs at partition "fe" which disrupts the palindrome
- this is because the odd freq letters are more than 1
  ```
  a a a b b c c d e f |f e| f e d c c b b a a a
  ```

### Integer k, remove k characters from string, form a palindrome with remaining letters
- example
- k = 2, s = [t a a g a a k]
- remove t and k to form palindrome "aagaa"

- removing k letters
- odd frequency becomes even
- a - 3, b - 5, c - 7 (k = 3)
- remove 3 letters
- remove 1 a, 1 b, 1 c
- a - 2, b - 4, c - 6
- it can form a palindrome

- say, string s has x letters with odd frequency
  ```
  if x > k + 1, then can't create palindrome "NO"
  if x <= k + 1, then can create palindrome "YES"
  ```

###### Example 
- k = 2 , string s = [t a a k a g a]
- t freq = 1 (odd) k freq = 1 (odd) g freq = 1 (odd)
- remove t and k
- there is only 1 letter with odd frequency (1 <= (k+1))
- so palindrome can be formed
