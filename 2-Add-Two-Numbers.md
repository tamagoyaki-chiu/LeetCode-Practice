# 進め方

Step1 : 問題を解く。

Step2 : 他の人のPRを参照する。

Step3 : 3回続けてエラーが出ないように書く。ドキュメントを参照する。

## step 1
### あきらめたコード ### 
一回目の発想としては、まず2つのLinkedListを走査しながら、`node × 10 + 次のnode` のような形で数値へ変換し、その後2つの値を加算することを考えました。
その後、加算結果を反転し、10で割りながら新しいLinkedListを作成しようとしていました。

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
自分の発想を ChatGPT に投げてみたところ
```python
class Solution:
    def addTwoNumbers(self, l1, l2):

        def to_number(node):
            num = 0
            digit = 1

            while node:
                num += node.val * digit
                digit *= 10
                node = node.next

            return num

        total = to_number(l1) + to_number(l2)

        dummy = ListNode()
        current = dummy

        if total == 0:
            return ListNode(0)

        while total > 0:
            digit = total % 10
            current.next = ListNode(digit)

            current = current.next
            total //= 10

        return dummy.next
```
