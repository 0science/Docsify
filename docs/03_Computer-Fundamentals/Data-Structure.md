# 一、绪论

## 1. 基本概念

**数据结构学科**：一门研究非数值计算的程序设计问题中的操作对象，以及他们之间的关系和操作相关问题的学科

**数据**：描述客观事物的符号

**数据元素**：组成数据的，有一定意义的基本单位

**数据项**：一个数据元素由若干数据项组成(**最小单位**)

**数据对象**：相同数据元素的集合

**数据结构**：相互存在一种或多种特定关系的数据元素集合

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307280951600.png" height=250 /></center>

## 2. 逻辑结构和物理结构

**逻辑结构**：数据对象中数据元素之间的相互关系

**集合结构**：数据元素属于统一集合

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307280956448.jpg" height=200 /></center>

**线性结构**：数据元素间是一对一的关系

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307280956966.jpg" height=200 /></center>

**树形结构**：数据元素间是一对多的关系

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307281008188.png" height=200 /></center>

**图形结构**：数据元素间是多对多的关系

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307281009776.png" height=250 /></center>

**物理结构**：计算机中的存储形式

**顺序存储结构**：将数据元素存放在地址连续的存储单元里

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307281016277.png" height=60 /></center>

**链式存储结构**：将数据元素存放在任意的存储单元里

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307281016084.png" height=250 /></center>


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

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/202307281048338.png" height=60 /></center>

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

```
/*将所有的在线性表Lb中但不在La中的数据元素插入到La中*/
void unionL(SqList *La,SqList Lb)
{
	int La_len,Lb_len,i;
	ElemType e;                        /*声明与La和Lb相同的数据元素e*/
	La_len=ListLength(*La);            /*求线性表的长度 */
	Lb_len=ListLength(Lb);
	for (i=1;i<=Lb_len;i++)
	{
		GetElem(Lb,i,&e);              /*取Lb中第i个数据元素赋给e*/
		if (!LocateElem(*La,e))        /*La中不存在和e相同数据元素*/
			ListInsert(La,++La_len,e); /*插入*/
	}
}
```

## 3. 顺序表

### 3.1 概念

**顺序表**：线性表的顺序存储，用一组地址连续的存储单元依次存储数据元素

**静态分配**：数组大小和空间固定

**动态分配**：在程序执行过程中分配空间

**地址**：存储器中每个存储单元的编号

> 线性表从1开始，数组从0开始
> 线性表具备三个属性：起始位置、最大容量、当前长度
> 线性表长度小于数组长度

```
#define MAXSIZE 20          /* 存储空间初始分配量 */
typedef int ElemType;       /* ElemType类型根据实际情况而定，这里为int */
typedef struct
{
	ElemType data[MAXSIZE]; /* 数组，存储数据元素 */
	int length;             /* 线性表当前长度 */
}SqList;
```

### 3.2 优缺点

1. 随机访问，可直接查找特定节点
2. 存储密度高
3. 逻辑相邻且物理相邻
4. 插入删除移动大量元素
5. 造成空间碎片化

## 4. 顺序表基本操作

### 4.1 获取元素 - O(1)

```
#define OK 1
#define ERROR 0
/* Status是函数的类型,其值是函数结果状态代码，如OK等 */
typedef int Status;         

/* 初始条件：顺序线性表L已存在，1≤i≤ListLength(L) */
/* 操作结果：用e返回L中第i个数据元素的值，注意i是指位置，第1个位置的数组是从0开始 */
Status GetElem(SqList L,int i,ElemType *e)
{
	if(L.length==0 || i<1 || i>L.length)
		return ERROR;
	*e=L.data[i-1];

	return OK;
}
```

### 4.2 插入 - O(n)

1. 插入位置不合理，则显示异常
2. 线性表长度大于数组长度，则显示异常或动态增加容量
3. 从最后一个元素开始向前遍历到第个元素，并将其向后移动一位
4. 将元素插入该位置
5. 表长加一

```
/* 初始条件：顺序线性表L已存在,1≤i≤ListLength(L)， */
/* 操作结果：在L中第i个位置之前插入新的数据元素e，L的长度加1 */
Status ListInsert(SqList *L,int i,ElemType e)
{ 
	int k;
	if (L->length==MAXSIZE)  			/* 顺序线性表已经满 */
		return ERROR;
	if (i<1 || i>L->length+1)			/* 当i比第一位置小或者比最后一位置后一位置还要大时 */
		return ERROR;				

	if (i<=L->length)        			/* 若插入数据位置不在表尾 */
	{
		for(k=L->length-1;k>=i-1;k--)  	/* 将要插入位置后的元素向后移一位 */
			L->data[k+1]=L->data[k];
	}
	L->data[i-1]=e;          			/* 将新元素插入 */
	L->length++;

	return OK;
}
```

### 4.3 删除 - O(n)

