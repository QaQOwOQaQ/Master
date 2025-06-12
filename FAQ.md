## 180. Folly 库

[Folly](https://github.com/facebook/folly) (acronymed loosely after Facebook Open Source Library) is a library of C++17 components designed with practicality and efficiency in mind. **Folly contains a variety of core library components used extensively at Facebook**. In particular, it's often a dependency of Facebook's other open source C++ efforts and place where those projects can share code.

It complements (as opposed to competing against) offerings such as Boost and of course `std`. In fact, we embark on defining our own component only when something we need is either not available, or does not meet the needed performance profile. We endeavor to remove things from folly if or when `std` or Boost obsoletes them.

Performance concerns permeate much of Folly, sometimes leading to designs that are more idiosyncratic than they would otherwise be (see e.g. `PackedSyncPtr.h`, `SmallLocks.h`). Good performance at large scale is a unifying theme in all of Folly.

主要组件可以参考 [docs](https://github.com/facebook/folly/tree/main/folly/docs) 和 [overview](https://github.com/facebook/folly/blob/main/folly/docs/Overview.md)。

### 1. FBstring







很有意思，通过 folly 的设计，我们也能窥见一些对 `string` 可行的优化。

1. 根据字符串的大小，使用不同的内存模型
   * small：SSO 优化，直接分配在栈上，不用动态分配，并且局部性更好
   * medium：动态分配，但是使用 eager-copy，并发安全
   * large：动态分配，使用 COW，以优化拷贝的开销，但是引用计数在并发环境下会带来额外开销
2. 针对内存分配器进行优化，提到了 [一篇论文](http://goog-perftools.sourceforge.net/doc/tcmalloc.html)，看不太懂...
3. 对末尾 `\0` 优化，因为这里有 C++ 字符串转化为 C 字符串的需要，所以需要处理 `\0` 的问题。
   * folly 使用的是 lazy-append `\0`，也即只有在需要 C++ 转 C 或者取得底层数据时才添加 `\0`，例如调用 `data()` 或 `c_str()`，从而避免每次修改字符串时 `\0` 带来的额外开销（特别是 `push_back`）
4. `realloc` 的处理：
   * 当字符串的内存利用率很少时（`size * 2 < capacity`），也即使用率不到 50% 时，放弃使用 `realloc`（因为 `realloc` 需要拷贝全部内存，但是其中一半多是无效内容，），而是通过 `free` + `malloc` + `copy` 的方式（只拷贝有效内容）重新分配内存，减少拷贝开销。
   * 当内存使用率大于 50% 时，则使用 `realloc`，并寄希望于 `realloc` 可以直接合并后面的空闲内存，以避免拷贝开销
5. `find` 的优化：这里似乎是针对 FaceBook 的常用场景做了特定优化？

参考自：

> 1. https://www.cnblogs.com/promise6522/archive/2012/06/05/2535530.html
> 2. https://zhuanlan.zhihu.com/p/348614098

### 2. small_vector































































































## C++ ABI

https://zhuanlan.zhihu.com/p/692886292

## C++ 代码究竟膨胀在哪里？

https://zhuanlan.zhihu.com/p/686296374

## arrregates、POD、trivial、Standard Layout

https://www.zhihu.com/question/472942396/answers/updated

https://stackoverflow.com/questions/4178175/what-are-aggregates-and-trivial-types-pods-and-how-why-are-they-special/4178176

https://stackoverflow.com/questions/4178175/what-are-aggregates-and-trivial-types-pods-and-how-why-are-they-special/7189821#7189821

https://en.wikipedia.org/wiki/Passive_data_structure

https://stackoverflow.com/questions/146452/what-are-pod-types-in-c

### 1. 概念

**POD**

> A POD struct is a non-union class that is both a trivial class and a standard-layout class, and has no non-static data members of type non-POD struct, non-POD union (or array of such types). 
>
> Similarly, a POD union is a union that is both a trivial class and a standard-layout class, and has no non-static data members of type non-POD struct, non-POD union (or array of such types). 
>
> A POD class is a class that is either a POD struct or a POD union.

**Trivial:**

> 6 A trivially copyable class is a class: 
>
> (6.1) — where each copy constructor, move constructor, copy assignment operator, and move assignment operator (15.8, 16.5.3) is either deleted or trivial,
>
> (6.2) — that has at least one non-deleted copy constructor, move constructor, copy assignment operator, or move assignment operator, and 
>
> (6.3) — that has a trivial, non-deleted destructor (15.4). 
>
> A trivial class is a class that is trivially copyable and has one or more default constructors (15.1), all of which are either trivial or deleted and at least one of which is not deleted. [ Note: In particular, a trivially copyable or trivial class does not have virtual functions or virtual base classes. — end note ]



### 2.  [Why is std::is_pod deprecated in C++20?](https://stackoverflow.com/questions/48225673/why-is-stdis-pod-deprecated-in-c20)

POD is being replaced with two categories that give more nuances. The [c++ standard meeting in november 2017](https://botondballo.wordpress.com/2017/11/20/trip-report-c-standards-meeting-in-albuquerque-november-2017/) had this to say about it:

> Deprecating the notion of **“plain old data” (POD).** It has been replaced with two more nuanced categories of types, **“trivial”** and **“standard-layout”**. **“POD” is equivalent to “trivial and standard layout”**, but for many code patterns, a narrower restriction to just “trivial” or just “standard layout” is appropriate; to encourage such precision, the notion of “POD” was therefore deprecated. The library trait is_pod has also been deprecated correspondingly.

For simple data types use the [`is_standard_layout`](http://en.cppreference.com/w/cpp/types/is_standard_layout) function, for trivial data types (such as simple structs) use the [`is_trivial`](http://en.cppreference.com/w/cpp/types/is_trivial) function.

[P0767R1: Deprecate POD](https://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0767r1.html)

##  `std::function` 源码分析

##  `libstdc++` 和 `libc++`

## 头文件 or 源文件

一般来说，将 inline 函数和 constexpr 函数的定义放在头文件中。

一般来说，如果非成员函数是类接口的组成部分，则这些函数的声明应该与类放在同一个文件内、

对于一个函数来说，noexcept 说明必须出现在该函数的所有声明语句和定义语句中。

## 默认初始化、值初始化

> ## 101. class对象值初始化BUG
>
> 看下面的代码：
>
> ``` c++
> class Foo {
> public:
>  Foo() {  }
>  Foo(int _a, int _b, int _c) 
>      : a(_a), b(_b), c(_c) 
>      {
>          cout << "ctor::iii" << endl;
>      }
> public:
>  short a;
>  int b;
>  double c;
> };
> 
> Foo global;
> 
> int main() 
> {
>  static Foo static_local;
>  Foo local;
>  Foo local_vaue{};
>  cout << global.a << ' ' << global.b << ' ' << global.c << endl;
>  cout << static_local.a << ' ' << static_local.b << ' ' << static_local.c << endl;
>  cout << local_vaue.a << ' ' << local_vaue.b << ' ' << local_vaue.c << endl;
>  cout << local.a << ' ' << local.b << ' ' << local.c << endl;
>  return 0;
> }
> ```
>
> 输出结果为：
>
> ``` shell
> 0 0 0
> 0 0 0
> 27751 779647075 2.11653e+214
> 27751 779647075 3.64265e-319
> ```
>
> 我们发现 `local` 对象和 `local_value` 对象的值是无意义的，对于 `local` 对象的结果我们可以预料，但在第 `100` 节我们讲过，值初始化的对象，基本类型的值应该为 `0` 才对，为什么这里是无意义的值呢？
>
> 我们修改一下代码：
>
> ``` c++
> #include "header.h"
> 
> using namespace std;
> 
> class Foo {
> public:
>  // Foo() {  }
>  // Foo(int _a, int _b, int _c) 
>  //     : a(_a), b(_b), c(_c) 
>  //     {
>  //         cout << "ctor::iii" << endl;
>  //     }
> public:
>  short a;
>  int b;
>  double c;
> };
> 
> Foo global;
> 
> int main() 
> {
>  static Foo static_local;
>  Foo local;
>  Foo local_vaue{};
>  cout << global.a << ' ' << global.b << ' ' << global.c << endl;
>  cout << static_local.a << ' ' << static_local.b << ' ' << static_local.c << endl;
>  cout << local_vaue.a << ' ' << local_vaue.b << ' ' << local_vaue.c << endl;
>  cout << local.a << ' ' << local.b << ' ' << local.c << endl;
>  return 0;
> }
> ```
>
> 注释掉我们自己定义的两个构造函数，再次观察结果：
>
> ``` c++
> 0 0 0
> 0 0 0
> 0 0 0
> 27751 779647075 2.11653e+214
> ```
>
> 可以发现，此时 `local_value` 对象的值是正常的，全部为 `0`。
>
> 我们再次修改代码：
>
> ``` c++
> class Foo {
> public:
>  Foo() = default;
>  Foo(int _a, int _b, int _c) 
>      : a(_a), b(_b), c(_c) 
>      {
>          cout << "ctor::iii" << endl;
>      }
> public:
>  short a;
>  int b;
>  double c;
> };
> 
> Foo global;
> 
> int main() 
> {
>  static Foo static_local;
>  Foo local;
>  Foo local_vaue{};
>  cout << global.a << ' ' << global.b << ' ' << global.c << endl;
>  cout << static_local.a << ' ' << static_local.b << ' ' << static_local.c << endl;
>  cout << local_vaue.a << ' ' << local_vaue.b << ' ' << local_vaue.c << endl;
>  cout << local.a << ' ' << local.b << ' ' << local.c << endl;
>  return 0;
> }
> ```
>
> 将我们原本自己定义的默认构造函数 `Foo() {}` 修改为系统为我们提供的默认构造函数 `Foo() = default;`
>
> 再次观察结果：
>
> ``` C++
> 0 0 0
> 0 0 0
> 0 0 0
> 27751 779647075 3.64265e-319
> ```
>
> 可以发现，此时 `local_value` 对象的值也是正确的。
>
> 其实通过对比也可以发现，问题就出现在我们自定义的默认构造函数 `Foo(){}` 上，它没有对我们的基本类型对象进行正确的初始化。
>
> 按理来说，我们自定义的 `Foo(){}` 和 `=default` 生成的构造函数应该相同啊？
>
> C++ Prime 7.5.1 节说到，如果我们没有在初始值列表显示的初始化成员变量的话，则该成员将在构造函数体之前执行“默认初始化”。而对于局部变量，基础类型在默认初始化下的值是未定义的。因此这里的 `local_value` 对象输出的值是未定义的。
>
> 所以说，停止你的UB行为！请你在构造函数中初始化成员变量，而不是依赖于编译器。
>
> 
>
> ---
>
> 
>
> ## 值初始化
>
> ```c++
> class Foo {
> public:
>  Foo() {}    // 注释掉呢？
>  int x, y;
> };
> 
> int main() 
> {
>  vector<Foo> a(10);
>  for(int i = 0; i < 10; i ++ ) {
>      cout << a[i].x - a[i].y << endl;
>  }
>  Foo b;
>  cout << b.x << ' ' << b.y << endl;
>  Foo c{};
>  cout << c.x << ' ' << c.y << endl;
>  return 0;
> }
> 
> ```
>
> 值初始化并不总是意味着0初始化
>
> ----
>
> ## 107. 合成默认构造函数
>
> 如果类内没有显示声明一个构造函数，编译器会合成一个默认构造函数。该构造函数会检查类的数据成员，如果有类内初始值就用它执行初始化操作，否则就执行默认初始化。

## C++ protected继承意义

下面是真实世界实践中 C++ 项目 **protected 继承**和 **private 继承**的情况：

| 项目名称 | 代码行数 | public继承     | private继承  | protected继承 |
| :------- | :------- | :------------- | :----------- | :------------ |
| LLVM     | 143万    | 3443次(99.68%) | 10次(0.29%)  | 1次(0.03%)    |
| Clang    | 90万     | 2373次(98.39%) | 36次(1.49%)  | 3次(0.12%)    |
| muduo    | 26484    | 27次(100%)     | 0次(0%)      | 0次(0%)       |
| leveldb  | 20884    | 90次(100%)     | 0次(0%)      | 0次(0%)       |
| envoy    | 44万     | 3125次(99.64%) | 3次(0.10%)   | 8次(0.26%)    |
| folly    | 30万     | 859次(94.6%)   | 47次(5.18%)  | 2次(0.22%)    |
| boost    | 340万    | 6998次(95.66%) | 290次(3.96%) | 18次(0.38%)   |

这与 C++ 社区的一般实践相符，因为 **public 继承** 更符合面向对象的 **"is-a"** 关系，而 **private/protected 继承** 是特殊场景下的工具。



## 函数标识符

* virtual
* inline
* static
* override?
* final?
* const?
* &?

## 动态链接库的命名冲突

https://zhuanlan.zhihu.com/p/354694011



## heap 传参 自定义排序规则

https://leetcode.cn/problems/top-k-frequent-elements/?envType=study-plan-v2&envId=top-100-liked

heap(priority_queue) 三个参数传入的都应该是类型，因为heap是一个模

----

priority_queue 自定义排序规则

1. 类对象
2. 非类对象

当然，以友元函数或者成员函数的方式都可以重载 > 或者 < 运算符。需要注意的是，**以成员函数的方式重载 > 或者 < 运算符时，该成员函数必须声明为 const 类型，且参数也必须为 const 类型**，

lambda

## lambda 导致 TLE 的问题

> ## 一、lambda函数的递归问题
>
> [题目链接](https://leetcode.cn/problems/ping-heng-er-cha-shu-lcof/)
>
> 我们尝试用 lambda 表达式实现递归的代码：
>
> ``` cpp
> /**
>  * Definition for a binary tree node.
>  * struct TreeNode {
>  *     int val;
>  *     TreeNode *left;
>  *     TreeNode *right;
>  *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
>  *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
>  *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
>  * };
>  */
> 
> bool isBalanced(TreeNode* root) {
>     function<int(TreeNode*)> getMaxDepth = [](TreeNode *r) ->int {
>         if(r == nullptr)    return 0;
>         // 下面一行 vscode 提示错误信息如下：
>         // an enclosing-function local variable cannot be referenced in a lambda body unless it is in the capture listC/C++(1735)
>         return 1 + max(getMaxDepth(r->left), getMaxDepth(r->right)); 
>     };
>     if(root == nullptr) return true;
>     int l = getMaxDepth(root->left), r = getMaxDepth(root->right);
>     return abs(l - r) <= 1 && isBalanced(root->left) && isBalanced(root->right);
> }
> ```
>
> 具体运行报错：
>
> ``` cpp
> 1.cpp: In lambda function:
> 1.cpp:35:24: error: ‘getMaxDepth’ is not captured
>    35 |         return 1 + max(getMaxDepth(r->left), getMaxDepth(r->right));
>       |                        ^~~~~~~~~~~
> 1.cpp:32:45: note: the lambda has no capture-default
>    32 |     function<int(TreeNode*)> getMaxDepth = [](TreeNode *r) ->int {
> ```
>
> 这是因为在 C++ 中，lambda 表达式在定义时实际上不能直接调用自己，因为 lambda 在定义时没有名字。要让一个 lambda 自我引用，你需要使用一个技巧：将 lambda 自身作为参数传递给自己，从而实现递归。
>
> 为什么 Lambda 自身在定义时无法被调用？
>
> 1. **匿名性**：Lambda 表达式是匿名的，编译器在定义时不为其生成名称，因此无法在其内部直接引用或调用自己。
> 2. **捕获和名称**：在 lambda 定义时，虽然可以捕获外部变量，但不能直接引用自身，因为 lambda 的名字在定义时尚未确定。
>
> 因此只需要将 `getMaxDepth` 引用捕获进来即可：
>
> ``` cpp
> bool isBalanced(TreeNode* root) {
>     function<int(TreeNode*)> getMaxDepth = [&getMaxDepth](TreeNode *r) ->int {
>         if(r == nullptr)    return 0;
>         return 1 + max(getMaxDepth(r->left), getMaxDepth(r->right)); 
>     };
>     if(root == nullptr) return true;
>     int l = getMaxDepth(root->left), r = getMaxDepth(root->right);
>     return abs(l - r) <= 1 && isBalanced(root->left) && isBalanced(root->right);
> }
> ```
>
> 这里不能使用值捕获，因为在捕获 `getMaxDepth` 时， `getMaxDepth` 尚未完全构造完成（因为 lambda 还在定义中）。即使能编译通过，递归调用时 `getMaxDepth` 会是一个**拷贝的 `std::function`**，可能导致：
>
> - **栈溢出**（递归无法终止）。
> - **未定义行为**（调用的可能是无效的函数对象）。
>
> 在这里，如果我们使用值捕获，会报错：
>
> ``` cpp
> /home/insights/insights.cpp:17:45: warning: variable 'getMaxDepth' is uninitialized when used within its own initialization [-Wuninitialized]
>    17 |     function<int(TreeNode*)> getMaxDepth = [=](TreeNode *r) ->int {
>       |                              ~~~~~~~~~~~    ^
> 1 warning generated.
> ```
>
> 和我们上面的分析一致，此时 `getMaxDepth` 还没有构造完成，是一个 **uninitialized** 的状态。
>
> > [reference1](https://www.cnblogs.com/Dreammoon/p/18388367#:~:text=%E6%8D%95%E8%8E%B7%E5%92%8C%E5%90%8D%E7%A7%B0%EF%BC%9A%E5%9C%A8%20lambda%20%E5%AE%9A%E4%B9%89%E6%97%B6%EF%BC%8C%E8%99%BD%E7%84%B6%E5%8F%AF%E4%BB%A5%E6%8D%95%E8%8E%B7%E5%A4%96%E9%83%A8%E5%8F%98%E9%87%8F%EF%BC%8C%E4%BD%86%E4%B8%8D%E8%83%BD%E7%9B%B4%E6%8E%A5%E5%BC%95%E7%94%A8%E8%87%AA%E8%BA%AB%EF%BC%8C%E5%9B%A0%E4%B8%BA%20lambda%20%E7%9A%84%E5%90%8D%E5%AD%97%E5%9C%A8%E5%AE%9A%E4%B9%89%E6%97%B6%E5%B0%9A%E6%9C%AA%E7%A1%AE%E5%AE%9A%E3%80%82%20%E9%80%9A%E8%BF%87%E4%BD%BF%E7%94%A8%20lambda%20%E7%9A%84%E5%BC%95%E7%94%A8%E6%8D%95%E8%8E%B7%EF%BC%88%E9%80%9A%E5%B8%B8%E6%98%AF%E5%B0%86,lambda%20%E5%86%85%E9%83%A8%E5%AE%9E%E7%8E%B0%E9%80%92%E5%BD%92%E3%80%82%20%E5%81%87%E8%AE%BE%E6%88%91%E4%BB%AC%E8%A6%81%E6%9F%A5%E6%89%BE%E4%B8%80%E4%B8%AA%20AActor%20%E4%B8%8B%E6%89%80%E6%9C%89%E7%9A%84%20URectLightComponent%EF%BC%8C%E6%88%91%E4%BB%AC%E5%8F%AF%E4%BB%A5%E4%BD%BF%E7%94%A8%E4%B8%80%E4%B8%AA%20lambda%20%E5%87%BD%E6%95%B0%E6%9D%A5%E9%80%92%E5%BD%92%E5%9C%B0%E9%81%8D%E5%8E%86%E6%89%80%E6%9C%89%E5%AD%90%E7%BB%84%E4%BB%B6%E3%80%82)
> >
> > [reference2](https://zhuanlan.zhihu.com/p/659164782)
>
> ## 二、lambda闭包开销导致递归时TLE
>
> [题目链接](https://leetcode.cn/problems/target-sum/submissions/578519493/)
>
> 具体代码：
>
> ``` cpp
> // TLE
> class Solution {
> public:
>     int findTargetSumWays(vector<int>& nums, int target) {
>         int res = 0;
>         function<void(int,int)> dfs = [&](int u, int cur) {
>             if(u == nums.size()) {
>                 res += cur == target;
>                 return ;
>             }
>             dfs(u + 1, cur + nums[u]);
>             dfs(u + 1, cur - nums[u]);
>         };
>         dfs(0, 0);
>         return res;
>     }
> };
> ```
>
> 提交之后会 **TLE**。但如果我们不用 lambda，而是直接写一个 inline 函数就不会 **TLE**：
>
> ``` cpp
> // AC
> class Solution {
>     int res;
>     /*inline*/void dfs(int u, int cur, vector<int> &nums, int target) 
>     {
>         if(u == nums.size()) {
>             res += cur == target;
>             return ;
>         }
>         dfs(u + 1, cur + nums[u], nums, target);
>         dfs(u + 1, cur - nums[u], nums, target);
>     }
> public:
>     int findTargetSumWays(vector<int>& nums, int target) {
>         dfs(0, 0, nums, target);
>         return res;
>     }
> };
> ```
>
> 上面的这份代码是没问题的。那显然的，问题出在我们定义的 lambda 递归函数了，我们可以通过 [CPPInsights](https://cppinsights.io/) 来看看 **TLE** 的代码在编译器的视角是怎样的：
>
> ``` C++
> class Solution
> {
> public:
>     inline int findTargetSumWays(std::vector<int, std::allocator<int>> &nums, int target)
>     {
>         int res = 0;
>         class __lambda_11_39
>         {
>         public:
>             inline /*constexpr */ void operator()(int u, int cur) const
>             {
>                 if (static_cast<unsigned long>(u) == nums.size())
>                 {
>                     res = res + (static_cast<int>(cur == target));
>                     return;
>                 }
> 
>                 dfs.operator()(u + 1, cur + nums.operator[](u));
>                 dfs.operator()(u + 1, cur - nums.operator[](u));
>             }
> 
>         private:
>             std::vector<int, std::allocator<int>> &nums;
>             int &target;
>             int &res;
>             std::function<void(int, int)> &dfs;
> 
>         public:
>             // inline /*constexpr */ __lambda_11_39(const __lambda_11_39 &) noexcept = default;
>             // inline /*constexpr */ __lambda_11_39(__lambda_11_39 &&) noexcept = default;
>             __lambda_11_39(std::vector<int, std::allocator<int>> &_nums, int &_res, int &_target, std::function<void(int, int)> &_dfs)
>                 : nums{_nums}, res{_res}, target{_target}, dfs{_dfs}
>             {
>             }
>         };
> 
>         std::function<void(int, int)> dfs = std::function<void(int, int)>(__lambda_11_39{nums, res, target, dfs});
>         dfs.operator()(0, 0);
>         return res;
>     }
> };
> ```
>
> ## 三、C++11 -- 匿名函数(lambda 表达式)
>
> > ### 0. 一道题目引入
> >
> > > [关于sb力扣定义外部函数和变量报错这件事](https://leetcode.cn/problems/sort-array-by-increasing-frequency/submissions/)
> >
> > 最初我定义了一个 $cmp$ 函数用来对 $vector$ 排序，和一个全局变量 $unordered\_map$ 用来记录元素个数。
> > 但是 $sb$ 力扣报我错，我也不知道为啥！于是我查看了官方题解 ~~我是sb，这种题还要看题解~~，发现官方题解是这样定义自己的 $cmp$ 函数的：
> >
> > ```
> > sort(nums.begin(), nums.end(), [&](int a, int b) ->bool{
> >     if(cnt[a] == cnt[b])    return a > b;
> >     return cnt[a] < cnt[b];
> > });
> > ```
> >
> > 没错！它直接在 $sort$ 里面定义了一个 “没有函数名字” 的 $cmp$ 函数。
> > 把 "$cmp$ 函数" 单独拿出来就是：
> >
> > ```
> > [&](int a, int b) -> bool{
> >     if(cnt[a] == cnt[b])  return a > b;
> >     return cnt[a] > cnt[b];
> > }
> > ```
> >
> > 于是我就上网 $goole$ 了一下这个语法，才知道这是 $C ++ 11$ 的新特性：**$lambda$ 函数，又叫做匿名函数，$lambda$ 表达式。**
> >
> > 这是AC代码：
> >
> > ```
> > class Solution {
> > public:
> >     vector<int> frequencySort(vector<int>& nums) {
> >         int n = nums.size();
> >         if(!n)  return nums;
> >         unordered_map<int, int> cnt;
> >         for(auto &x : nums)
> >         {
> >             cnt[x] ++ ;
> >         }
> > 
> >         sort(nums.begin(), nums.end(), [&](int a, int b) ->bool{
> >             if(cnt[a] == cnt[b])    return a > b;
> >             return cnt[a] < cnt[b];
> >         });
> >         return nums;
> >     }
> > };
> > ```
> >
> > ### 1. lambda 表达式介绍
> >
> > 先上语法：
> >
> > ```
> > auto val = [captures](args) -> return_type {
> > 	...
> > }
> > 
> > val : 对象名
> > [captures] : 捕获作用域内变量
> > (args) : 匿名函数的参数列表
> > -> return_type : 函数返回值类型
> >           如果 lambda 函数没有传回值（例如 void），其返回类型可被完全忽略。
> > {...} : 函数实现体
> > ```
> >
> > 
> >
> > 一个简单的例子：通过匿名函数实现 x+y
> >
> > ```
> > int main()
> > {
> >     int x = 1, y = 2;
> >     auto f = [&]() -> int {
> > 	    return x + y;
> >     };
> > 
> >     cout << f() << endl;
> >     return 0;
> > }
> > ```
> >
> > > 我个人认为，这个语法更应该叫做 $lambda$ 表达式，~~而“匿名函数”不是非常合适~~，因此它并是真的完全“匿名”，它也是有名字的。
> > > 在上面的例子总，我们定义了一个 “函数” $f$~~[应该是个函数吧，毕竟需要通过()调用]~~，$f$ 不就是它的名字吗？
> > > 但为啥还要说“匿名”呢，我觉得，$f$ 并不能理解为一个函数的名字，它应该理解为一个**“对象”**的名字，$f$ 是一个“对象”，只不过这个对象的内容不是一个 $int$，也不是一个 $char$，而是一个“没有名字的函数”罢了。
> >
> >
> > ### 2. lambda 表达式的闭包
> >
> > 在 $Lambda$ 表达式内可以访问当前作用域的变量，这是 $Lambda$ 表达式的闭包（$Closure$）行为。 与 $JavaScript$ 闭包不同，$C++$ 变量传递有传值和传引用的区别。可以通过前面的 $[]$ 来指定：
> >
> > ```
> > []      // 沒有定义任何变量。使用未定义变量会引发错误（即不能引用函数自己定义的参数之外的变量）。
> > [x, &y] // x以传值方式传入（默认），y以引用方式传入。
> > [&]     // 任何被使用到的外部变量都隐式地以引用方式加以引用。
> > [=]     // 任何被使用到的外部变量都隐式地以传值方式加以引用。
> > [&, x]  // x显式地以传值方式加以引用。其余变量以引用方式加以引用。
> > [=, &z] // z显式地以引用方式加以引用。其余变量以传值方式加以引用。
> > ```
> >
> > 另外有一点需要注意。对于 $[=]$ 或 $[&]$ 的形式，$lambda$ 表达式可以直接使用 $this$ 指针。但是，对于 $[]$ 的形式，如果要使用 $this$ 指针，必须显式传入：
> >
> > ```
> > [this]() { this->someFunc(); }();
> > ```
> >
> > > [更多关于语法的细节](https://icode.best/i/45463231702232)
> >
> > ### 3. lambda 值引用 map/unordered_map 的一个坑
> >
> > 简单来说，在 $lambda$ 的捕获列表里面捕获 $map/unordered\_map$ 要么是引用捕获，要么使用 $at()$ 来获取容器内的元素。
> > 这是因此当捕获为 $map/unordered\_map$ 的值时，$lambda$ 表达式会默认转换为 $const map/const unordered\map$。
> > 之所以会发生这种转换，是因为 $map/unordered\_map$ 的一个特性：**当我们引用一个关键字 $key$ 的使用，如果这个关键字不存在则进行插入，也就说会修改容器。**
> > 另外，注意使用 $at()$ 去获取容器内元素，如果 $key$ 不存在，会报错：$out\_of\_range$，因为我们引用了一个容器中不存在的 $key$。
> > 这也就证明了使用 $at()$ 不会插入关键字，也就不会修改容器。
> >
> > 再来测试一下这个特性：**当我们引用一个关键字 $key$ 的使用，如果这个关键字不存在则进行插入，也就说会修改容器。**
> >
> > ```
> > int main()
> > {
> >     unordered_map<int,int> m;
> >     m[1] = 1;
> >     cout << m.size() << endl; // output：1
> >     int x = m[2];
> >     cout << m.size() << endl; // output：2
> > 
> >     return 0;
> > }
> > ```
> >
> > > 可以发现，我们仅仅只是引用了 $m[2]$，但容器的 $size$ 多了一个。
> >
> > > 具体的可以看一个博客：[C++11 lambda表达式不能捕获map/unordered_map值](https://blog.csdn.net/a3192048/article/details/82718678)



