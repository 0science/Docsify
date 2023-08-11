# 一、绪论

## 1. 基本概念

![image.png|525](https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307280951600.png)

**数据结构学科**：一门研究非数值计算的程序设计问题中的操作对象，以及他们之间的关系和操作相关问题的学科

**数据**：描述客观事物的符号

**数据元素**：组成数据的，有一定意义的基本单位

**数据项**：一个数据元素由若干数据项组成==(最小单位)==

**数据对象**：相同数据元素的集合

**数据结构**：相互存在一种或多种特定关系的数据元素集合

## 2. 逻辑结构和物理结构

**逻辑结构**：数据对象中数据元素之间的相互关系

**集合结构**：数据元素属于统一集合

![Image00415.jpg|250](https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307280956448.jpg)

**线性结构**：数据元素间是一对一的关系

![Image00421.jpg|325](https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307280956966.jpg)

**树形结构**：数据元素间是一对多的关系

![image.png|375](https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307281008188.png)

**图形结构**：数据元素间是多对多的关系

![image.png|350](https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307281009776.png)

**物理结构**：计算机中的存储形式

**顺序存储结构**：将数据元素存放在地址连续的存储单元里

![image.png|450](https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307281016277.png)

**链式存储结构**：将数据元素存放在任意的存储单元里

![image.png|325](https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307281016084.png)

## 3. 数据类型

**数据类型**：一组性质相同的值的集合及定义在此集合上的一些操作

**原子类型**：不可再分解的基本类型

**结构类型**：由若干个类型组合而成，可再分解

**抽象**：提取出事物具有的普遍性质

**抽象数据类型(ADT)**：一个数学模型及定义在该模型上的一组操作

## 4. 算法

### 4.1 定义

**算法**：解决特定问题求解步骤的描述

### 4.2 特性

1. **输入输出**：算法可以没有输入，但至少有一个输出
2. **有穷性**：算法在执行有限步骤后会自动结束，每一步都在可接受的时间内完成
3. **确定性**：算法的每一步都有确定的含义
4. **可行性**：算法的每一步都可执行，每一步都能在有限执行次数内完成

### 4.3 要求

1. **正确性**：无歧义，正确得到答案，正确反应需求
2. **可读性**：方便阅读、交流和理解
3. **健壮性**：输入不合法时，能做出相关处理
4. **时间效率高**
5. **低存储需求**

### 4.4 效率度量

**事后统计法**：通过设计好的程序和数据，比较运行时间

**事前估计法**：编程前估计算法输入规模

**输入规模**：输入量的多少

### 4.5 复杂度

**时间复杂度**：算法执行时间的增长率随问题规模变化的函数

**大O记法**：用大写的O()表示时间复杂度

推导大O阶：
1. 用1取代加法常数
2. 只保留最高阶
3. 去除最高阶系数

![image.png|675](https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307281048338.png)

**空间复杂度**：算法执行空间的增长率随问题规模变化的函数

# 二、线性表

## 1. 概念

### 1.1 定义

L=( a<sub>1</sub>,a<sub>2</sub>,a<sub>3</sub>,...,a<sub>n</sub>)

**线性表**：n个数据元素的有限序列

**表长**：线性表的元素个数n

**空表**：n=0的线性表

**位序**：数据元素的下标

**表头**：第一个元素

**表尾**：最后一个元素

**前驱**：元素左侧元素

**后继**：元素右侧元素

**直接前驱**：元素左侧相邻元素

**直接后继**：元素右侧相邻元素

> 每个元素都有前驱（除表首）
> 每个元素都有后继（除表尾）

### 1.2 特点

1. 元素个数有限
2. 元素有先后顺序
3. 每个元素都是数据元素
4. 元素大小相同
5. 元素具有抽象性

## 2. 线性表基本操作

