## 【基础入门题型】
#### (1) 输入处理（重要）：HJ5.进制转换
```python
import sys
dic = {"A": 10, "B": 11, "C": 12, "D": 13, "E": 14, "F": 15,"x":0}
num = input()
num = num[:]
n = 0
for i in range(0,10):
    dic[str(i)] = i
for i in range(len(num)):
    if num[i] in dic:
        n += dic[num[i]] * 16 ** (len(num) - i - 1) 
if n>=1 and n<= 2147483647:
    print(n)
```
使用int(num,16)转换为十进制
```Python
import sys
while True:
    try:
        a = input()
        print(int(a,16))
    except:
        break
```
#### (2) 排列组合：(牛客搜索)NC61.两数之和
①两层for比较

②哈希表法
把target-x都放到表里
```Python
class Solution:
    def twoSum(self , numbers: List[int], target: int) -> List[int]:
        # write code here
        hashtable = dict()
        for i in range(0,len(numbers)):
            if target - numbers[i] in hashtable:
                print([hashtable[target-numbers[i]]+1,i+1])
                return ([hashtable[target-numbers[i]]+1,i+1])
            hashtable[numbers[i]] = i
```
#### (3) 快速排序：HJ3.明明的随机数
>数组去重,排序
```Python
import sys
while True:
    try:
        n = int(input())#整型
        set1 = set({})#去重
        for i in range(n):# add
            set1.add(int(input()))
        nums = list(set1)
        nums.sort()#排序
        for i in nums:#输出
            print(i)
    except:
        break
```
#### (4) 哈希表：HJ10.字符个数统计
①去重set
```Python
import sys
str1 = input()
str1 = set(str1)
n = 0
for s in str1:
    n += 1
print(n)
```
②哈希表
```Python
import sys
hashtable = dict()#哈希表
str1 = input()
n = 0
for i in str1:
    if i not in hashtable:
        hashtable[i] = 1#不在哈希表置1
print(len(hashtable))#打印哈希表长度
```
(5) 递归：NC68.跳台阶
（带\*题目与第一第二道题目难度相近，以下题目基本覆盖大部分知识点）
跳台阶-==斐切那波数列== - 动态规划(用上一步结果快速计算下一步结果)![[Pasted image 20230906211451.png]]
```python
class Solution:                          
    def jumpFloor(self,number: int) -> int:    
        # write code here                
        n = [1,2]                      
        if number < 3:                              
            return number                
        for i in range(2,number):        
            n.append(n[i-1] + n[i-2])    
        return n[number - 1]
```
2.字符串操作（6题）
(1) HJ17.坐标移动

(2) HJ20.密码验证合格程序
(3) *HJ23.删除字符串中出现次数最少的字符
(4) *HJ33.整数与IP地址间的转换
(5) HJ101.输入整型数组和排序标识
(6) *HJ106.字符串逆序
3.排序（5题）
(1) HJ8.合并表记录
(2) *HJ14.字符串排序
(3) HJ27.查找兄弟单词
(4) *NC37.合并区间
(5) *HJ68.成绩排序
4.栈（2题）
(1) NC52.括号序列
(2) *leetcode 1614.括号的最大嵌套深度
5.排列组合（2题）
(1) *leetcode 面试题08.08.有重复字符串的排列组合
(2) leetcode 77.组合
6.双指针（3题）
(1) *leetcode 674.最长连续递增序列
(2) NC17.最长回文子串
(3) NC28.最小覆盖子串
7.深搜（1题）
(1) HJ41.称砝码
8.二叉树（2题）
(1) *leetcode 剑指offer 32 — II.从上到下打印二叉树 II
(2) leetcode 剑指offer 32 — III.从上到下打印二叉树 III
9.其他（6题）
(1) *HJ108.求最小公倍数
(2) *HJ28.素数伴侣
(3) *HJ60.查找组成一个偶数最接近的两个素数
(4) *leetcode 994.腐烂的橘子
(5) leetcode 204.计数质数
(6) HJ25. 数据分类处理
递归、分治、单调栈、并查集、滑动窗口、前缀和、查分、 二分 查找 、BFS广搜、DFS深搜