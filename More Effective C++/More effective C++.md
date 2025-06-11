# 一、基础议题

## 1. 指针和引用的区别

## 2. 尽量使用 C++ 风格的类型转换

## 3. 不要对数组使用多态

不要对数组使用多态，本质上来说是**“不要混合使用多态和指针算法”**，因为数组使用多态出错的情况一般是我们使用了 `for` 循环（值得注意 `delete[]` 底层上也是通过循环实现的）。

`for` 循环本质上就是通过对指向对数组首指针一直 `+1` 实现的，这里的 `+1` 操作依赖于元素的大小 `size`，它是固定的，一般来说是根据数组的静态类型决定的。

而对于多态来说，在数组 `Base arr[];` 和数组 `Derived arr[];` 上执行 `for` 循环显然不能是一回事，因为 `Base` 和 `Derived` 大小不相等的情况是很常见的。如果我们的 `+1` 是依赖于基类 `Base` 的大小，那么如果我们传入一个 `Derived` 类型的数组，`for` 循环就显然不正确了。

### 1. 数组的构造与析构顺序

``` cpp
struct Node {
    int x;
    Node(int _x) : x(_x) { cout << "ctor:" << x << endl; }
    ~Node() { cout << "dtor:" << x << endl; }
};

int main()
{
    Node *arr = new Node[3]{1, 2, 3};
    delete[] arr;
    return 0;
}
// ctor:1
// ctor:2
// ctor:3
// dtor:3
// dtor:2
// dtor:1
```

构造顺序，析构逆序。

## 4. 避免无用的缺省构造函数

# 二、运算符

## 5. 谨慎定义类型转换函数

让编译器进行隐式类型转换造成的弊端往往大于它所带来的好处，所以除非你确实需要，不要定义类型转换函数。

解决单参数构造函数隐式类型转换的问题：

1. explicit 关键字
2. 在不能使用 explicit 关键字的情况下，使用 nested/proxy class，其原理是编译器只能进行一步隐式类型转换

解决隐式类型转换函数会隐式类型转换的问题：

1. 使用 `int toint()` 替换 `operator int()`

## 6. 自增、自减操作符前缀形式与后缀形式的区别

``` cpp
struct X
{
    int _val;

    X(int val) : _val(val) {}

    // prefix increment
    X& operator++()
    {
        ++ _val;
        return *this; // return new value by reference
    }
 
    // postfix increment
    const X operator++(int)
    {
        X old = *this; // copy old value
        operator++();  // prefix increment
        return old;    // return old value
    }
 
    // prefix decrement
    X& operator--()
    {
        -- _val;
        return *this; // return new value by reference
    }
 
    // postfix decrement
    const X operator--(int)
    {
        X old = *this; // copy old value
        operator--();  // prefix decrement
        return old;    // return old value
    }
    X& modify(int val) {
        _val = val;
        return *this;
    }
};
```

* 在后缀自增中使用前缀自增，提高代码复用率

一个很关键的问题，为什么后缀自增返回的是 `const X` 而不是 `X` ?

1. 首先，从与内置类型行为一致的角度出发，我们应该返回 `const X`，因为对于 `int` 类型来说，`x++++` 是不合法的。因此对于我们自定义的类型，`X++++` 也应该是不合法的。
2. 两次后缀自增的结果可能并不符合我们的预期，并产生与直觉相悖的结果，在 `x++++` 中，`x` 只自增了一次，第二次递增针对的是`(x++)` 返回的临时对象。

## 7. 不要重载 `&&`，`||` 或 `,`

`||` 和 `&&` 运算符有短路求值的特性，而我们自己重载的版本并不能保证短路求值。

`,` 表达式自左向右计算，并返回右侧表达式的值，但是我们自己重载的版本并不能保证自左向右求值。

## 8. 理解各种不同含义的 new 和 delete

``` cpp
string *ps = new string("Memory Management");
// equals to
void *rp = operator new(sizeof(string));
rp->string("Memory Management");
string *ps = static_cast<string*>(rp);

delete ps;
// equals to
ps->~string();
operator delete(ps);
```

# 三、异常

## 9. 使用析构函数防止资源泄露



















































































































































































































































































































































































































































































































































































































































































































































































