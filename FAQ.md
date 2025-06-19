

## C++ protected 继承意义

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









## Memory Barrier





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

##  

