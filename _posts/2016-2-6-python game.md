---
layout:         post
title:          "Python Game"
subtitle:       "designed by myself "
date:           2016-02-06 
author:         "Cunyuan Lu"
header-img:     "img/post-bg-XXXX.jpg"
description:    ""
catalog:        true
mathjax:        false
categories:     
                - python

---
自己编的第一个python程序——猜数字

# 猜数字 
## 游戏规则 
猜一个各个数位不重复的四位数，当你猜对一个数字但数位不对时，电脑告诉你1B，当你猜对一个数字而且数位也是对的时，电脑告诉你1A，A和B不重复计算。比如答案是3408，你输入4807，电脑会回复“1A2B”
## 代码 ##
<p>第一个问题是要让电脑随机取出四个数字不同的四位数，可以用无限循环，判断条件，break来完成
<pre><code>
  ###coding:utf-8 
  import random
  while 1:
   secret=random.randint(1000,9999)
   a=secret/1000
   b=(secret/100)%10
   c=(secret/10)%10
   d=secret%10
   if not(a==b or a==c or a==d or b==c or b==d or c==d):
     break
</code></pre>
<p>然后就是用数学方法取出这四位数四个数位上数字，用a1，b1，c1，d1表示，然后与原数字的a，b，c，d进行比较，得出A和B的值即可
<pre><code>
C=0
   A=0
   if a1 in (a,b,c,d) :
      C+=1
   if b1 in (a,b,c,d) :
      C+=1
   if c1 in (a,b,c,d) :
      C+=1
   if d1 in (a,b,c,d) :
      C+=1
   if a1==a:
      A+=1
   if b1==b:
      A+=1
   if c1==c:
      A+=1
   if d1==d:
      A+=1
   B=C-A
   print A, "A",B,"B"
   if A==4:
      break
   print "please guess again"
print"Congratulations!You 've got the number"
</code></pre>
<p>到这里就完成了大部分内容，最后进行检查，发现当玩家不输入数字或者输入四个相同的数字时，程序无法进行识别。所以我采用了异常处理的方法，判断如果输入的不是int型，就报错。
<pre><code>
while 1:
   while 1:
      try:
         i=int(raw_input("please enter a four-digit number "))
      except:
         print "you must enter a number"
         continue
      a1=i/1000
      b1=(i/100)%10
      c1=(i/10)%10
      d1=i%10
      if a1==0 or a1==b1 or a1==c1 or a1==d1 or b1==c1 or b1==d1 or c1==d1 or a1>=10:
         print "your number is not a four-digit number or it has repeated digits."
      elif b1==0 or c1==0 or d1==0:
         print "number 0 should not be entered"   
      else:
         break
</code></pre>
<p>大功告成，附上全部代码。
<pre><code>
###coding:utf-8
import random
while 1:
   secret=random.randint(1000,9999)
   a=secret/1000
   b=(secret/100)%10
   c=(secret/10)%10
   d=secret%10
   if not(a==b or a==c or a==d or b==c or b==d or c==d):
     break
while 1:
   while 1:
      try:
         i=int(raw_input("please enter a four-digit number "))
      except:
         print "you must enter a number"
         continue
      a1=i/1000
      b1=(i/100)%10
      c1=(i/10)%10
      d1=i%10
      if a1==0 or a1==b1 or a1==c1 or a1==d1 or b1==c1 or b1==d1 or c1==d1 or a1>=10:
         print "your number is not a four-digit number or it has repeated digits."
      elif b1==0 or c1==0 or d1==0:
         print "number 0 should not be entered"   
      else:
         break
   C=0
   A=0
   if a1 in (a,b,c,d) :
      C+=1
   if b1 in (a,b,c,d) :
      C+=1
   if c1 in (a,b,c,d) :
      C+=1
   if d1 in (a,b,c,d) :
      C+=1
   if a1==a:
      A+=1
   if b1==b:
      A+=1
   if c1==c:
      A+=1
   if d1==d:
      A+=1
   B=C-A
   print A, "A",B,"B"
   if A==4:
      break
   print "please guess again"
print"Congratulations!You 've got the number"
</code></pre>
