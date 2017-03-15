---
title: "Visual C++ 2015 更新 1 中的重大更改 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c0b1c2b-e1cf-4767-885b-b98df9b3730e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "mithom"
manager: "ghogen"
---
# Visual C++ 2015 更新 1 中的重大更改
当升级到 Visual C\+\+ 2015 更新 1 后，之前编译并正常运行的代码中可能会出现编译和\/或运行时错误。 编译器和运行时行为中会引起这类问题的更改称为*重大更改*，通常，修改 C\+\+ 语言标准、函数签名或内存中的对象布局时需要进行这种更改。  
  
 本文的其余部分介绍了 Visual C\+\+ 2015 更新 1 中具体的重大更改，并且在本文中，术语“新行为”或“现在”均指该版本。 术语“旧行为”和“早期\/之前”指 Visual Studio 2015 初始版本和早期版本。 有关 Visual Studio 2013 和 Visual Studio 2015 之间重大更改的信息，请参阅 [Visual C\+\+ 2015 中的重大更改](/visual-cpp/porting/visual-cpp-change-history-2003-20151)。  
  
-   [编译器的重大更改](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Visual C\+\+ 编译器  
  
-   **私有虚拟基类和间接继承**  
  
     早期版本的编译器允许派生类调用*间接派生* `private virtual`基类的成员函数。 这种旧行为不正确，也不符合 C\+\+ 标准。 编译器不再接受这种方式编写的代码，因此会发出编译器错误 C2280。  
  
 **错误 C2280：*'void \*S3::\_\_delDtor\(unsigned int\)'*： 尝试引用已删除的函数**     示例（之前）  
  
    ```cpp  
    class base { protected: base(); ~base(); }; class middle: private virtual base {};class top: public virtual middle {}; void destroy(top *p) { delete p;  // }  
    ```  
  
     示例（之后）  
  
    ```cpp  
    class base;  // as above class middle: protected virtual base {}; class top: public virtual middle {}; void destroy(top *p) { delete p; }  
    ```  
  
     \- 或 \-  
  
    ```  
    class base;  // as above class middle: private virtual base {}; class top: public virtual middle, private virtual bottom {}; void destroy(top *p) { delete p; }  
    ```  
  
-   **重载的 new 运算符和 delete 运算符**  
  
     早期版本的编译器允许非成员 `operator new` 和非成员 `operator delete` 声明为静态，并在全局命名空间之外的命名空间中声明。  这种旧行为会引发风险，导致程序无法按按程序员的预期调用 `new` 或 `delete` 运算符实现，从而导致无提示的运行时行为错误。 编译器不再接受这种方式编写的代码，因此会发出编译器错误 C2323。  
  
 **错误 C2323：*“new 运算符”*：非成员运算符 new 或 delete 函数不能声明为静态或全局命名空间之外的命名空间中。**     示例（之前）  
  
    ```cpp  
  
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323  
    ```  
  
     示例（之后）  
  
    ```cpp  
  
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'  
    ```  
  
     此外，尽管编译器不能进行具体诊断，但内联运算符 new 会被视为格式不正确。  
  
-   **对非类类型调用“operator *ype*\(\)”（用户定义的转换）**  
  
     早期版本的编译器允许以无提示忽略的方式对非类类型调用“operator *type*\(\)”。 这种旧行为会导致无提示代码生成错误风险，从而导致不可预知的运行时行为。 编译器不再接受这种方式编写的代码，因此会发出编译器错误 C2228。  
  
 **错误 C2228：“.operator *type*”的左边必须有类\/结构\/联合**     示例（之前）  
  
    ```cpp  
    typedef int index_t; void bounds_check(index_t index); void login(int column) { bounds_check(column.operator index_t());  // error C2228 }  
    ```  
  
     示例（之后）  
  
    ```cpp  
    typedef int index_t; void bounds_check(index_t index); void login(int column) { bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int' }  
    ```  
  
-   **详细的类型说明符中的多余 typename**  
  
     早期版本的编译器允许详细的类型说明符中出现 `typename`；用这种方式编写的代码在语义上不正确。 编译器不再接受这种方式编写的代码，因此会发出编译器错误 C3406。  
  
 **错误 C3406：“typename”不能在详细类型说明符中使用**     示例（之前）  
  
    ```cpp  
    template <typename class T> class container;  
    ```  
  
     示例（之后）  
  
    ```cpp  
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case class container;  
    ```  
  
-   **初始值设定项列表中数组的类型推断**  
  
     早期版本的编译器不支持对初始值设定项列表中的数组进行类型推断。 编译器现在支持这种形式的类型推断，因此调用使用初始值设定项列表的函数模板现在可能会不明确，或者选择一个与以前版本的编译器不同的重载。 要解决这些问题，程序现在必须显式指定程序员所需的重载。  
  
     当这一新行为导致重载解决方法要考虑与以往候选一样好的其他候选时，调用变得不明确，编译器会发出编译器错误 C2668。  
  
 **错误 C2668：“*函数*”：对重载函数的调用不明确。**     示例 1： 对重载函数的调用不明确（之前）  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...) template <typename... Args> void f(int, Args...);  // template <int N, typename... Args> void f(const int (&)[N], Args...); int main() { // The compiler now considers this call ambiguous, and issues a compiler error  f({3});  error C2668: 'f' ambiguous call to overloaded function }  
    ```  
  
     示例 1： 对重载函数的调用不明确（之后）  
  
    ```cpp  
    template <typename... Args> void f(int, Args...);  // template <int N, typename... Args> void f(const int (&)[N], Args...); int main() { // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it. f(3); }  
    ```  
  
     这一新行为会导致重载解决方法要考虑比以往候选更适合的其他候选时，调用将明确地解析为新候选，导致程序行为的更改可能与程序员的需要有所不同。  
  
     示例 2：重载解决方法的更改（之前）  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...) struct S { int i; int j; }; template <typename... Args> void f(S, Args...); template <int N, typename... Args> void f(const int *&)[N], Args...); int main() { // The compiler now resolves this call to f(const int (&)[N], Args...) instead  f({1, 2}); }  
    ```  
  
     示例 2：重载解决方法的更改（之后）  
  
    ```cpp  
    struct S;  // as before template <typename... Args> void f(S, Args...); template <int N, typename... Args> void f(const int *&)[N], Args...); int main() { // To call f(S, Args...), perform an explicit cast to S on the initializer list. f(S{1, 2}); }  
    ```  
  
