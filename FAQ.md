## 190. `atoi` vs. `std::stoi`

### **1. `atoi`（ASCII to Integer）**

**特点**

- **头文件**：`<stdlib.h>`（C 标准库）

- **原型**：`int atoi(const char *str);`

- **行为**：

  - 从字符串开头解析，跳过前导空格（` `、`\t` 等）。
  - 遇到 **非数字字符（如字母、符号）** 立即停止，返回已解析的部分。
  - 如果字符串无法转换（如 `"abc"`），返回 `0`。

- **错误处理**：

  ❌ **无错误检测**，无法区分 `"0"` 和无效输入（如 `"xyz"`）。

- **示例**：

  ```cpp
  #include <stdlib.h>
  int num = atoi("123");   // 返回 123
  int zero = atoi("abc");  // 返回 0（无法区分错误）
  ```

#### **缺点**

- 不检查溢出（如 `"2147483648"` 超出 `int` 范围时行为未定义）。
- 无法处理非十进制（如十六进制 `"0xFF"`）。

### **2. `stoi`（String to Integer）**

**特点**

- **头文件**：`<string>`（C++ 标准库）

- **原型**：`int stoi(const string& str, size_t* pos = 0, int base = 10);`

- **行为**：

  - 从字符串解析，跳过前导空格。
  - 可指定进制（如 `base=16` 解析十六进制）。
  - 如果解析失败（如 `"123abc"` 的非数字部分），抛出 `std::invalid_argument` 异常。
  - 如果数值超出 `int` 范围，抛出 `std::out_of_range` 异常。

- **错误处理**：
  ✅ **支持异常机制**，能明确区分无效输入和合法 `0`。

- **示例**：

  ```cpp
  #include <string>
  #include <stdexcept>
  try {
      int num = stoi("123");      // 返回 123
      int hex = stoi("FF", nullptr, 16); // 返回 255（十六进制）
      int bad = stoi("abc");     // 抛出 std::invalid_argument
  } catch (const std::exception& e) {
      std::cerr << "Error: " << e.what() << std::endl;
  }
  ```

#### **优点**

- 支持进制转换（如二进制、十六进制）。
- 严格的错误处理机制。
- 可获取解析结束位置（通过 `pos` 参数）。

### **关键区别总结**

| 特性             | `atoi` (C)         | `stoi` (C++)                                  |
| :--------------- | :----------------- | :-------------------------------------------- |
| **所属标准**     | C 标准库           | C++ 标准库                                    |
| **错误处理**     | 无（返回 `0`）     | 抛出异常（`invalid_argument`/`out_of_range`） |
| **溢出行为**     | 未定义行为         | 抛出 `out_of_range`                           |
| **支持进制**     | 仅十进制           | 可指定进制（如 2、8、16）                     |
| **参数类型**     | `const char*`      | `std::string`                                 |
| **线程安全**     | 是                 | 是                                            |
| **推荐使用场景** | 简单的、受控的输入 | 需要健壮性和灵活性的场景                      |

### **何时选择？**

- **用 `atoi`**：
  - 快速处理已知安全的输入（如硬编码字符串）。
  - C 语言环境或无需复杂错误检查的场景。
- **用 `stoi`**：
  - 需要验证用户输入或外部数据。
  - 需要处理不同进制（如十六进制）。
  - C++ 项目（优先使用 C++ 标准库）。

### **替代方案**

- **C++17 的 `std::from_chars`**：
  更高效且无异常的开销（但需手动处理错误）：

  ```cpp
  #include <charconv>
  const char* str = "123";
  int num;
  auto [ptr, ec] = std::from_chars(str, str + strlen(str), num);
  if (ec == std::errc()) {
      std::cout << num; // 成功
  }
  ```

## 191. Memory Order













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







## Reflection

https://zhuanlan.zhihu.com/p/456982033?share_code=jcaA0cvywMY7&utm_psn=1890557889598432770

https://zhuanlan.zhihu.com/p/669358870?share_code=HN8GXtCllrLR&utm_psn=1889970809050730641



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

