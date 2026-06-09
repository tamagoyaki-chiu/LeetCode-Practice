# 進め方

Step1 : 問題を解く。

Step2 : 他の人のPRを参照する。

Step3 : 3回続けてエラーが出ないように書く。ドキュメントを参照する。

## step 1
### あきらめたコード
最初は文字列の中で括弧の組み合わせを判定したり、先頭と末尾が対応しているかを確認したりする方法を考えていました。  
その結果を比較して True / False を返そうと思ったのですが、時間切れになってしまいました。  
また、Stack を使う発想にはたどり着いたものの、どのように変数を用意して実装すればよいかにまだ慣れておらず、最後まで解き切ることができませんでした。  

```python
class Solution:
    def isValid(self, s: str) -> bool:
        if str != "":
            when str[0] is ")" or "}" or "]"
                return false
            when str[0] is "(" or "{" or "["
                case 1 
                case 2 
                case 3 str[-1]
```

## step 2
### 他の方の 解答/PR を見てみる  
refer to  
https://github.com/takao-Tokunaga/leetcode/pull/6/changes　　
https://github.com/nicah4o/arai60/pull/6/changes
https://github.com/wanwan87/LeetCode_arai60/pull/6/changes
https://neetcode.io/solutions/valid-parentheses  


### Stack
どちらも Stack を使った解法ですが、  
前者は「閉じ括弧 → 開き括弧」の対応表を使い、  
後者は「開き括弧 → 閉じ括弧」の対応表を使っています。  
後者は空の Stack に対して pop() しないように、番兵（sentinel）として "#" を入れている点が特徴です。  
個人的には一つ目の書き方のほうが好きです。空の Stack を考慮するための特別な工夫がいらないの感じ。　　

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        closeToOpen = { ")" : "(", "]" : "[", "}" : "{" }

        for char in s:
            if char in closeToOpen:
                if stack and stack[-1] == closeToOpen[char]:
                    stack.pop()
                else:
                    return False
            else:
                stack.append(char)

        return True if not stack else False
```

```python
class Solution:
    def isValid(self, s: str) -> bool:
        open_to_close = {"(" : ")", "{" : "}", "[" : "]"}
        stack = ["#"]
        for char in s:
            if char in open_to_close:
                stack.append(char)
                continue
            last_open_brackets = stack.pop()
            if char != open_to_close.get(last_open_brackets,""):
                return False
        return stack == ["#"]
```

### Dictionary
自分のStep 1 発想は Stack というより Dictionary に近いものでした。  
Stack の練習にはなりませんでしたが、一応これでも解法の一つではあると思います。  
```python
class Solution:
    def isValid(self, s: str) -> bool:
        while '()' in s or '{}' in s or '[]' in s:
            s = s.replace('()', '')
            s = s.replace('{}', '')
            s = s.replace('[]', '')
        return s == ''
```

## step 3  
3回続けてエラーが出ないように書く  

```python

```
