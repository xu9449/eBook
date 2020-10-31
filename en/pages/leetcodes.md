


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
Leetcode 42 水池蓄水问题
基础解法  brutal force
  找到当前结点左侧最高点，右侧最高点。计算出两点中较小的点，算出该点值与当前点值之间的差值，加入总结果中。
  T:O(n^2) S: O(1)
优化解法1 DP
  先利用两个array A[] B[], 分别记录从左边起始点到当前节点（包括）的最大值，以及右边同样。然后过一遍所有点，取 A[i] B[i] 较小点，与height[i]进行相减。
  T:O(n) S: O(n)
  关键点，dp帮助我们进行了记录，并且利用A[i] = Math.max(A[i - 1], height[i])，大大减少了重复计算的时间。
优化解法2 Stack
  利用stack帮助我们过一次array就可以得出所有的凹槽蓄水。相比于解法2更为优化，减少遍历次数。
  关键点，遇到下降趋势将节点坐标放入stack，等遇到向上趋势回头算账。且利用while，将所有小于当前节点的账目全部算清。
  关键点，不可以像往常一样用stack.isEmpty做为while结束条件，因为我们有情况是最高点在中间，它会一直存在于stack中无法弹出，因为弹出条件是当前节点的值大于stack的top。
  T:O(n) S:O(n)
优化解法3 2pointers
  左右两个pointer，向中心收缩，谁小挪谁，因为已经确定对面有比他大的，只用关心当前节点与其身后节点中最大的那个值谁大，如果当前节点大，更新最大值不蓄水，如果小，将差值加入蓄水的结果中。
  关键点，当两个pointer值相等的时候，可以走任意一方，不影响计算。
  T:O(n) S:O(1)
