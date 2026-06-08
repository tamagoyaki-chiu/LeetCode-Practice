# 進め方

Step1 : 問題を解く。

Step2 : 他の人のPRを参照する。

Step3 : 3回続けてエラーが出ないように書く。ドキュメントを参照する。

## step 1
### あきらめたコード ### 
一回目の発想としては、まず2つのLinkedListを走査しながら、`node × 10 + 次のnode` のような形で数値へ変換し、その後2つの値を加算することを考えました。
その後、加算結果を反転し、10で割りながら新しいLinkedListを作成しようとしていました。

構文への理解が浅かったため、最終的にはうまく実装まで落とし込むことができませんでした。

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
## step 2
### 解答を参考にする

まず自分の発想を ChatGPT に投げてみたところ
わかりやすいと思います、問題も解決できそうですが、あまり良い解法ではない気がします。

原因：
数値に変換する処理が必要になり、実装が回りくどくなる。
Python では問題ないが、他の言語では整数の桁数制限によりオーバーフローする可能性がある。

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

他の方の PR を見てみる
refer to 

https://github.com/wanwan87/LeetCode_arai60/pull/5/changes  
https://github.com/takao-Tokunaga/leetcode/pull/5/changes  
https://github.com/rimokem/arai60/pull/5/changes  

どちらかの桁がまだ残っている、または繰り上がり（carry）が残っている限り、処理を続る。  

```python
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode()
        node = dummy
        carry = 0
        while l1 is not None or l2 is not None or carry != 0:
            if l1 is not None:
                value1 = l1.val
            else:
                value1 = 0
            if l2 is not None:
                value2 = l2.val
            else:
                value2 = 0 
            tmp = value1 + value2 + carry
            carry = tmp // 10
            digit = tmp % 10
            node.next = ListNode(digit)
            node = node.next
            if l1 is not None:
                l1 = l1.next
            if l2 is not None:
                l2 = l2.next
        return dummy.next
```

```python
        dummy = ListNode()
        sum_node = dummy
        node1 = l1
        node2 = l2
        carry = 0
        while node1 is not None or node2 is not None:
            value1 = node1.val if node1 is not None else 0
            value2 = node2.val if node2 is not None else 0

            carry, digit = divmod(value1 + value2 + carry, 10)
            sum_node.next = ListNode(digit)

            sum_node = sum_node.next
            node1 = node1.next if node1 is not None else None
            node2 = node2.next if node2 is not None else None

        if carry != 0:
            sum_node.next = ListNode(carry)

        return dummy.next
```
