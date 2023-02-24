# 21. Merge Two Sorted Lists
#lc/easy #lc/success

## Question
You are given the heads of two sorted [[linked-list|linked lists]] `list1` and `list2`.

Merge the two lists in a one **sorted** list. The list should be made by splicing together the nodes of the first two lists.

Return _the head of the merged linked list_.

###### Example 1:
```
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

###### Example 2:
```
Input: list1 = [], list2 = []
Output: []
```

###### Example 3:
```
Input: list1 = [], list2 = [0]
Output: [0]
```

###### Constraints:
-   The number of nodes in both lists is in the range `[0, 50]`.
-   `-100 <= Node.val <= 100`
-   Both `list1` and `list2` are sorted in **non-decreasing** order.

---
## Solution
### Initial Solution

```typescript
function mergeTwoLists(list1: ListNode | null, list2: ListNode | null)
	: ListNode | null 
{
    let sum = new ListNode(0);
    let head = sum;
    
    while (list1 && list2) {
        if (list1.val <= list2.val) {
            sum.next = new ListNode(list1.val);
            list1 = list1.next;
        } else {
            sum.next = new ListNode(list2.val);
            list2 = list2.next;
        }
        sum = sum.next;
    }
    
    if (list1) sum.next = list1;
    if (list2) sum.next = list2;
    
    return head.next
};
```

###### Analysis
>[!success]
> - Runtime: 151 ms, faster than 9.23% of TypeScript online submissions for Merge Two Sorted Lists.
> - Memory Usage: 44.9 MB, less than 67.63% of TypeScript online submissions for Merge Two Sorted Lists.

### LeetCode Solution
>[!Note]
>Premium required

### User Solution
Most solutions are fairly similar approaches.