-   **switch 语句警告的还原**  
  
     前一个版本的编译器删除了之前存在的与 `switch` 语句相关的警告；现在已还原所有这些警告。 编译器现在将发出还原的警告，并且现在会在包含有问题用例的行中发出与特定用例（包括默认情况下）相关的警告，而不是在 switch 语句的最后一行发出。 因此，现在发出这些警告的行与过去不同，按照需要使用 `#pragma warning(disable:####)` 可不再禁止显示以前禁止显示的警告。 要按照需要禁止显示这些警告，可能需要将 `#pragma warning(disable:####)` 指令移到第一个可能有问题的用例上面的行。 以下是还原的警告。  
  
 **警告 C4060：switch 语句没有包含“case”或“default”标签 警告 C4061：枚举数“*bit1*”（在枚举“*flags*”的 switch 中）没有被 case 标签显式处理 警告 C4062：枚举数“*bit1*”（在枚举“*flags*”的 switch 中）没有被处理 警告 C4063：case“*bit32*”对于枚举“*flags*”的 switch 不是有效值 警告 C4064：不完整的枚举“*flags*”的 switch 警告 C4065：switch 语句包含“default”标签但未包含“case”标签 警告 C4808：case“*value*”不是类型“*bool*”的切换条件的有效值 警告 C4809：switch 语句有多余的“default”标签；给定所有可能的“case”标签**     C4063 示例（之前）  
  
    ```cpp  
    class settings { public: enum flags { bit0 = 0x1, bit1 = 0x2, ... }; ... }; int main() { auto val = settings::bit1; switch (val) { case settings::bit0: break; case settings::bit1: break;  case settings::bit0 | settings::bit1:  // warning C4063 break; } };  
    ```  
  
     C4063 示例（之后）  
  
    ```cpp  
    class settings {...};  // as above int main() { // since C++11, use std::underlying_type to determine the underlying type of an enum typedef std::underlying_type<settings::flags>::type flags_t; auto val = settings::bit1; switch (static_cast<flags_t>(val)) { case settings::bit0: break; case settings::bit1: break; case settings::bit0 | settings::bit1:  // ok break; } };  
    ```  
  
     在其文档中提供了其他还原警告的示例。  
  
-   **\#include：在路径名中使用父目录说明符“..”**（只影响 \/Wall\/WX）  
  
     早期版本的编译器没有检测到使用父目录说明符“..” （在 `#include` 指令的路径名中）。 以这种方式编写的代码通常用于包含因不正确使用项目相对路径而留在项目外的标头。 这一旧行为会引发风险，导致编译程序时包含了程序员不需要的源文件来，或这些相对路径不能移植到其他生成环境中。 编译器现在会检测以这种方式编写的代码并通知程序员，并发出可选编译器警告 C4464（如果已启用）。  
  
 **警告 C4464：相对包含路径包含“..”**     示例（之前）  
  
    ```cpp  
    #include "..\headers\C4426.h"  // emits warning C4464  
    ```  
  
     示例（之后）  
  
    ```cpp  
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories  
    ```  
  
     此外，虽然编译器并不会进行具体诊断，但我们建议父目录说明符“..” 不应用于指定项目的包含目录。  
  
