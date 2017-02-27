---
title: "最佳做法和示例 (SAL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 最佳做法和示例 (SAL)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

这里有一些方法，可以获得最大的源代码注释语言（SAL），并避免一些常见的问题。  
  
## \_In\_  
 如果函数应写入元素，请使用 `_Inout_` 而不是 `_In_`。  这在从旧的宏自动转换为SAL的情况下尤为重要。  在 SAL 之前，许多程序员使用的宏作为注释—名为 `IN`、`OUT`， `IN_OUT`的宏或变量。  尽管建议您转换这些宏为SAL，但在转换时仍需注意，因为该代码可能已经改变，因为原来写入的原型和老宏可能不再反映代码的作用。  请特别小心有关 `OPTIONAL`注释 宏，因为它摆放的位置通常不正确—例如，在逗号错误的一边。  
  
```cpp  
  
// Incorrect  
void Func1(_In_ int *p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
  
// Correct  
void Func2(_Inout_ PCHAR p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
  
```  
  
## \_opt\_  
 如果调用者不允许传递一个空指针、使用 `_In_` 或 `_Out_` 而不是 `_In_opt_` 或 `_Out_opt_`。  这甚至检查应用于其参数并返回 false 的函数，当它不应为空时为空。  虽然具有测试其意外的 NULL 的参数的函数并返回适当好方法是一个好的防御性编码习惯，这并不意味着参数注释可以是一个选项类型 \(\_*Xxx*\_opt\_）。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_opt_ int *p1)  
{  
    *p = 1;  
}  
  
// Correct  
void Func2(_Out_ int *p1)  
{  
    *p = 1;  
}  
  
```  
  
## \_Pre\_defensive\_ 和 \_Post\_defensive\_  
 如果函数出现在信任边界，建议您改用 `_Pre_defensive_` 注释。“防御型”修饰符修改一些注释来暗示，指针调用，严格检查接口，但是，在方法体内应假定不可能出现不正确的参数传递。  在此情况下，`_In_ _Pre_defensive_` 优先信任边界意味着，尽管调用方在尝试传递空值时会出现错误，函数体将被分析，如果该参数可能是NULL，因此，任何未先检查它是否为空就尝试取消引用指针的都会被标记。注释 `_Post_defensive_` 还可用，使用受信任的方假定为调用方的回调，并且不信任的代码为被调用的代码。  
  
## \_Out\_writes\_  
 下面的示例显示了一个常见的`_Out_writes_`误用。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 注释 `_Out_writes_` 表示可具有缓冲区。  它在退出具有 `cb` 字节分配，其中第一字节初始化。  此注释不严格为 false，并且表示分配的大小很有用。  但是，它不显示函数初始化了多少个元素。  
  
 下一个示例演示三个完全指定缓冲区初始化的确切大小的正确方法。  
  
```cpp  
  
// Correct  
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,   
    DWORD size,  
    PDWORD pCount  
);  
  
void Func2(_Out_writes_all_(size) CHAR *pb,   
    DWORD size  
);  
  
void Func3(_Out_writes_(size) PSTR pb,   
    DWORD size  
);  
  
```  
  
## \_Out\_ PSTR  
 使用 `_Out_ PSTR` 几乎始终是错误的。  这可解释为具有到字符的映射点缓存的输出参数并且以 null 结尾。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 一个类似 `_In_ PCSTR` 的注释都通用和有用。  它指向输入具有 NULL 结尾的字符串，因为 `_In_` 的前提条件允许 null 终止的字符串标识的。  
  
## \_In\_ WCHAR\* p  
 `_In_ WCHAR* p` 添加具有一个字符的输入指针 `p`。  但是，在大多数情况下，这可能不是预期的规范。  相反，可能应该是 null 终止数组的规范；为此，请使用 `_In_ PWSTR`。  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 缺少 NULL 终止的相应规范是通用的。  如下面的示例所示，使用相应的 `STR` 版本替换类型。  
  
```cpp  
  
// Incorrect  
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
// Correct  
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
```  
  
## \_Out\_range\_  
 如果该参数属于指针，并且您想表示指针指向的元素的值的范围，请使用 `_Deref_out_range_` 而不是 `_Out_range_`。  在下面的示例中，显示的是\*pcbFilled 的范围而不是 pcbFilled。  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Out_range_(0, cbSize) DWORD *pcbFilled  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled   
);  
  
```  
  
 `_Deref_out_range_(0, cbSize)` 并不严格需要某些工具，因为可从 `_Out_writes_to_(cbSize,*pcbFilled)`推断，在这里显示是出于完整性的考虑。  
  
## \_When\_ 中的上下文有误  
 另一个常见错误是前置条件状态的使用后期计算。  在下面的示例中，`_Requires_lock_held_` 是一个前提。  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 表达式 `result` 是指不适用于预状态的后状态值。  
  
## 在 \_Success\_ 中为 TRUE  
 如果函数成功执行，则返回值非零时，请使用 `return != 0` 作为成功条件而不是 `return == TRUE`。  非零不一定表示和编译器为 `TRUE`提供的实际值相等。   `_Success_` 的参数是一个表达式，并且以下表达式被认为是等效的：`return != 0`、`return != false`、`return != FALSE`和 `return` 不带任何参数或比较。  
  
```cpp  
  
// Incorrect  
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
// Correct  
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
```  
  
## 引用变量  
 对于引用变量，SAL 早期版本使用了隐式的指针作为注释目标并且需要添加一个 `__deref` 到附加到引用变量的注释。  此版本使用自身对象而不需要额外的 `_Deref_`。  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
```  
  
## 返回值的批注  
 下面的示例演示返回值注释的一个常见问题。  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 在此示例中，`_Out_opt_`表示指针可能为 NULL 作为前置条件的一部分。  但是，前置条件不能应用于返回值。  在这种情况下，正确的注释为 `_Ret_maybenull_`。  
  
## 请参阅  
 [使用 SAL 批注以减少 C\/C\+\+ 代码缺陷](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [对函数参数和返回值进行批注](../code-quality/annotating-function-parameters-and-return-values.md)   
 [对函数行为进行批注](../code-quality/annotating-function-behavior.md)   
 [批注结构和类](../code-quality/annotating-structs-and-classes.md)   
 [对锁定行为进行批注](../code-quality/annotating-locking-behavior.md)   
 [指定何时以及在何处应用批注](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [内部函数](../code-quality/intrinsic-functions.md)