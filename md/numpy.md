### Introduction to numpy 
```python
import numpy as np
```
***
*1.创建数组*
```python
#维数与中括号对数有关
print(np.array([1,2,3]))
#1 dimension [1,2,3]
print(np.array([[1,2,3]]))
#2 dimensions [[1,2,3]]
```
***

*2.转置矩阵*
```python
#不改变维度，一维不变
a = np.array([1,2,3])
print(np.transpose(a))
#[1,2,3]
b = np.array([[1,2,3]])
print(b.T)
#[[1]
# [2]
# [3]]
```

*3.矩阵属性*
```python
#1 dimension
a = np.array([1,2,3])
print(np.shape(a))
#(3,) 
#2 dimensions
b = np.array([[1,2,3],[4,5,6]])
print(np.shape(b))
#(2,3)
#改变属性
c = b.reshape(3,2)
print(c)
#[[1 2]
# [3 4]
# [5 6]]
#需要注意的是，原先的矩阵不会发生改变，需要重新赋一个
```

*4.矩阵相乘*
```python
a = np.array([[1,2,3]])
b = np.array([[4,5,6]])
print(np.dot(a.T,b))
#[[ 4  5  6]
# [ 8 10 12]
# [12 15 18]]
#注意满足列数等于行数
data = np.transpose(np.array([[1, 2], [1, 3], [2, 1], [1, -1], [2, -1]]))
th = np.array([[1], [1]])
th0 = -2
def signed_dist(x, th, th0):
    return (np.dot(th.T, x) + th0) / length(th)
#注意，这里是矩阵整体运算，而不是单指某个元素
```

*5.返回判断正负性*
```python
#正数返回1，零返回0，负数返回-1
print(np.sign(1))
# 1
print(np.sign(0))
# 0
print(np.sign(-1))
# -1
```

*6.求和*
```python
a = np.array([[1,2,3],[4,5,6]])
print(np.sum(a))
#21 不加参数为全部求和
print(np.sum(a,axis = 0))
#[5,7,9]
#看最外面的中括号，里面的元素为[1,2,3],[4,5,6],两个列表之间进行操作
print(np.sum(a,axis = 1))
#[6,15] 
#看最里面的中括号，里面的元素是不是一个为1，2，3.另一个是4，5，6，那元素之间进行求和，两者互不干扰
#同样的axis原则适用于np其他函数
test = [[ True  True False False  True]]
print(np.sum(test,axis = 1))
#[3]
print(np.sum(test,axis = 1,keepdims = True))
#[[3]]
#记住sum之后会清除axis确定的维度，如果需要保留，需要将keepdims = True
```

*7.索引与切片*
```python
a = np.array([[1,2,3],[4,5,6]])
print(a[0])
#[1,2,3] 
#可以理解为两个小列表作为一个大列表的元素
print(a[0:1])
#[[1,2,3]]
print(a[:,2:])
#[[3]
# [6]]
#注意，如果中间加逗号，则意味着前面对行进行操作，后面对列进行操作
print(a[:,0])
#[1,4]
#注意，如果单独用整数索引或者切片，数组会保持原来的维度，但如果两者混用，则会导致降维
```

*8.行向量与列向量*

```python
#row vector
a = np.array([[1,2,3,4]])
#column vector
b = np.array([[1],[2],[3]])
#接收一个列表变为行向量
t = np.array([value_list])
#接收一个列表变为列向量
q = t.T or np.transpose(t)
```

*9.数组的长度*
```python
a = np.array([[1,2,3]])
print(np.sum(a * a)**0.5)
#3.7416573867739413 
#与求向量的模类似
```

*10.布尔值判断*
```python
g = np.array([[1.,-1.,1.,1.,-1.]])
labels = np.array([[1.,-1.,-1.,-1.,-1.]])
print(g == labels)
#[[ True  True False False  True]]
#需要注意的是，numpy对布尔值也可以求和，
print(np.sum(g == labels))
#3
True = 1,False = 0
#还可以一对多布尔值判断
print(np.array([[1,2,3,4]]) == 1)
#[[ True False False False]]
```

*11.返回最大值索引*
```python
a = np.argmax(np.array([[1,2,3,4,5,6]]))
print(a)
#5
```

*12.分割处理*
```python
a = np.array([[1,2,3,4,5],[6,7,8,9,0]])
print(np.array_split(a,5,axis = 1))

#[array([[1],
#        [6]]), array([[2],
#        [7]]), array([[3],
#        [8]]), array([[4],
#        [9]]), array([[5],
#        [0]])]
#axis不再赘言，split之后会产生列表，跟Python语法一样的
```

*13.合成*

```python
a = np.array([[1]])
b = np.array([[2]])
print(np.concatenate((a,b),axis = 1))
#[[1 2]]
b = np.array([[1,2,3,4,5],[6,7,8,9,0]])
b_div = np.array_split(b,5,axis = 1)

print(np.concatenate(b_div[0:3]+b_div[4:],axis = 1))
#[[1 2 3 5]
# [6 7 8 0]]
```