-   **\#pragma optimize\(\) 超出标头文件的末尾**（只影响 \/Wall\/WX）  
  
     早期版本的编译器无法检测到对转义翻译单元中包含的标头文件的优化标志设置的更改。 编译器现在会检测以这种方式编写的代码并通知程序员，并在有问题的 `#include` 的位置发出可选编译器警告 C4426（如果已启用）。 只有更改与编译器命令行参数设置的优化标志发生冲突时，才发出此警告。  
  
 **警告 C4426：包含标头后优化标志发生更改，可能是由 \#pragma pack\(pop\) 造成**     示例（之前）  
  
    ```cpp  
    // C4426.h #pragma optimize("g", off) ... // C4426.h ends // C4426.cpp #include "C4426.h"  // warning C4426  
    ```  
  
     示例（之后）  
  
    ```cpp  
    // C4426.h #pragma optimize("g", off) ... #pragma optimize("", on)  // restores optimization flags set via command-line arguments // C4426.h ends // C4426.cpp #include "C4426.h"  
    ```  
  
-   **\#pragma warning\(push\)** 和 **\#pragma warning\(pop\)** 不匹配（只影响 \/Wall\/WX）  
  
     早期版本的编译器无法检测到不同源文件中与 `#pragma warning(pop)` 状态更改配对的 `#pragma warning(push)` 状态更改，这并不是我们所预期的。这种旧行为会引发风险，导致程序编译时会启用一组程序员不希望出现的警告，可能会导致无提示的运行时行为错误。编译器现在能够检测以这种方式编写的代码并通知程序员，并在匹配 `#pragma warning(pop)` 位置发出可选编译器警告 C5031（如果已启用）。此警告包含引用对应 \#pragma warning\(push\) 的位置的注释。  
  
 **警告 C5031：\#pragma warning\(pop\)：可能不匹配，弹出推入不同文件的警告状态**     示例（之前）  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h ... #pragma warning(pop)  // pops a warning state not pushed in this source file ... // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling' ... #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031 ...   
    ```  
  
     示例（之后）  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... #pragma warning(pop)  // pops the warning state pushed in this source file // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h #pragma warning(push)  // pushes the warning state pushed in this source file #pragma warning(disable:####) ... #pragma warning(pop) // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order. ... #include "C5031_part2.h" ...   
    ```  
  
     虽然不常见，但有时会有意用这种方式编写代码。以这种方式编写的代码对于 `#include` 顺序的更改比较敏感；如果可能，我们建议源代码文件以自包含的方式管理警告状态。  
  
-   **\#pragma warning\(push\) 不匹配**（只影响 \/Wall\/WX）  
  
     早期版本的编译器无法检测到翻译单元末尾出现的不匹配 `#pragma warning(push)` 状态更改。 编译器现在能够检测以这种方式编写的代码并通知程序员，并在不匹配的 \#pragma warning\(push\) 位置发出可选编译器警告 C5032（如果已启用）。 只有翻译单元中没有任何编译错误时，才会发出此警告。  
  
 **警告 C5032：检测到没有对应 \#pragma warning\(pop\) 的 \#pragma warning\(push\)**     示例（之前）  
  
    ```cpp  
    // C5032.h #pragma warning(push) #pragma warning(disable:####) ... // C5032.h ends without #pragma warning(pop) // C5032.cpp #include "C5032.h" ... // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h  
    ```  
  
     示例（之后）  
  
    ```cpp  
    // C5032.h #pragma warning(push) #pragma warning(disable:####) ... #pragma warning(pop) // matches #pragma warning (push) on line 1 // C5032.h ends // C5032.cpp #include "C5032.h" ... // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)  
    ```  
  
-   **\#pragma 警告状态跟踪改进后可能会发出更多警告**  
  
     早期版本的编译器无法有效跟踪 \#pragma 警告状态更改，因而无法发出所有所需的警告。 这种行为会引发风险，导致在程序不希望的情况下有效禁止显示某些警告。 编译器现在能够更加可靠地跟踪 \#pragma 警告状态，尤其与模板内部的 \#pragma 警告状态更改相关，并选择性发出新警告 C5031 和 C5032，旨在帮助程序员找到意外使用 `#pragma warning(push)` 和 `#pragma warning(pop)`。  
  
     由于改进了 \#pragma 警告状态更改跟踪，现在可能会发出以前错误地禁止显示的警告或与以前误诊问题的相关警告。  
  
-   **对无法访问代码标识的改进**  
  
     针对早期版本的编译器进行的 C\+\+ 标准库的更改和内联函数调用能力改进可能会使编译器能够证明某些代码现在无法访问。 这一新行为可能导致新警告并更频繁地发出警告 C4720 实例。  
  
 **警告 C4720：无法访问的代码**     在许多情况下，只有启用优化进行编译时，才会发出此警告，因为优化可能嵌入更多函数调用，消除冗余代码或者能够确定某些代码是否无法访问。 我们观察到，警告 C4720 的新实例在 try\/catch 块中经常发生，尤其是在使用 [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True) 时。  
  
     示例（之前）  
  
    ```cpp  
    try { auto iter = std::find(v.begin(), v.end(), 5); } catch(…) { do_something();  // ok }  
    ```  
  
     示例（之后）  
  
    ```cpp  
    try { auto iter = std::find(v.begin(), v.end(), 5); } catch(…) { do_something();  // warning C4702: unreachable code }  
    ```