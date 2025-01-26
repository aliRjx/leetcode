# 2) Add Two Numbers

## First submission (0 ms)
Loop through all the nodes to create a string representation of each ListNode, reverse the resulting string, and then create a new node from the reversed string.

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def makeNumber(self, l: Optional[ListNode]):
        num = ""
        while l != None:
            num += str(l.val)
            l = l.next
        return num

    def addTwoNumbers(
        self, l1: Optional[ListNode], l2: Optional[ListNode]
    ) -> Optional[ListNode]:
        a = self.makeNumber(l1)[::-1]
        b = self.makeNumber(l2)[::-1]
        res = str(int(a) + int(b))[::-1]
        ln = ListNode()
        firstNode = ln
        n = len(res)
        rg = range(n)
        for i in rg:
            ln.val = int(res[i])
            if i < n - 1:
                ln.next = ListNode()
                ln = ln.next
        return firstNode
```
