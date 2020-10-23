


### Goal: #90days400leetcodes
10/11/2020 - 01/09/2021  
[Coding Record File](https://docs.google.com/spreadsheets/d/1kFZOmmElIO5Ik969EUWhK7tl5dMdUAHI/edit#gid=718835785) keep updating ...

update | Problems Fixed | Average
------------ | ------------- |  ----------
10/23/2020 |    18 / 400 |   

Interview Process:

1. Document your assumptions   
2. Explain your approach and how you intend to solve the problem  
3. Provide code comments where applicable  
4. Explain the big-O run time complexity of your solution. Justify your answer  
5. Identify any additional data structures you used and justify why you use them  
6. Only provide your best answer to each part of the question

819 Most Common Word  
>这是一道substring类型题目，大量的简介方法，总结一起. 关键是要分清楚几种情况。
解法1: String Processing in Pipeline, 将string通过split 切成 array，将string存储到对应的map中去，记录count，最后求出map中通过比较value求出map的key。
> Time: O(m + n) n为number of characters in iput string, m为number of characters in ban string.
> Space: O(N + M)  
解法2: Character Processing in One-Pass 通过对整个string 挨个character的扫，遇到不是l ter的就跳过。

```java
  // replace to lower case
  String normalizedStr = paragraph.replaceAll("[^a-zA-Z0-9 ]", " ").toLowerCase();

  // split the string with multiple spaces
  String[] words = normalizedStr.split("\\s+");

  // map
  wordCount.put(word, wordCount.getOrDefault(word, 0) + 1);

  // return the word with the highest frequency
  return Collections.max(wordCount.entrySet(), Map.Entry.comparingByValue()).getKey();
```
