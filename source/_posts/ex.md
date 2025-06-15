---
title: 图论专题三阶段
date: 2025-07-20 18:30:45
categories: note
tags: author
---

### 学习成果

1. **核心知识点**

   - 掌握堆优化Dijkstra模板（时间复杂度 `O((V+E)\log V)`）
   - 理解SPFA判负环的两种方法：**BFS记录松弛次数**（节点入队次数 `\geq V`） 和 **DFS回溯标记**（适用于稀疏图）
   - 新增Floyd算法应用场景：传递闭包、最小环检测

2. **解题记录**

   | 题目来源   | 题号 | 算法           | 结果 |
   | ---------- | ---- | -------------- | ---- |
   | LeetCode   | #743 | 堆优化Dijkstra | AC   |
   | HDU        | 1003 | SPFA+负环检测  | AC   |
   | CodeForces | 95B  | Floyd求最小环  | AC   |

3. **代码模板**

```
import heapq  
def dijkstra(graph, start):  
    dist = [float('inf')] * len(graph)  
    dist[start] = 0  
    heap = [(0, start)]  
    while heap:  
        d, u = heapq.heappop(heap)  
        if d != dist[u]: continue  
        for v, w in graph[u]:  
            if dist[u] + w < dist[v]:  
                dist[v] = dist[u] + w  
                heapq.heappush(heap, (dist[v], v))  
    return dist  
```



