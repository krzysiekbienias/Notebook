# Palindrome check

| Title            | Source     | Data Structure | Algo Concept | Difficulty | Time Complexity | Space Complexity |
|------------------|------------|----------------|--------------|------------|-----------------|------------------|
| Palindrome check | AlgoExpert | string         | Two pointers | easy       | O(n)            | O(1)             |
```python
def isPalindrome(string):
    l_p=0
    r_p=len(string)-1
    while l_p<r_p:
        if string[l_p]==string[r_p]:
            l_p+=1
            r_p-=1
        else:
            return False
    return True
```
### Key code insights
* two pointers, and while loop.

# Longest substring without repeating character
| Title                                         | Source   | Data Structure | Algo Concept   | Difficulty | Time Complexity | Space Complexity |
|-----------------------------------------------|----------|----------------|----------------|------------|-----------------|------------------|
| Longest Substring Without Repeating Character | LeetCode | String         | Sliding Window | Medium     | O(n)            | O(min(m,n))      |

```python 
def length_of_longest_substring(input_string: str) -> int:
    start_index = 0
    end_index = 0
    char_count = {}
    max_length = 0

    while end_index < len(input_string):
        current_char = input_string[end_index]
        if current_char in char_count:
            char_count[current_char] += 1
        else:
            char_count[current_char] = 1

        while char_count[current_char] > 1:
            start_char = input_string[start_index]
            char_count[start_char] -= 1
            start_index += 1

        max_length = max(max_length, end_index - start_index + 1)
        end_index += 1

    return max_length

```
### Key code insights
1.	Expanding the Window (Outer while Loop):
	* The ```while end_index < len(input_string)``` loop moves the end of the window (end_index) forward one character at a time.
	* Each iteration processes the character at end_index (referred to as current_char) and updates the char_count dictionary to track the occurrences of each character in the window.
	* This expansion increases the size of the window.
2. Shrinking the Window (Inner while Loop):
	* If the current character (current_char) appears more than once in the char_count dictionary, the inner ```while char_count[current_char] > 1``` loop is triggered.
	* In this loop, the start of the window (start_index) moves forward one character at a time to shrink the window until there are no duplicate characters in the current substring.
	* During this process, the count of the character at start_index (referred to as start_char) is decremented in the char_count dictionary.
3. Updating results:
   * ```max(max_length, end_index - start_index + 1)``` 
   After ensuring the window contains only unique characters (no duplicates), the code calculates the length of the current valid window ```(end_index - start_index + 1)``` and updates max_length if this length is greater than the previous maximum.

### debug
```python
char_count = {dict: 2} {'p': 0, 'w': 2}
current_char = {str} 'w'
end_index = {int} 2
input_string = {str} 'pwwkew'
max_length = {int} 2
start_char = {str} 'w'
start_index = {int} 1
```

# 389. Find the Difference

| Title               | Source   | Data Structure | Algo Concept | Difficulty | Time Complexity | Space Complexity |
|---------------------|----------|----------------|--------------|------------|-----------------|------------------|
| Find the difference | LeetCode | string         | hashing      | easy       | O(n)            | O(1)             |
## Idea - Hashing
* Count the occurrences of each character in  word1  and  word2 .
* Increment the count for each character in  word1.
* Decrement the count for each character in  word2.
* The character with a non-zero count after processing both strings is the added character.


```python
def find_difference(word1: str, word2: str) -> str:
    #this is a difference of characters in words
    word_dict=dict()
    for i in range(len(word1)):
        if word1[i] in word_dict:
            word_dict[word1[i]] += 1
        else:
            word_dict[word1[i]] = 1
    for i in range(len(word2)):
        if word2[i] in word_dict:
            word_dict[word2[i]] -= 1
        else:
            word_dict[word2[i]] = 1
    for key,value in word_dict.items():
        if value != 0:
            return key
```

Function to To get a key from a hash map (dictionary in Python) based on a specific value, you can iterate through the dictionary and check for the value. Here’s how you can do it:
```python 
def get_key_by_value(d, target_value):
    for key, value in d.items():  # Iterate through key-value pairs
        if value == target_value:
            return key
    return None  # Return None if no matching value is found

print(key)  # Output: 'b'
```