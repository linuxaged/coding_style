# Files

C++ 头文件使用 .hpp 后缀，以区分 C 头文件

        source.cpp // c++ 实现
        source.hpp // c++ 接口

        source.c  // c 实现
        source.h  // c 接口

使用 `#pragma once` 避免头文件重复引用

代码文件应当包含头信息：

        /************************************************************************************

        Filename	:	Demo.cpp
        Content		:	This sample uses the application framework.
        Created		:	Feb, 2017
        Authors		:	Tracy Ma

        Copyright	:	Copyright 2017 Your Company Name, LLC. All Rights reserved.

        *************************************************************************************/

# Types

* 在表示大小的时候使用明确大小的类型：

        uint8_t age;            // good
        uint16_t length;        // good
        uint32_t count;         // good
        unsigned char age;      // bad
        unsigned short length;  // bad
        unsigned int count;     // bad
     
* 慎用类型转换，在强制类型转换的时候明确你在干嘛，参考：

    * [Type Conversions and Type Safety (Modern C++)](https://docs.microsoft.com/en-us/cpp/cpp/type-conversions-and-type-safety-modern-cpp)

# Naming Conventions

* 函数和类型名使用帕斯卡(Pascal)命名法: 将标识符的首字母和后面连接的每个单词的首字母都大写。

        class MyClass
        {
            void PrivateFunction();
        }

* 类型实例使用骆驼(Camel)命名法：标识符的首字母小写，而每个后面连接的单词的首字母都大写。

        MyClass myClass;


* 顾名思义

        // Bad:
        t = s + l -b;
        EndCurCmdEnc();
        // Good:
        TotalLeaves = SmallLeaves + LargeLeaves - SmallAndLargeLeaves;
        EndCurrentCommandEncoder();

# Syntax

* Format

    遵循  [WebKit Code Style Guidelines](https://webkit.org/code-style-guidelines/)

    使用 clang-format 进行格式化：

        clang-format -style=llvm -dump-config > .clang-format
        clang-format -style=.clang-format

* declarator layout

    * `&` , `*` 紧跟类型

        T& operator[](size_t); // good
        T &operator[](size_t); // bad
        T & operator[](size_t); // bad

    * 只把同类型的声明放在同一行

        int a, b, c;             // ok
        int a = 7; char* p = 28; // bad

# Class

声明类的时候，各成员的出场顺序：

* 类型：`class`, `enums`, `using`
* 构造函数，赋值构造函数，析构函数
* 普通成员函数
* 数据成员

`public` 成员先于 `protect` 先于 `private`

# Modern C++

鼓励使用以下 C++11 特性：

* ## static_assert

    编译时断言，在编译时做尽可能多的检查

* ## override and final

    [显示声明 override 和 final](https://www.devbean.net/2012/05/cpp11-override-final/)

* ## nullptr

    禁止使用 NULL, 空指针一律用 nullptr 表示

* ## Strongly-Typed Enums

        // c++98
        enum Sex
        {
            Man,
            Woman
        }
        Sex sex = Man;

        // c++11, type safe
        enum class Sex
        {
            Man,
            Womam
        }
        Sex sex = Sex::Man;

    除了 C 接口外，一律使用强类型的枚举类型


# References

* [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)
* [Unreal Engine Coding Standard](https://docs.unrealengine.com/latest/INT/Programming/Development/CodingStandard/index.html)
* [<< Effective Modern C++ >>](http://shop.oreilly.com/product/0636920033707.do)