1. 位置不合理，则显示异常
2. 取出删除元素
3. 从删除元素位置开始遍历到最后一个元素，并将其前移一位
4. 表长减一

```
/* 初始条件：顺序线性表L已存在，1≤i≤ListLength(L) */
/* 操作结果：删除L的第i个数据元素，并用e返回其值，L的长度减1 */
Status ListDelete(SqList *L,int i,ElemType *e) 
{ 
	int k;
	if (L->length==0)               /* 线性表为空 */
		return ERROR;
	if (i<1 || i>L->length)         /* 删除位置不正确 */
		return ERROR;
	*e=L->data[i-1];
	if (i<L->length)                /* 如果删除不是最后位置 */
	{
		for(k=i;k<L->length;k++)	/* 将删除位置后继元素前移 */
			L->data[k-1]=L->data[k];
	}
	L->length--;
	return OK;
}
```

## 5. 单链表

### 5.1 概念

**单链表**：线性表的链式存储，用任意一组存储单元存储元素

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-6-7.jpg" height=120 /></center>

**头指针**：链表中第一个节点的存储位置，有头结点则指向头结点(**必备**)

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-6-8.jpg" height=40 /></center>

**头结点**：单链表第一个结点前附加的一个结点

**数据域**：存储信息元素的域(**p->data**)

**指针域**：存储直接后继的位置(**p->next**)

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-6-10.jpg" height=120 /></center>

**空链表**

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/20230812133616.png" height=120 /></center>

```
/* 线性表的单链表存储结构 */
typedef struct Node
{
    ElemType data;
    struct Node *next;
} Node;
/* 定义LinkList */
typedef struct Node *LinkList;
```

### 5.2 优缺点

1. 无需连续存储单元
2. 指针域会浪费空间
3. 非随机存取，无法直接查找特定节点

## 6. 单链表的基本操作

### 6.1 读取 - O(n)

1. 声明指针p指向头结点，初始化j=1
2. j<i时遍历链表，指针p不断向下移动，++j
3. p为空时，则i结点不存在
4. 查找成功，则返回结点p的数据

```
/* 初始条件：顺序线性表L已存在，1≤i≤
   ListLength(L) */
/* 操作结果：用e返回L中第i个数据元素的值 */
Status GetElem(LinkList L, int i, ElemType *e)
{
    int j;
    LinkList p;            /* 声明一指针p */
    p = L->next;        /* 让p指向链表L的第个结点 */
    j = 1;                 /* j为计数器 */
    /* p不为空且计数器j还没有等于i时，循环继续 */
    while (p && j < i)    
    {
        p = p->next;    /* 让p指向下一个结点 */
        ++j;
    }
    if (!p || j > i)
        return ERROR;      /* 第i个结点不存在 */
    *e = p->data;       /* 取第i个结点的数据 */
    return OK;
}
```

### 6.2 插入 - O(n)

**单链表的插入**
<center><table><tr>
<td><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-8-2.jpg" width=250 /></td>
<td><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-8-3.jpg" width=250 /></td></tr></table></center>

**表头/表尾的插入**
<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-8-4.jpg" width=500 /></center>

1. 声明p指针指向头结点，初始化j=1
2. j<i时遍历链表，指针p不断向下移动，++j
3. p为空时，则i结点不存在
4. 查找成功，则生成空结点s
5. s->data = e
6. s->next = p->next
7. p->next = s
8. 返回成功

```
/* 初始条件：顺序线性表L已存在，1≤i≤
   ListLength(L)， */
/* 操作结果：在L中第i个结点位置之前插入新的数
   据元素e，L的长度加1 */
Status ListInsert(LinkList *L, int i, ElemType e)
{
    int j;
    LinkList p, s;
    p = *L;
    j = 1;
    /* 寻找第i-1个结点 */
    while (p && j < i)                     
    {
        p = p->next;
        ++j;
    }
    /* 第i个结点不存在 */
    if (!p || j > i)
        return ERROR;                      
    /* 生成新结点（C标准函数） */
    s = (LinkList)malloc(sizeof(Node));    
    s->data = e;
    /* 将p的后继结点赋值给s的后继 */
    s->next = p->next;                    
    /* 将s赋值给p的后继 */
    p->next = s;
    return OK;
}
```

### 6.3 删除 - O(n)

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-8-5.jpg" width=400 /></center>

1. 声明p指针指向头结点，初始化j=1
2. j<i时遍历链表，指针p不断向下移动，++j
3. p为空时，则i结点不存在
4. 查找成功，则q = p->next
5.  p->next = q->next
6. e = q->data
7. 释放q结点
8. 返回成功

