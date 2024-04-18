---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://blog.csdn.net/boysoft2002/article/details/129409557","title":"C++ 实现的二叉树创建和遍历，超入门邻家小女也懂了_c++ 二叉树的建立与遍历 - CSDN 博客","summary":null,"Created-Date":"2024-01-05 16:42:40","Modified-Date":"2024-04-18 11:52:12","permalink":"/Z01_InBox/SimpRead/C++ 实现的二叉树创建和遍历，超入门邻家小女也懂了_c++ 二叉树的建立与遍历 - CSDN 博客/","dgPassFrontmatter":true}
---


# A. 二叉树
![](https://img-blog.csdnimg.cn/67cbff65fbb1487992282f276705cdac.png)



## A.1. 二叉树 

树（Tree）是 n(n≥0) 个节点的有限集。在任意一棵树中有且仅有一个特定的称为根（Root）的节点；当 n＞1 时，其余节点可分 m(m＞0) 为个互不相交的有限集 T1,T2,...,Tm；其中每一个集合本身又是一棵树，并且称为根的子树（SubTree）。

二叉树（Binary Tree）是一种特殊的有序树型结构，所有节点最多只有 2 棵子树。

### A.1.1. 特点

（1）每个节点至多有两棵子树；  
（2）二叉树的子树有左右之分；  
（3）子树的次序不能任意颠倒（有序树）。

### A.1.2. 性质

（1）二叉树的第 i 层上至多有 2^(i-1) 个节点（i≥1）。  
（2）深度为 h 的二叉树中至多含有 2^h-1 个节点 (h≥1)。  
（3）若在任意一棵二叉树中，有 n0 个叶子节点，有 n2 个度为 2 的节点，则必有 n0=n2+1。  
（4）具有 n 个节点的满二叉树深为 log2n+1。  
（5）若对一棵有 n 个节点的完全二叉树进行顺序编号（1≤i≤n），  
那么，对于编号为 i（i≥1）的节点：   
　　当 i=1 时，该节点为根，它无双亲节点。  
　　当 i>1 时，该节点的双亲节点的编号为 i/2。  
　　若 2i≤n，则有编号为 2i 的左节点，否则没有左节点。  
　　若 2i+1≤n，则有编号为 2i+1 的右节点，否则没有右节点。

## A.2. 二叉树的创建

### A.2.1. 声明

```
struct TreeNode {
    int val;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : val(x), left(NULL), right(NULL) {}
};
```


在 C/C++ 语言中，经常使用 NULL 来表示空指针。

NULL 在头文件里的定义：

```
#ifndef NULL
    #ifdef __cplusplus
        #define NULL 0
    #else
        #define NULL ((void *)0)
    #endif
#endif
```

即在 C++ 中，NULL 被定义为整形常量 0，而在 C 中，被定义为无类型指针常量 (void*) 0 

**C++11 标准增加了新的关键字 nullptr，表示空指针。**

建议使用 C++11 及以上版本的用以下的二叉树声明：

```cpp
struct TreeNode {
    int val;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};
```

### A.2.2. 创建

```cpp
#include <iostream>
 
struct TreeNode {
    int val;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};
 
int main() {
	
    TreeNode* root = new TreeNode(1);
    root->left = new TreeNode(2);
    root->right = new TreeNode(3);
    root->right->left = new TreeNode(4);
    root->right->right = new TreeNode(5);
 
    return 0;
}
```

 创建结果：

![](https://img-blog.csdnimg.cn/563563a1125d46588882592e07e0e99f.png)

### A.2.3. 成员运算符 ->

指向结构体或对象的指针访问其内成员。当一个指针指向一个结构体、对象时，称之为结构体指针或对象指针。结构体指针或对象指针中的值是所指向的结构体或对象的首地址。通过结构体指针或对象指针即可访问该结构体或对象。

结构体指针变量定义的一般形式为：

```cpp
struct 结构体类型名 *指针名; //结构体指针
struct 结构体类型名 *指针名 = &一个结构体的名字; //结构体指针并赋初值
struct 结构体类型名 *指针名 = new struct 结构体类型名; //结构体指针并用new申请内存
struct 结构体类型名 *指针名 =(struct 结构体类型名 *)malloc(sizeof(struct 结构体类型名)) 
//结构体指针并用malloc申请内存 使用应包含头文件stdlib.h
```

子树 root->left, root->right 还可以 **.** 运算表示，也是成员运算符。两者的区别：

点运算符 `.` 左边必须用 `*` 寻址运算符取到指针 root 指向的结构或者对象实体，如 `(*root)`；

对比箭头状的成员运算符 `->` ，其左边必须为结构体指针，如 root。



```cpp
    TreeNode* root = new TreeNode(1);
    (*root).left = new TreeNode(2);
    (*root).right = new TreeNode(3);
    (*(*root).right).left = new TreeNode(4);
    (*(*root).right).right = new TreeNode(5);
```

### A.2.4. 批量创建

上例只是创建 5 节点，如要建更多节点，这样一个一个增加节点写起来复杂；可以用数组或容器等可迭代数据类型批量来创建。

#### A.2.4.1.  完全二叉树的创建

```
        _______1________
       /                \
    __2__             ___3___
   /     \           /       \
  4       5        _6        _7
 / \     / \      /  \      /  \
8   9   10  11   12   13   14   15
```

代码：

```cpp
#include <iostream>
#include <vector>
using namespace std;
 
struct TreeNode
{
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};
 
TreeNode* buildTree(vector<int>& nums)
{
	// 空树
	if (nums.empty()) return nullptr;

	
    TreeNode *root = new TreeNode(nums.front());
    vector<TreeNode*> q = {root};
    int i = 1;
    while(!q.empty() && i < nums.size())
    {
        TreeNode *cur = q.front();
        q.assign(q.begin() + 1, q.end());
        if(i < nums.size())
        {
            cur->left = new TreeNode(nums[i++]);
            q.push_back(cur->left);
        }
        if(i < nums.size())
        {
            cur->right = new TreeNode(nums[i++]);
            q.push_back(cur->right);
        }
    }
    return root;
}
 
int main()
{
    vector<int> nums = {1,2,3,4,5,6,7,8,9,10,11,12,13,14,15};
    TreeNode *root = buildTree(nums);
 
    return 0;
}
```

创建后，可以用代码把二叉树打印出来以供验证： 

#### A.2.4.2. [打印二叉树](https://so.csdn.net/so/search?q=%E6%89%93%E5%8D%B0%E4%BA%8C%E5%8F%89%E6%A0%91&spm=1001.2101.3001.7020)

```cpp
#include <iostream>
#include <vector>
using namespace std;
 
struct TreeNode
{
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};
 
TreeNode* buildTree(vector<int>& nums)
{
	if (nums.empty()) return nullptr;
    TreeNode *root = new TreeNode(nums.front());
    vector<TreeNode*> q = {root};
    int i = 1;
    while(!q.empty() && i < nums.size())
    {
        TreeNode *cur = q.front();
        q.assign(q.begin() + 1, q.end());
        if(i < nums.size())
        {
            cur->left = new TreeNode(nums[i++]);
            q.push_back(cur->left);
        }
        if(i < nums.size())
        {
            cur->right = new TreeNode(nums[i++]);
            q.push_back(cur->right);
        }
    }
    return root;
}
 
void levelOrderPrint(TreeNode* root)
{
    if(!root) return;
    vector<TreeNode*> q = {root};
    while(!q.empty())
    {
        int size = q.size();
        for(int i = 0; i < size; i++)
        {
            TreeNode *cur = q.front();
            q.assign(q.begin() + 1, q.end());
            cout << cur->val << " ";
            if(cur->left)
                q.push_back(cur->left);
            if(cur->right)
                q.push_back(cur->right);
        }
        cout << endl;
    }
}
 
int main()
{
    vector<int> nums;
    for (int i = 0; i < 15; i++)
    	nums.push_back(i+1);   
    TreeNode *root = buildTree(nums);
    levelOrderPrint(root);
 
    return 0;
}
```

**输出：**

1  
2 3  
4 5 6 7  
8 9 10 11 12 13 14 15

逐个打印二叉树节点的过程，称为遍历，稍后再讲。

#### A.2.4.3. 普通二叉树的创建

如下这棵树比上面的树少了 3 个节点：

```
        _______1________
       /                \
    __2__             ___3___
   /     \           /       \
  4       5        _6         7
 /       /        /  \         \
8       10      12   13        15
```

空结点一般用 null 描述，如：{1,2,3,4,5,6,7,8,null,10,11,null,13,null,15}。

为了不改变数组的描述，用最小负整数来定义 null： # define null INT_MIN

**代码：**

增加对空节点的判断 if(i < nums.size() && nums[i] != null)

```cpp
#include <iostream>
#include <vector>
#include <queue>
#define null INT_MIN
using namespace std;
 
struct TreeNode
{
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};
 
TreeNode* buildTree(vector<int>& nums)
{
    if (nums.empty()) return nullptr;
	TreeNode *root = new TreeNode(nums.front());
    queue<TreeNode*> q;
    q.push(root);
    int i = 1;
    while(!q.empty() && i < nums.size())
    {
        TreeNode *cur = q.front();
        q.pop();
        if(i < nums.size() && nums[i] != null)
        {
            cur->left = new TreeNode(nums[i]);
            q.push(cur->left);
        }
        i++;
        if(i < nums.size() && nums[i] != null)
        {
            cur->right = new TreeNode(nums[i]);
            q.push(cur->right);
        }
        i++;
    }
    return root;
}
 
void levelOrder(TreeNode* root)
{
    if(!root) return;
    queue<TreeNode*> q;
    q.push(root);
    while(!q.empty())
    {
        int size = q.size();
        for(int i = 0; i < size; i++)
        {
            TreeNode *cur = q.front();
            q.pop();
            cout << cur->val << " ";
            if(cur->left)
                q.push(cur->left);
            if(cur->right)
                q.push(cur->right);
        }
        cout << endl;
    }
}
 
int main()
{
    vector<int> nums = {1,2,3,4,5,6,7,8,null,10,11,null,13,null,15};
    TreeNode *root = buildTree(nums);
    levelOrder(root);
    
    return 0;
}
```

**输出：** 

1  
2 3  
4 5 6 7  
8 10 11 13 15

以上代码，直接用 **队列 queue** 来存放二叉树各节点的指针，queue 有队列操作的专用内置方法 pop 和 push，所以要比在前一例中用 vector 模拟的队列操作要稍微方便一点。

注：二叉树的遍历，如

用 **队列** 操作的一般是广度优先遍历 （BFS，Breath First Search）

而用 **栈** 操作的一般是深度优先遍历 （DFS，Depth First Search）

## A.3. 二叉树的遍历

指如何按某种搜索路径巡防树中的每个结点，使得每个结点均被访问一次，而且仅被访问一次。  
常见的遍历方法有：**层序遍历，先序遍历，中序遍历，后序遍历**。

### A.3.1. [层序遍历](https://so.csdn.net/so/search?q=%E5%B1%82%E5%BA%8F%E9%81%8D%E5%8E%86&spm=1001.2101.3001.7020)

若二叉树为空，为空操作；否则从上到下、从左到右按层次进行访问。

遍历结果： 1 [2 3] [4 5 6 7] [8 9 10 11 12 13 14 15]  

![](https://img-blog.csdnimg.cn/20210725085538742.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JveXNvZnQyMDAy,size_16,color_FFFFFF,t_70)

层序遍历的 BFS 代码在上面的 **打印二叉树** 章节已放出，这里放上我见过的一种用递归法写的二叉树层序遍历：

```cpp
#include <iostream>
#include <vector>
#include <queue>
#define null INT_MIN
using namespace std;
 
struct TreeNode
{
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};
 
TreeNode* buildTree(vector<int>& nums)
{
    if (nums.empty()) return nullptr;
	TreeNode *root = new TreeNode(nums.front());
    queue<TreeNode*> q;
    q.push(root);
    int i = 1;
    while(!q.empty() && i < nums.size())
    {
        TreeNode *cur = q.front();
        q.pop();
        if(i < nums.size() && nums[i] != null)
        {
            cur->left = new TreeNode(nums[i]);
            q.push(cur->left);
        }
        i++;
        if(i < nums.size() && nums[i] != null)
        {
            cur->right = new TreeNode(nums[i]);
            q.push(cur->right);
        }
        i++;
    }
    return root;
}
 
int countNodesAtLevel(TreeNode* root, int level)
{
    if(root == nullptr) return 0;
    if(level == 0) return 1;
    return countNodesAtLevel(root->left, level - 1) + countNodesAtLevel(root->right, level - 1);
}
 
TreeNode* getNodeAtLevel(TreeNode* root, int level, int index)
{
    if(root == nullptr) return nullptr;
    if(level == 0)
    {
        if(index == 0) return root;
        else return nullptr;
    }
    TreeNode *left = getNodeAtLevel(root->left, level - 1, index);
    if(left != nullptr) return left;
    return getNodeAtLevel(root->right, level - 1, index - countNodesAtLevel(root->left, level - 1));
}
 
void levelOrder(TreeNode* root)
{
    int level = 0;
    while(true)
    {
        int cnt = countNodesAtLevel(root, level);
        if(cnt == 0) break;
        for(int i = 0; i < cnt; i++)
        {
            TreeNode *node = getNodeAtLevel(root, level, i);
            cout << node->val << " ";
        }
        cout << endl;
        level++;
    }
}
 
int main()
{
    vector<int> nums = {1,2,3,4,5,6,7,8,null,10,11,null,13,null,15};
    TreeNode *root = buildTree(nums);
    levelOrder(root);
    
    return 0;
}
```

### A.3.2. 先序遍历

若二叉树为空，为空操作；  
否则（1）访问根节点；（2）先序遍历左子树；（3）先序遍历右子树。

遍历结果： `1 [2 [4 8 9] [5 10 11]] [3 [6 12 13] [7 14 15]`   “**根左右**”

![](https://img-blog.csdnimg.cn/20210725082352964.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JveXNvZnQyMDAy,size_16,color_FFFFFF,t_70)

### A.3.3. 中序遍历

若二叉树为空，为空操作；  
否则（1）中序遍历左子树；（2）访问根结点；（3）中序遍历右子树。

遍历结果： `[[8 4 9] 2 [10 5 11]] 1 [[12 6 13] 3 [14 7 15]]`  “**左根右**”

![](https://img-blog.csdnimg.cn/20210725083710482.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JveXNvZnQyMDAy,size_16,color_FFFFFF,t_70)

### A.3.4. 后序遍历

若二叉树为空，为空操作；  
否则（1）后序遍历左子树；（2）后序遍历右子树；（3）访问根结点。

遍历结果： [[8 9 4] [10 11 5] 2] [[12 13 6] [14 15 7] 3] 1  “**左右根**”

![](https://img-blog.csdnimg.cn/20210725084708331.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JveXNvZnQyMDAy,size_16,color_FFFFFF,t_70)

#### A.3.4.1. 递归法

```cpp
#include <iostream>
#include <vector>
#include <queue>
#define null INT_MIN
using namespace std;
 
struct TreeNode
{
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};
 
TreeNode* buildTree(vector<int>& nums)
{
    if (nums.empty()) return nullptr;
	TreeNode *root = new TreeNode(nums.front());
    queue<TreeNode*> q;
    q.push(root);
    int i = 1;
    while(!q.empty() && i < nums.size())
    {
        TreeNode *cur = q.front();
        q.pop();
        if(i < nums.size() && nums[i] != null)
        {
            cur->left = new TreeNode(nums[i]);
            q.push(cur->left);
        }
        i++;
        if(i < nums.size() && nums[i] != null)
        {
            cur->right = new TreeNode(nums[i]);
            q.push(cur->right);
        }
        i++;
    }
    return root;
}
 
void preOrderTraversal(TreeNode* root) {
    if (root == nullptr) {
	        return;
    }
    cout << root->val << " ";
    preOrderTraversal(root->left);
    preOrderTraversal(root->right);
}
 
void inOrderTraversal(TreeNode* root) {
    if (root == nullptr) {
	        return;
    }
    inOrderTraversal(root->left);
    cout << root->val << " ";
    inOrderTraversal(root->right);
}
 
void postOrderTraversal(TreeNode* root) {
    if (root == nullptr) {
	        return;
    }
    postOrderTraversal(root->left);
    postOrderTraversal(root->right);
    cout << root->val << " ";
}
 
int main()
{
    vector<int> nums;
    for (int i = 0; i < 15; i++)
    	nums.push_back(i+1);
    TreeNode *root = buildTree(nums);
    preOrderTraversal(root);
    cout << endl;
    inOrderTraversal(root);
    cout << endl;
    postOrderTraversal(root);
    cout << endl;
    
    return 0;
}
```

**输出：**

1 2 4 8 9 5 10 11 3 6 12 13 7 14 15  
8 4 9 2 10 5 11 1 12 6 13 3 14 7 15  
8 9 4 10 11 5 2 12 13 6 14 15 7 3 1

#### A.3.4.2. 前中后序对比

遍历时核心代码的顺序是关键，就是上面讲过的用 “**根左右**”“**左根右**”“**左右根**” 记忆，看根节点的左右子树节点的位置比较：

**根左右——前序**  

```cpp
cout <<root->val << " ";  
preOrderTraversal(root->left);  
preOrderTraversal(root->right);
```

**左根右——中序**  

```cpp
inOrderTraversal(root->left);  
cout <<root->val << " ";  
inOrderTraversal(root->right);
```

**左右根——后序**  
```cpp
postOrderTraversal(root->left);  
postOrderTraversal(root->right);  
cout <<root->val << " ";
```

遍历除了直接打印节点外，还可以把各节点值域存入数组，以中序为例：

```cpp
vector<int> inorderTraversal(TreeNode* root) {
    vector<int> res;
    inorderTraversal(root, res);
    return res;
}
void inorderTraversal(TreeNode* root, vector<int>& res) {
    if (root == nullptr) {
        return;
    }
    inorderTraversal(root->left, res);
    res.push_back(root->val);
    inorderTraversal(root->right, res);
}
```

#### A.3.4.3. DFS 遍历

DFS 会用到 `<stack>`，直接打印版：

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <stack>
#define null INT_MIN
using namespace std;
 
struct TreeNode
{
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};
 
TreeNode* buildTree(vector<int>& nums)
{
    if (nums.empty()) return nullptr;
	TreeNode *root = new TreeNode(nums.front());
    queue<TreeNode*> q;
    q.push(root);
    int i = 1;
    while(!q.empty() && i < nums.size())
    {
        TreeNode *cur = q.front();
        q.pop();
        if(i < nums.size() && nums[i] != null)
        {
            cur->left = new TreeNode(nums[i]);
            q.push(cur->left);
        }
        i++;
        if(i < nums.size() && nums[i] != null)
        {
            cur->right = new TreeNode(nums[i]);
            q.push(cur->right);
        }
        i++;
    }
    return root;
}
 
void preOrderTraversal(TreeNode* root) {
    stack<TreeNode*> st;
    TreeNode* node = root;
    while (node != nullptr || !st.empty()) {
        while (node != nullptr) {
            cout << node->val << " ";
            st.push(node);
            node = node->left;
        }
        node = st.top();
        st.pop();
        node = node->right;
    }
}
 
void inOrderTraversal(TreeNode* root) {
    stack<TreeNode*> st;
    TreeNode* node = root;
    while (node != nullptr || !st.empty()) {
        while (node != nullptr) {
            st.push(node);
            node = node->left;
        }
        node = st.top();
        st.pop();
        cout << node->val << " ";
        node = node->right;
    }
}
 
void postOrderTraversal(TreeNode* root) {
    stack<TreeNode*> st;
    TreeNode* node = root;
    TreeNode* last = nullptr; // 上一次访问的节点
    while (node != nullptr || !st.empty()) {
        while (node != nullptr) {
            st.push(node);
            node = node->left;
        }
        node = st.top();
        if (node->right == nullptr || node->right == last) { 
			// 右子树为空或已经访问过
            cout << node->val << " ";
            st.pop();
            last = node; // 更新上一次访问的节点
            node = nullptr; // 继续弹出栈顶元素
        } else { // 右子树还未访问
            node = node->right;
        }
    }
}
 
int main()
{
    vector<int> nums;
    for (int i = 0; i < 15; i++)
    	nums.push_back(i+1);
    TreeNode *root = buildTree(nums);
    preOrderTraversal(root);
    cout << endl;
    inOrderTraversal(root);
    cout << endl;
    postOrderTraversal(root);
    cout << endl;
    
    return 0;
}
```

二叉树转数组，分别用 DFS,BFS 实现：

```cpp
vector<int> DFSinorderTraversal(TreeNode* root) {
    vector<int> res;
    stack<TreeNode*> st;
    while (root != nullptr || !st.empty()) {
        while (root != nullptr) {
            st.push(root);
            root = root->left;
        }
        root = st.top();
        st.pop();
        res.push_back(root->val);
        root = root->right;
    }
    return res;
}
 
vector<int> BFSinorderTraversal(TreeNode* root) {
    vector<int> res;
    queue<TreeNode*> q;
    if (root != nullptr) {
        q.push(root);
    }
    while (!q.empty()) {
        TreeNode* node = q.front();
        q.pop();
        if (node->left != nullptr) {
            q.push(node->left);
        }
        res.push_back(node->val);
        if (node->right != nullptr) {
            q.push(node->right);
        }
    }
    return res;
}
```

## A.4. **树的相关术语**

**节点**：包含一个数据元素及若干指向其子树的分支，又的译成 “**结点**”（Node）  
**根**：树和子树的 “顶点”（Root）  
**度**：节点拥有的子树数量称为 **节点的度**（Degree）；**树的度** 是指树内个结点的度的最大值  
**分支节点**：度不为 0 的节点  
**叶子**：没有子树的节点，即它的度为 0 （Leaf）  
**子节点**：结点的子树的根称为该节点的 **孩子**（Child）  
**父节点**：对应子节点上一层 (level) 节点称为该节点的 **双亲**（Parent）  
**兄弟结点**：同一父节点的子节点，互称 **兄弟**（Sibling）  
节点的 **祖先**：是从根到该结点所经分支上的所有节点  
节点的 **子孙**：以某结点为根的子树中的所有节点  
**层**：从根开始，根为第一层，根的孩子为第二层...（Level）  
**深度**：树中结点的最大层次数，称为树的深度或高度 （Depth or Height）  
**森林**：是很多互不相交的树的集合（Forest）

**无序树**：树中任意节点的子节点之间没有顺序关系，这种树称为无序树，也称为自由树  
**有序树**：树中任意节点的子节点之间有顺序关系，这种树称为有序树  
**最大树（最小树）**：每个结点的值都大于（小于）或等于其子结点（如果有的话）值的树

## A.5. 特殊二叉树

### A.5.1. 满二叉树

所有层的节点都达到最大数量，叶子除外的所有节点都有两个子节点，所有叶子都在最底一层 (k) 且数目为 2^(k - 1)。即深度 k 且有 2^k - 1 个节点 (叶子“长” 满最后一层)，或称完美二叉树 （Perfect Binary Tree）

```
         ______12_______
        /               \
     __3__             __5__
    /     \           /     \
  _7       6        _9       11
 /  \     / \      /  \     /  \
13   8   1   4    10   2   0    14
```

### A.5.2. 完全二叉树

如果删除最底一层的所有叶子它就是满二叉树，即除了最后一层，每层节点都达到最大数量 ，即有深度 k 的个节点数在左闭右开【2^(k-1)+1,2^k-1】区间内。（Complete Binary Tree）

```
         ________3______
        /               \
    ___11___           __4__
   /        \         /     \
  14         7       9       13
 /  \      /  \     /   
2    5    8    6   1 
```

**完全二叉树性质：**

1. 具有 N 个节点的完全二叉树的深度为 [log2 N]+1，其中 [x] 为高斯函数，截尾取整。  
2. 如果对一棵有 n 个节点的完全二叉树的节点按层序编号（从第一层到最后一层，每层从左到右），则对任一节点，有：  
（1）如果 i=1，则节点 i 是二叉树的根，无双亲；如果 i>1, 则其双亲节点为 [i/2]；  
（2）如果 2i>n，则节点 i 无左孩子；否则其左孩子是节点 2i；  
（3）如果 2i+1>n，则节点 i 无右孩子；否则其右孩子是节点 2i+1。