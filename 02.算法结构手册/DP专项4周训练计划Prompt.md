# DP专项4周训练计划（增强版）

## 适用情况

- 已完成一轮算法训练。
- 除动态规划（DP）外，其他算法模块已经学习。
- DP基础薄弱，需要系统建立DP能力。
- 每天投入2-3小时。
- 目标：达到大厂算法面试中的DP建模与解题能力。

---

# 总目标

4周后能够：

1. 理解DP核心思想：
   - 状态
   - 子问题
   - 状态转移
   - 初始化
   - 空间优化

2. 面对陌生DP题完成：

题目识别 → 判断DP类型 → 定义状态 → 推导转移 → 分析复杂度 → 编写代码

3. 掌握主要DP类型：

- 线性DP
- 背包DP
- 序列DP
- 状态机DP
- 区间DP
- 树形DP

---

# 新增训练模块：每日DP分类识别训练（固定15分钟）

每天正式刷题前完成。

训练方式：

给出10道随机DP相关题目，只回答：

1. 是否适合使用DP？
2. 属于哪一种DP模型？
3. 状态大概如何定义？

禁止写代码。

目标：

训练面试第一阶段：

识别问题 → 建模。

---

# 训练原则

不要背模板。

每道题按照：

1. 暴力思考
2. 找重复子问题
3. 定义状态
4. 推导状态转移
5. 初始化
6. 编码
7. 优化

进行。

不会时：

优先回答：

- 当前状态是什么？
- 最后一步发生什么？
- 当前状态来自哪些旧状态？
- 状态是否覆盖所有情况？

---

# 每日安排

每天2-3小时：

- 15分钟：DP分类识别训练
- 30分钟：学习当天DP模型
- 90分钟：完成题目训练
- 30分钟：整理状态定义和错误
- 15分钟：复盘

---

# 第1周：DP基础与背包体系

## Day1：DP入门

学习：

- 递归
- 记忆化搜索
- DP数组
- 状态定义

题目：

- LC509 Fibonacci Number
- LC70 Climbing Stairs
- LC746 Min Cost Climbing Stairs

重点：

回答：

- dp[i]表示什么？
- 为什么依赖前面的状态？

---

## Day2：线性DP

题目：

- LC198 House Robber
- LC213 House Robber II
- LC53 Maximum Subarray

重点：

选择当前 vs 不选择当前。

---

## Day3：二维DP入门

题目：

- LC62 Unique Paths
- LC63 Unique Paths II
- LC64 Minimum Path Sum

重点：

二维状态定义。

---

## Day4：0/1背包

题目：

- LC416 Partition Equal Subset Sum
- LC1049 Last Stone Weight II

重点：

为什么容量倒序。

---

## Day5：完全背包

题目：

- LC322 Coin Change
- LC279 Perfect Squares

重点：

为什么容量正序。

---

## Day6：背包计数

题目：

- LC518 Coin Change II
- LC494 Target Sum

重点：

组合和排列区别。

---

## Day7：第一周总结

完成：

10道DP分类题。

只分析：

- 是否DP
- DP类型
- 状态定义

---

# 第2周：序列DP与状态机DP

## Day8-9：LCS体系

题目：

- LC1143 Longest Common Subsequence
- LC583 Delete Operation
- LC1092 Shortest Common Supersequence

重点：

dp[i][j]。

---

## Day10：编辑距离

题目：

- LC72 Edit Distance

重点：

插入、删除、替换三种转移。

---

## Day11：LIS体系

题目：

- LC300 Longest Increasing Subsequence
- LC673 Number of LIS
- LC354 Russian Doll Envelopes（新增）

重点：

序列增长模型。

连接DP与二分。

---

## Day12-13：状态机DP

题目：

- LC121
- LC122
- LC309
- LC714

重点：

建立：

- hold
- cash
- cooldown

---

## Day14：模拟训练

完成：

5道DP面试题。

要求：

先解释状态，再写代码。

---

# 第3周：高级DP模型

## Day15-17：区间DP

题目：

- LC516 Longest Palindromic Subsequence
- LC312 Burst Balloons
- LC486 Predict Winner

重点：

小区间推出大区间。

LC312首次目标：

理解最后一步思想，不强求一次AC。

---

## Day18-19：树形DP

题目：

- LC337 House Robber III
- LC543 Diameter of Binary Tree
- LC124 Binary Tree Maximum Path Sum
- LC968 Binary Tree Cameras（新增）

重点：

区分：

- 返回值
- 全局答案

---

## Day20：DP优化

学习：

- 空间压缩
- 滚动数组
- 记忆化搜索

---

## Day21：综合测试

随机：

10道DP题。

记录：

- 分类错误
- 状态错误
- 转移错误
- 初始化错误

---

# 第4周：面试强化

目标：

从模板题提升到陌生DP。

每天：

## 前30分钟

分析一道Hard DP：

只回答：

- 状态是什么？
- 转移是什么？
- 为什么正确？

## 中间90分钟

完成Medium DP。

## 最后30分钟

整理错题：

格式：

题目：

DP类型：

错误原因：

正确状态：

状态转移：

复杂度：

---

# 最终能力检查

训练结束后：

看到DP题，5分钟内判断：

- 是否适合DP
- 属于哪类DP
- 状态如何定义
- 转移如何设计
- 是否可以优化空间

最终目标：

从“会做经典DP题”

提升到：

“能够解决陌生DP问题”。
