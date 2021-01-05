# Intro

Learning notes of python 算法

# original books

https://github.com/r1551z/ebooks

# Chapter 2
注意python中float的运算精度问题：整数是天然精确的，
但是浮点数天然是近似值。

减法运算会损失很多有效数字

example：see the difference between
```python
sqrt(x+1）-sqrt(x)

1/(sqrt(x+1)+sqrt(x))
```
后者更加精确

解决方法

1. 使用其他模块: decimal & sage

2. 避免使用减法，利用表达式的变化达到这个目的


# Chapter 3 

## recursion and devide & conquer

1. 递归的对应关系：

T(n)=aT(n/b)+f(n)

if we want on the leaf node, the question has a complexity of 1, and
on the root level complexity is n, then we have

b^height of tree * 1=n

Thus height of tree = log(n, b)

so the width of tree, or number of leaves = a^(log(n, b))


2. 三个一刀切解决的情况

a.大部分操作都在根节点上， 即在整体操作的表达式中占据主体地位. i.e.,
f(n)的增长快于叶节点数的增长。表达式如下


```
a * f(n/b)<=cf(n), c<1
```

or
```
f(n) belong to Sigma(n^(log(a+eta,b)
```

换言之，f(n)的增长比log要快一些,或者说，T(n)=theta(f(n))

      proof:
      
      1. we know f=theta(g) means there exists n0, c1, and c2,
      thus for any n>n0, 
      
      c1g(n)<=f(n)<=c2g(n)
  
  
      assuming that T(n/b)=theta(f(n/b)), we then have
      
      T(n)=aT(n/b)+f(n), and there exists n0, c1, and c2,
      thus for any n>n0, 
      
      therefore, 
      
      if for n=1, we have
      
      c2 f(1) <=T(1) <= c1 f(1) (which is possible, since they are all constant)
      
      then we prove that for T(n), we have T(n)<=c^log(n, b)*c1 f(n) + f(n)
      
      Assume it holds on T(n/b), then on T(n), we have 
      
      f(n)<=T(n)=aT(n/b) + f(n) <= c^ log (n/b, b) f(n/b)+f(n) <= c ^ (log(n, b)-1) * c * f(n) + f(n) = c^log(n, b) * f(n)+f(n);
      
      so T(n)<=c^log(n, b)*c1 f(n) + f(n) is proved.
      
      Due to c<1, if n is large enough, c^log(n, b) can be very small, thus the T(n) = theta (f(n))
      
 2. condition 2
 
 渐进表达式的运算时间以叶节点占大多数，T(n) = theta(n^(log(a, b)),
condition为f(n)=theta(n^(log(a-eta,b))
 
 3。 condition 3 
 
 各层操作量相同。 即T(n)=theta(n^(log(a,b))* log n)), condition为f(n)=theta(n^(log(a,b))
 