```
/* 初始条件：顺序线性表L已存在，1≤i≤
   ListLength(L) */
/* 操作结果：删除L的第i个结点，并用e返回其
   值，L的长度减1 */
Status ListDelete(LinkList *L, int i, ElemType *e)
{
    int j;
    LinkList p, q;
    p = *L;
    j = 1;
    /* 遍历寻找第i-1个结点 */
    while (p->next && j < i)    
    {
        p = p->next;
        ++j;
    }
    /* 第i个结点不存在 */
    if (!(p->next) || j > i)
        return ERROR;           
    q = p->next;
    /* 将q的后继赋值给p的后继 */
    p->next = q->next;          
    /* 将q结点中的数据给e */
    *e = q->data;               
    /* 让系统回收此结点，释放内存 */
    free(q);                    
    return OK;
}
```

### 6.4 整表创建

**头插法**

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-9-1.jpg" width=400 /></center>

1. 声明指针p和变量i
2. 初始化空链表L
3. 建立带头结点的空表(头结点指向NULL)
4. 循环：
	1. 生成新节点，并赋值给p
	2. 随机生成数赋值给p的数据域
	3. 将p插入到头结点与新结点之间

```
/* 随机产生n个元素的值，建立带表头结点的单链
   线性表L（头插法） */
void CreateListHead(LinkList *L, int n)
{
    LinkList p;
    int i;
    /* 初始化随机数种子 */
    srand(time(0));                            
    *L = (LinkList)malloc(sizeof(Node));
    /* 先建立一个带头结点的单链表 */
    (*L)->next = NULL;                         
    for (i = 0; i < n; i++)
    {
        /* 生成新结点 */
        p = (LinkList)malloc(sizeof(Node));    
        /* 随机生成100以内的数字 */
        p->data = rand() % 100 + 1;            
        p->next = (*L)->next;
        /* 插入到表头 */
        (*L)->next = p;                        
    }
}
```

**尾插法**

```
/* 随机产生n个元素的值，建立带表头结点的单链
线性表L（尾插法） */
void CreateListTail(LinkList *L, int n)
{
    LinkList p,r;
    int i;
    /* 初始化随机数种子 */
    srand(time(0));                         
    /* 为整个线性表 */
    *L = (LinkList)malloc(sizeof(Node));    
    /* r为指向尾部的结点 */
    r = *L;                                 
    for (i = 0; i < n; i++)
    {
        /* 生成新结点 */
        p = (Node *)malloc(sizeof(Node));   
        /* 随机生成100以内的数字 */
        p->data = rand() % 100 + 1;         
        /* 将表尾终端结点的指针指向新结点 */
        r->next = p;                        
        /* 将当前的新结点定义为表尾终端结点 */
        r = p;                              
    }
    /* 表示当前链表结束 */
    r->next = NULL;                         
}
```

### 6.5 整表删除

1. 声明指针p和q
2. 将头结点赋值给p
3. 循环：
	1. 将下一结点赋值给q
	2. 释放p
	3. 将q赋值给p

```
/* 初始条件：顺序线性表L已存在，操作结果：将L
   重置为空表 */
Status ClearList(LinkList *L)
{
    LinkList p, q;
    /* p指向第一个结点 */
    p = (*L)->next;       
    /* 没到表尾 */
    while (p)             
    {
        q = p->next;
        free(p);
        p=q;
    }
    /* 头结点指针域为空 */
    (*L)->next = NULL;    
    return OK;
}
```

| 线性表 | 存储方式 | 时间性能                         | 空间性能     | 适用 |
| ------ | -------- | -------------------------------- | ------------ | ---- |
| 顺序表 | 连续存储 | 查找O(1)<br>插入O(n)<br>删除O(n) | 预分配空间   |频繁查找，很少插入删除      |
| 单链表 | 链式存储 | 查找O(n)<br>插入O(n)<br>删除O(n) | 自由分配空间 | 元素个数多，变化大     |

## 7. 静态链表

### 7.1 概念

**静态链表**：用数组描述的链表

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-12-1.jpg" height=150 /></center>

```
/* 线性表的静态链表存储结构 */
/* 假设链表的最大长度是1000 */
#define MAXSIZE 1000                     
typedef struct
{
    ElemType data;
    /* 游标（Cursor），为0时表示无指向 */
    int cur;                             
} Component, 
  /* 对于不提供结构struct的程序设计语言，
     可以使用一对并行数组data和cur来处理。 */
  StaticLinkList[MAXSIZE];
```

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-12-3.jpg" height=120 /></center>

```
/* 若备用空间链表非空，则返回分配的结点下标，
   否则返回0 */
int Malloc_SLL(StaticLinkList space)
{
    /* 当前数组第一个元素的cur存的值， */
    /* 就是要返回的第一个备用空闲的下标 */
    int i = space[0].cur;               
    /* 由于要拿出一个分量来使用了，所以我们 */
    /* 就得把它的下一个分量用来做备用 */
    if (space[0].cur)
        space[0].cur = space[i].cur;    
    return i;
}
```

