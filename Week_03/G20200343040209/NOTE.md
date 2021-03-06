学习笔记

题目:
LeetCode_n-ary-tree-preorder-traversal_589

题目解析:
题目是前序遍历一个3叉树
二叉树的前序遍历就是根--左--右，那么3叉树就是
根--子节点(从左到右)了

解题步骤:
1、创建一个list保存结果
2、写一个递归逻辑，其中先判断是否是异常值，异常跳出
然后因为是前序遍历，所以要把当前节点先写入list中
3、随后对children字节点进行循环获取，再行递归判断其深层逻辑


下面是递归解法
然后我看了一下官方解答:
其原理是先创建一个栈，将根节点放入栈中，Python中用列表可以实现栈
然后取出先获取值，然后获取其子节点，因为栈是先进后出，
此题是前序遍历，所以要反向将子节点放入栈，
反向这里，用的是列表切片，然后利用extend写入列表
然后再进行下一轮操作


************我是分割线************
题目:
LeetCode_n-ary-tree-postorder-traversal_590

题目解析:
首先是递归法，后续遍历就是左--右--根，所以跟上一道题相比，
其最主要的区别就是何时进行根节点的写入
前序遍历在进行子节点的遍历前进行根节点的写入，
那么后续遍历则是在子节点全部写入后再进行写入

下面是递归解法:
跟上一道题基本一样，第一种方法是，稍微调整一下根节点和子节点的顺序
然后列表反转就行
然后我看了一下官方解法，也是这样的

解题步骤:
1、创建res保存结果
2、写递归函数
3、如果没有节点，直接返回
4、如果没有子节点，则节点写入res
5、遍历子节点，调用递归函数
6、for循环结束后，将子节点写入res
7、调用递归函数，return res


************我是分割线************
题目:
LeetCode_binary-tree-preorder-traversal_144

题目解析:
还是前序遍历的题目，在回顾一下，前序遍历就是根--左--右

解题步骤:
1、首先堆root进行判断，如果没有结果，直接返回
2、创建一个递归函数
3、如果root值没有结果，则直接返回
4、然后去判断left和right节点有没有参数，有的话直接调用递归函数
5、调用递归函数，返回res列表

然后还是迭代的方法处理


************我是分割线************
题目:
LeetCode_n-ary-tree-level-order-traversal_429

题目解析:
本题是典型的广度优先，在要将同一层的节点放置在一个列表内
就要明确的知晓节点所在的层数，故递归的时候要传入节点和其层数

解题步骤：
1、如果没有root直接返回
2、创建返回列表，创建递归函数
3、如果返回列表与层数相等，则对列表追加一个空列表的元素，
进行新的层处理
4、将节点的值追加到返回列表中
5、遍历该节点的子节点并调用相对应的递归函数
6、调用递归函数，返回结果

************我是分割线************
题目:
LeetCode_lowest-common-ancestor-of-a-binary-tree_236

题目解析:
本体考的是公共祖先，这个题的方法是，用一个列表保存祖先节点
按深度遍历树，如果发现了节点，则返回布尔标记，如果两者都返回True，
则该节点就是祖先节点

但是确实官方的答案没有完全理解，下来还需要再理解理解


************我是分割线************
题目:
LeetCode_construct-binary-tree-from-preorder-and-inorder-traversal_105

题目解析:
前序遍历的顺序是根--左--右
中序遍历的顺序是左--根--右
所以前序遍历的第一个值是根，而其前面的数字就是他的左子树
通过前序遍历获取左子树后，可以从中序遍历获取到左子树的参数


但是具体的逻辑也没完全理解





本周内容较多，主要就是树、堆、递归、分治、回溯。其中分治、回溯确实没有时间详细了解

本周重点知识还是树，图和树的区别是有无环，没有环就是树，反之就是树


树相关的概念如下（来源于知乎：https://zhuanlan.zhihu.com/p/39527221）:

根节点：根节点是一个没有双亲结点的结点，一棵树中最多有一个根节点（如上图的结点A就是根节点）；
边：边表示从双亲结点到孩子结点的链接（如上图中所有的链接）；
叶子结点：没有孩子结点的结点叫作叶子结点（如E、J、K、H和I）；
兄弟结点：拥有相同双亲结点的所有孩子结点叫作兄弟结点（B、C、D是A的兄弟结点，E、F是B的兄弟结点）；
祖先结点：如果存在一条从根节点到结点q的路径，其结点p出现在这条路径上，那么就可以把结点p叫作结点q的祖先结点，结点q也叫做p的子孙结点（例如，A、C和G是K的祖先结点）；
结点的大小：结点的大小是指子孙的个数，包括其自身。（子树C的大小为3）；
树的层：位于相同深度的所有结点的集合叫作树的层（B、C和D具有相同的层，上图的结构有0/1/2/3四个层）；
结点的深度：是指从根节点到该节点的路径长度（G点的深度为2，A—C—G）；
结点的高度：是指从该节点到最深节点的路径长度，树的高度是指从根节点到书中最深结点的路径长度，只含有根节点的树的高度为0。（B的高度为2，B—F—J）；
树的高度：是树中所有结点高度的最大值，树的深度是树中所有结点深度的最大值，对于同一棵树，其深度和高度是相同的，但是对于各个结点，其深度和高度不一定相同

树利用子节点的方法，相较链表等数据结构，可以显著提高查找的效率
树的分类很多，老师上课提到的有二叉树、多叉树、斐波那契树等等
其中二叉树又有完全二叉树、满二叉树、二叉搜索树、平衡二叉树、红黑树
嗯……这是个需要花费很多时间的知识块
二叉树的遍历有三种:
1、前序遍历：根——左——右；
2、中序遍历：左——根——右；
3、后序遍历：左——右——根；
还有层次遍历、广度优先遍历、深度优先遍历等


