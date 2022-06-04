# Document

本教程中的所有代码将会用三种形式呈现：入语言代码，英语描述（与中文含义一一对应）以及等效的Scheme代码。

## 语言对照表

| 关键词  | 解释                                               |
| ------- | -------------------------------------------------- |
| 入      | lambda                                             |
| 得      | .                                                  |
| 取...者 | 求值（f 取 x 者  ->  f  x）                        |
| 之      | 反向求值（x之f  ->  f  x）                         |
| 「 」   | 多个字符组成的变量名需要用「 」包括（「 变量甲」） |
| “”      | 字符串需要用双引号包括                             |

## 一阶函数

### 简单算术

```入语言
令算术法甲为
   入 甲乙丙
     得 〔甲之平方 〔乙 二 取积者〕丙〕之和
令平方为
   入 甲
     得 甲甲之积
一二三取算术法甲者
	即 结果为八
```


```scheme
(define (sum1 x y z)
  (+ (square x) (* y 2) z))
(define (square x)
  (* x x))
(sum1 1 2 3)
;结果为8
```

### 构造复合数据结构

```入语言
令有序对为
   入 甲乙『取值』得
      当『取值』壹取等者 得甲
      当『取值』贰取等者 得乙
令前者为
   入 某序对 得
      壹之有序对
令后者为
   入 某序对 得
      贰之有序对
五六之有序对之前者 即五
```

```scheme
(define (pair x1 x2 pick)
  (cond ((= pick 1) x1)
        ((= pick 2) x2)))

(define (car x) (x 1))
(define (cdr x) (x 2))
(pair 5 6);5
```