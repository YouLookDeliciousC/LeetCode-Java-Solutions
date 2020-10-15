# 🐯LeetCode-Java-Solutions
This repository is used to summarize all the leetcode algorithms that have been solved using Java Programming.

# 前言
- 本项目意在收集 leetcode 中各大题型最清晰的解题思路 😉，帮助短时间内捋顺 Java 编程知识体系、掌握常规通用、简单有效的解题方法，理解并记忆一些避免代码冗余的黑科技模块。
- 由于之前都是使用CPP编程，但迫于现实原因，转向Java编程。因此代码或许解法或写法不是最优，但是代码会尽量减少冗余。另外，由于时间紧迫，可能只有少数题目会配套题解，但大多数题目都会有简洁的注释。
- 水平有限，若您发现已存在的代码中如有冗余部分，欢迎 issue 或 PR。
- 另外这里有一份[ 🐍 Python 最短题解](https://github.com/cy69855522/Shortest-LeetCode-Python-Solutions)，带您体验 python 中各种让人叹为观止的奇巧解法，如果您对俩门语言都感兴趣的话，同时服用效果更佳。
- 此外还有一份体量相对完善的[Clearest-LeetCode-Cpp-Solutions](https://github.com/YouLookDeliciousC/Clearest-LeetCode-Cpp-Solutions)，尽量使用不冗余的解法，用CPP解决leetcode官方探索题。目前已经基本完成了探索内的数据类型模块。
- 欢迎加入QQ交流群：902025048 群内提供更多相关资料，更有刷题大牛为你解答疑问~
- 推荐使用【Ctrl + F】按键搜索题号
- Leetcode Acccount: [youlookdeliciousc](https://leetcode-cn.com/u/youlookdeliciousc/)
# 题目部分
## 数组
### [867. 转置矩阵](https://leetcode-cn.com/problems/transpose-matrix/)
```java
class Solution {
    public int[][] transpose(int[][] A) {
        int c = A.length, r = A[0].length;

        int[][] B = new int[r][c];
        for(int i = 0; i < c; ++ i){
            for(int j = 0; j < r; ++ j){
                B[j][i] = A[i][j]; //B[i][j] = A[j][i] 会超出索引。
            }
        }
        return B;
    }
}

```
### [1476. 子矩形查询](https://leetcode-cn.com/problems/subrectangle-queries/)
- 这题目很简单，难在题目太过冗长。
#### 第一种是暴力解法
能通过。
```java
class SubrectangleQueries {

    private int[][] rec = null;
    public SubrectangleQueries(int[][] rectangle) {
        this.rec = rectangle;
    }
    
    public void updateSubrectangle(int row1, int col1, int row2, int col2, int newValue) {
        if(rec != null){
            for(int i = row1; i <= row2; ++ i){
                for(int j = col1; j <= col2; ++ j){
                    rec[i][j] = newValue;
                }
            }
        }
    }
    
    public int getValue(int row, int col) {
        if(rec != null){
            return rec[row][col];
        }
        return -1;
    }
}

```

#### 第二种解法。高赞题解中，记录之前更新的值，如果getValue(location) location在之前更新的子矩阵范围内，可以直接返回相应value
### [977. 有序数组的平方](https://leetcode-cn.com/problems/squares-of-a-sorted-array/)
- 暴力解法，每个平方完之后sort排序
```java
class Solution {
    public int[] sortedSquares(int[] A) {
        for(int i = 0; i < A.length; ++ i){
            A[i] = A[i] * A[i];
        }
        Arrays.sort(A);
        return A;
    }
}
```

- 双指针法
```java
class Solution {
    public int[] sortedSquares(int[] A) {
        int l = 0, r = A.length-1, k = r;
        int[] B = new int[A.length];
        while(l <= r){
            if(A[l] + A[r] > 0){
                B[k--] = A[r] * A[r];
                r--;
            }else{
                B[k--] = A[l] * A[l];
                l++;
            }
        }
        return B;
    }
}
```

## 数组

### [1576. 替换所有的问号](https://leetcode-cn.com/problems/replace-all-s-to-avoid-consecutive-repeating-characters/)
```java
class Solution {
    public String modifyString(String s) {
        int len = s.length();
        
        if(len == 1) return "a";
        char[] schar = s.toCharArray();
        for(int i = 0; i < len; i ++){

            if(schar[i] == '?'){
                if(i > 0 && i < len -1){
                    char temp = 'a';
                    schar[i] = temp;
                    while(schar[i-1] == temp || schar[i + 1] == temp){
                        schar[i] = ++ temp;
                    }
                }else if(i == 0){
                    schar[i] = schar[i+1] == 'a' ? 'b': 'a';
                }else{
                    schar[i] = schar[i-1] == 'a' ? 'b': 'a';
                }
            }
        }
        s = new String(schar);
        return s;
    }
}
```
- 这题我写得有点冗长，观评论区大佬有人直接用`while ( (i < s.size()-1 && s[i]==s[i+1]) || (i > 0 && s[i] == s[i-1])) `这一行代码可以缩减掉好几个if判断语句。



### [459. 重复的子字符串](https://leetcode-cn.com/problems/repeated-substring-pattern/)
```java
class Solution {
    public boolean repeatedSubstringPattern(String s) {
        return (s+s).substring(1,s.length()*2-1).indexOf(s)!=-1;
    }
}
```
- 解析待添加

### []()



### []()


### []()
