## step1

最初は問題の意味を勘違いして、1・0・-1を返すものだと思っていた。
```Python
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        visited = set()
        node = head
        while node:
            if node in visited
            node != head:
            visited.add(node)
            node = node.next
            return 1
            visited.add(node)
            node = node.next
            else if node in visited 
            node = head
            visited.add(node)
            node = node.next
            return 0
        return -1
```

### 解答を参考にする
            
```Python        
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
         visited = set()
         node = head
         while node:
            if node is not None:
                return node
                visited.add(node)
                node = node.next
```  

refer to https://qiita.com/kensussu/items/512eadf679f3258ee29e  
調べてみたところ、Pythonにもmatch-caseという書き方があることが分かったが、　

```Python 
match node:
    case None:
        return None
    case _:
```      
match-caseはデータの構造や値に応じて分岐するための構文であり、  
今回のようにノードを追跡して状態を管理する処理には適していないの感じです。

## step2

もう一度やってみる  

whileでnodeがNoneではないことを確認しているのに、  
さらに「node is not None」と判定していたため、その条件は常に真になってしまいます。  
その結果、ループに入った直後にreturnしてしまい、正しく探索できていませんでした。  

```Python        
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
         visited = set()
         node = head
         while node:
            if node is not None:  ＜ーー
                return node
            visited.add(node)
            node = node.next
```  

なぜ null を特別に処理する必要がないのかを調べる  
👉 anwser by GPT  
Pythonの設計では、Noneは特別なものではなく、単に「値が存在しない状態」を表すオブジェクトとして扱われます。  

### 解答
従来の習慣が残っていたため、nullチェックを追加して解答を修正し、正常に動作することを確認
```Python 
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
         visited = set()
         node = head
         while node is not None:
            if node in visited:
                return node
            visited.add(node)
            node = node.next
```

## step3

3回連続で再現できるようになる
```Python 
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
         visited = set()
         node = head
         while node is not None:
            if node in visited:
                return node
            visited.add(node)
            node = node.next
```
