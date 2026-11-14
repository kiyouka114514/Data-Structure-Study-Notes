# 概念
**顺序性+平衡性**
前提：必须满足[[二叉排序树的概念及插入与查找]]
平衡因子：该结点的左右子树的高度差
AVL树的平衡因子的绝对值 $\le$ 1

一个结点的高度=max(左孩子的高度，右孩子的高度)+1

# 旋转

当AVL树插入新的结点时
![[平衡二叉树（AVL树）的概念和旋转 失衡状态图解]]

此时应该通过**旋转**来维护AVL树

## **右旋**

![[平衡二叉树（AVL树）的概念和旋转 右旋图解]]
```cpp
//右旋
AVLTree Right(AVLNode* x){
    AVLNode *y = x->l;
    //右旋链接
    x->l = y->r;    //1
    y->r = x;       //2
    //调整高度
    x->h = maxx(Get_h(x->l), Get_h(x->r)) + 1;
    y->h = maxx(Get_h(y->l), Get_h(y->r)) + 1;

    return y;   //返回调整之后的根结点
}
```


## **左旋**
![[平衡二叉树（AVL树）的概念和旋转 左旋图解]]

```cpp
//左旋
AVLTree Left(AVLNode* x){
    AVLNode *y = x->r;
    //左旋链接
    x->r = y->l;     //1
    y->l = x;        //2
    //调整高度
    x->h = maxx(Get_h(x->l), Get_h(x->r)) + 1;
    y->h = maxx(Get_h(y->l), Get_h(y->r)) + 1;

    return y; // 返回调整之后的根结点
}
```