
```python
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        list1val = l1
        list2val = l2
        while list1val is not None:
            list1val = list1val.val * 10 + list1val.val.next
            continue
        while list2val is not None:
            list2val = list1val.val * 10 + list2val.val.next
            continue
        list12total = list1val + list2val
        newlist12total = list12total / 10
```
