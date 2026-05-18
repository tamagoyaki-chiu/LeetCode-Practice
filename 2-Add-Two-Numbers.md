# 進め方

Step1 : 問題を解く。

Step2 : 他の人のPRを参照する。

Step3 : 3回続けてエラーが出ないように書く。ドキュメントを参照する。

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
