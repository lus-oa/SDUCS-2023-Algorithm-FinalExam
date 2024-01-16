## 山东大学计算机学院2023研究生高级算法设计与分析期末考试题

### 作业题
1.对顶点覆盖问题的图做如下限制：每个顶点的度不超过3。请设计从3SAT问题到此特殊的顶点覆盖问题的多项式变换，证明该问题是NPC的。设计该特殊顶点覆盖问题的常数近似算法，分析并证明近似性能比。
2.重叠图是定义如下：每个点对应数轴上的一个区间，两个点之间有边当且仅当它们对应的区间是相交的，且任何一个都不完全包含另一个。请设计多项式时间的精确算法，计算重叠图的最大独立集，分析算法的时间复杂度。给出一个至少10个点的实例, 并用你的算法求解。
3。广义划分问题的定义如下：给定n个正整数S={a1，a2,…, an}，是否存在一些整数S’，满足$\sum_{a_{i}}\$∑_(a_i∈s^')▒a_i =c⋅∑_(a_i∈s-s^')▒a_i ，其中c是正整数，是个常数。请构造从划分问题到广义划分问题的多项式变换，证明广义划分问题是NPC的。请设计广义划分问题的拟多项式时间算法。

当每个顶点的度限制为不超过 3 时，设计一个常数近似算法来解决顶点覆盖问题。

### 详细解释算法过程：

给定一个图 $G = (V, E)$，其中每个顶点的度不超过 3。

1. **初始化**：创建一个空的顶点覆盖集合 `cover = []`。
2. **遍历所有的边**：
   - 对于每条边 $(u, v) \in E$，检查 $u$ 和 $v$ 是否已经在 `cover` 中：
     - 如果 $u$ 不在 `cover` 中，则将 $u$ 添加到 `cover` 中。
     - 如果 $v$ 不在 `cover` 中，则将 $v$ 添加到 `cover` 中。
     - 如果 $u$ 和 $v$ 都在 `cover` 中，跳过当前边，因为它已经被覆盖了。
3. **返回结果**：`cover` 即为近似的顶点覆盖集合。

### 解释算法原理：

这个算法采用了贪心的策略：遍历图中的每条边，并检查边连接的两个顶点是否已经在 `cover` 中。如果不在，将它们中的一个或两个顶点加入 `cover` 中，以确保至少有一个顶点覆盖这条边。

由于每个顶点的度不超过 3，因此每条边最多连接两个新的顶点。因此，在遍历所有边的过程中，我们至多选择两个顶点来覆盖一条边。这确保了输出的顶点覆盖大小不超过最优解的两倍。

### 举例说明：

假设有一个图 G 包含如下边的集合 E：

- E = { (1, 2), (1, 3), (2, 3), (3, 4), (4, 5) }

使用算法过程如下：

1. 初始时 `cover = []`。
2. 对于每条边：
   - (1, 2)：1 和 2 都不在 `cover` 中，所以将 1 和 2 添加到 `cover` 中。
   - (1, 3)：1 在 `cover` 中，但 3 不在，所以将 3 添加到 `cover` 中。
   - (2, 3)：2 在 `cover` 中，但 3 已经在 `cover` 中了，所以跳过这条边。
   - (3, 4)：3 和 4 都不在 `cover` 中，所以将 3 和 4 添加到 `cover` 中。
   - (4, 5)：4 不在 `cover` 中，但 5 不在 `cover` 中，所以将 4 和 5 添加到 `cover` 中。

最终得到 `cover = [1, 2, 3, 4, 5]`，它是一个顶点覆盖，覆盖了所有的边。

该算法的近似性能比为 2，因为它最多选择两个顶点来覆盖一条边，所以输出的顶点覆盖大小不超过最优解的两倍。