```
InitList(&L)       \\初始化表
Length(L)          \\表长
LocalElem(L,e)     \\按值查找
GetElem(L,e)       \\按位查找
ListInsert(&L,i,e) \\插入
ListDelete(&L,i,e) \\删除
PrintList(L)       \\输出
Empty(L)           \\判空
DestroyList(L)     \\销毁
```

## 3. 顺序表

### 3.1 定义

**顺序表**：线性表的顺序存储，用一组地址连续的存储单元依次存储数据元素

**静态分配**：数组大小和空间固定

**动态分配**：在程序执行过程中分配空间

**地址**：存储器中每个存储单元的编号

> 线性表从1开始，数组从0开始

### 3.2 特点

1. 随机访问，可直接查找特定节点
2. 存储密度高
3. 逻辑相邻则物理相邻
4. 插入删除不便

## 4. 顺序表基本操作

### 4.1 插入

最好情况：表尾插入，移动0
最坏情况：表头插入，移动n
平均情况：各点插入概率取平均，移动$\frac{n}{2}$

```
//插入元素 
#define MaxSize 10
typedef struct{
	int data[MaxSize];
	int length;
}SqList;
void ListInsert(SqList &L,int i,int e){
	for (int j=L.length;j>=i;j--)
		L.data[j]=L.data[j-1];
	L.data[i-1]=e;
	L.length++;
}
int main()
{
	SqList L;
	ListInsert(L,3,3);
	return 0;
}
```

```
//判断并插入 
#define MaxSize 10
typedef struct{
	int data[MaxSize];
	int length;
}SqList;
bool ListInsert(SqList &L,int i,int e){
	if(i<1||i>L.length+1)
		return false;
	if(L.length>=MaxSize)
		return false;
	for (int j=L.length;j>=i;j--)
		L.data[j]=L.data[j-1];
	L.data[i-1]=e;
	L.length++;
	return true;
}
```

==顺序表**插入**算法平均复杂度为o(n)==

### 4.2 删除

最好情况：表尾删除，移动0
最坏情况：表头删除，移动n-1
平均情况：各点删除概率取平均，移动$\frac{n-1}{2}$

==顺序表**删除**算法平均复杂度为o(n)==

### 4.3 按值查找/顺序查找

最好情况：元素在表头，比较1次
最坏情况：元素在表尾，比较n次
平均情况：各点查找概率取平均，比较$\frac{n+1}{2}$次

==顺序表**按值查找**算法平均复杂度为o(n)==

## 5. 单链表

### 5.1 定义

**单链表**：线性表的链式存储，用任意一组存储单元存储元素

**头指针**：链表中第一个节点的存储位置

**头结点**：单链表第一个结点前附加的一个结点

### 5.2 特点

1. 无需连续存储单元
2. 指针域会浪费空间
3. 非随机存取，无法直接查找特定节点

## 6. 单链表的基本操作

### 插入

#### 按位序插入

带头结点

不带头结点

####  指定节点前插入

#### 指定节点后插入

### 删除

#### 按位序删除

#### 删除指定节点

### 6.1 头插法

1. 从空表开始，生成一个新节点
2.  将新节点插入到表头
3. 读取顺序与插入顺序相反

时间复杂度o(n)

### 6.2 尾插法

1. 从空表开始，生成一个新节点
2. 添加一个尾指针
3.  将新节点插入到表尾
4. 读取顺序与插入顺序相同

时间复杂度o(n)

### 6.3 按序号查找

1. 从第一个节点出发
2. 顺指针域依次查找，直到找到为止
3. 否则返回NULL

时间复杂度o(n)

### 6.4 按值查找

1. 从第一个节点开始
2. 依次比较各节点的数据域值
3. 找到给定值则返回节点指针
4. 否则返回NULL

时间复杂度o(n)

### 6.5 插入



### 6.6 删除



### 6.7 求表长



## 5. 双链表



## 6. 循环链表



## 7. 静态链表



# 三、栈、队列、数组