### 7.2 优缺点

1. 插入删除只改游标，不动元素
2. 无法确定表长
3. 无法随机读取

## 8. 静态链表的基本操作

### 8.1 插入

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-12-3.jpg" height=120 /></center>

```
/* 若备用空间链表非空，则返回分配的结点下标，
   否则返回0 */
int Malloc_SLL(StaticLinkList space)
{
    /* 当前数组第一个元素的cur存的值， */
    /* 就是要返回的第一个备用空闲的下标 */
    int i = space[0].cur;               
    /* 由于要拿出一个分量来使用了，所以我们 */
    /* 就得把它的下一个分量用来做备用 */
    if (space[0].cur)
        space[0].cur = space[i].cur;    
    return i;
}
```

```
/* 在L中第i个元素之前插入新的数据元素e  */
  Status ListInsert(StaticLinkList L, int i, ElemType e)
  {
      int j, k, l;
      /* 注意k首先是最后一个元素的下标 */
      k = MAX_SIZE - 1;                   
      if (i < 1 || i > ListLength(L) + 1)
          return ERROR;
      /* 获得空闲分量的下标 */
      j = Malloc_SSL(L);                  
      if (j)
      {
         /* 将数据赋值给此分量的data */
         L[j].data = e;                  
         /* 找到第i个元素之前的位置 */
         for (l = 1; l <= i - 1; l++)    
             k = L[k].cur;
         /* 把第i个元素之前的cur赋值给新元素的cur */
         L[j].cur = L[k].cur;        
         /* 把新元素的下标赋值给第i个元素之前元素的cur */
         L[k].cur = j;                   
         return OK;
     }
     return ERROR;
 }
```

### 8.2 删除

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-12-4.jpg" height=80 /></center>

```
/* 删除在L中第i个数据元素e */
Status ListDelete(StaticLinkList L, int i)
{
    int j, k;
    if (i < 1 || i > ListLength(L))
        return ERROR;
    k = MAX_SIZE - 1;
    for (j = 1; j <= i - 1; j++)
        k = L[k].cur;
    j = L[k].cur;
    L[k].cur = L[j].cur;
    Free_SSL(L, j);
    return OK;
}
```

```
/* 将下标为k的空闲结点回收到备用链表 */
void Free_SSL(StaticLinkList space, int k)
{
    /* 把第一个元素cur值赋给要删除的分量cur */
    space[k].cur = space[0].cur;    
    /* 把要删除的分量下标赋值给第一个元素的cur */
    space[0].cur = k;               
}
```

```
/* 初始条件：静态链表L已存在。操作结果：返回L
   中数据元素个数 */
int ListLength(StaticLinkList L)
{
    int j = 0;
    int i = L[MAXSIZE - 1].cur;
    while (i)
    {
        i = L[i].cur;
        j++;
    }
    return j;
}
```

## 9. 循环链表

**循环链表**：将链表末端空指针改为指向头节点

**空循环链表**
<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-13-3.jpg" height=60 /></center>

**非空循环链表**
<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-13-4.jpg" height=70 /></center>

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-13-5.jpg" height=70 /></center>

**合并链表**
<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-13-7.jpg" height=180 /></center>

```
/* 保存A表的头结点，即① */
p = rearA->next;                    
/*将本是指向B表的第一个结点（不是头结点） */
rearA->next = rearB->next->next;    
/* 赋值给reaA->next，即② */
q = rearB->next;
/* 将原A表的头结点赋值给rearB->next，即③ */
rearB->next = p;                    
/* 释放q */
free(q);
```

## 10. 双向链表

**双向链表**：单链表的每个结点中设置一个指向前驱的指针域

**空双向链表**
<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-14-3.jpg" height=80 /></center>

```
/* 线性表的双向链表存储结构 */
typedef struct DulNode
{
    ElemType data;
    struct DuLNode *prior;    /* 直接前驱指针 */
    struct DuLNode *next;     /* 直接后继指针 */
} DulNode, *DuLinkList;
```

### 10.1 插入
<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-14-5.jpg" height=200 /></center>

```
/* 把p赋值给s的前驱，如图中① */
s->prior = p;          
/* 把p->next赋值给s的后继，如图中② */
s->next = p->next;     
/* 把s赋值给p->next的前驱，如图中③ */
p->next->prior = s;    
/* 把s赋值给p的后继，如图中④ */
p->next = s;
```

### 10.2 删除

<center><img src="https://djm-1317856319.cos.ap-shanghai.myqcloud.com/djm-1317856319/3-14-6.jpg" height=150 /></center>

```
/* 把p->next赋值给p->prior的后继，如图中① */
p->prior->next = p->next;     
/* 把p->prior赋值给p->next的前驱，如图中② */
p->next->prior = p->prior;    
/* 释放结点 */
free(p);
```

