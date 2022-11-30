## LinkedList Template and Similar Thoughts

### 合并两个有序链表

```java
ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    // 虚拟头结点
    ListNode dummy = new ListNode(-1), p = dummy;
    ListNode p1 = l1, p2 = l2;
  
    while (p1 != null && p2 != null) {
        // 比较 p1 和 p2 两个指针
        // 将值较小的的节点接到 p 指针
        if (p1.val > p2.val) {
            p.next = p2;
            p2 = p2.next;
        } else {
            p.next = p1;
            p1 = p1.next;
        }
        // p 指针不断前进
        p = p.next;
    }
  
    if (p1 != null) {
        p.next = p1;
    }
  
    if (p2 != null) {
        p.next = p2;
    }
  
    return dummy.next;
}
```

本质上的思想是双指针：

- 找两个数，比较其中较小的数（多个数用堆来做）
- 移动指针，并移动新建的指针（把较小数的点加入堆中）

同向双指针：

- 比较距离最小的点（尽可能让不同指针指向内容一致）

#### question

21 连接链表

23 多个链表连接

88 数组意义上的连接，逆向反转一下

1940 同向双指针

243，244，245 其中244是同向双指针的用法

243的意思是找所有的间隔，本质上也就是排除不可能的情况

244的思想就是排除，排除不可能的情况，例如 i < j -> 移动j使其变得更大，这没什么意义

245 https://leetcode.com/problems/shortest-word-distance-iii/discuss/67095/Short-Java-solution-10-lines-O(n)-modified-from-Shortest-Word-Distance-I 

这种想法也很不错，当此时单词和前一个单词不一致的情况下才去更新，否则没有意义
