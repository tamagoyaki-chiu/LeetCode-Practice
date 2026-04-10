最初のチャレンジでは、よく分からず、何も書けませんでした。

一度解答を見て、理解しようと思い、Pythonの公式ドキュメントで関連するメソッドについて調べました。
refer to 
https://github.com/fuga-98/arai60/pull/2

##解答##

```Python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        visited = set()
        node = head
        while node:
            if node in visited:
                return True
            visited.add(node)
            node = node.next
        return False
```

その後、もう一度自分で書いてみましたが、正しく書けませんでした。
```Python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        start = hasCycle(head)
        reply = head
            if 
                start = head
                    return ture
            head = head.next

            
            return false
        break
```
解答と見比べて確認したところ、set() を呼び出す必要があることを完全に忘れていました。

その後、もう一度自分で書いてみたところ、ほぼ完成に近い状態でしたが、
コロン（:）の書き忘れや、TrueとFalseは先頭を大文字にする必要がある点に気づきませんでした。
また、node と now を混同して使用してしまう場面もありました。
```Python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        visited = set()
        now = head
        while node
            if now in visited
                now = visited #この行は誤りです。node と visited は本質的に異なるため、コンパイル（実行）は通りますが、実際には不要であり、書くべきではありません。
                return true
            visited.add(node)
            now = node.next
        return false
```

### 3回連続で再現できるようになるまで練習

所要時間の記録：

1回目：1:40
2回目：1:12
3回目：1:05

```Python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        visited = set()
        node = head
        while node:
            if node in visited:
                return True
            visited.add(node)
            node = node.next
        return False
```
