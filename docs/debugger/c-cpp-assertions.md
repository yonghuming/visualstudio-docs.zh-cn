---
title: "C/C++ 断言 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "_DEBUG 宏"
  - "ASSERT 宏"
  - "“断言失败”对话框"
  - "断言"
  - "断言, 副作用"
  - "“调用堆栈”窗口, 断言失败"
  - "调试 [C++], 断言"
  - "调试 [MFC], 断言"
  - "错误 [C++], 用断言捕获"
  - "失败, 查找位置"
  - "结果检查"
  - "结果, 检查"
  - "测试, 带有断言语句的错误条件"
  - "VERIFY 宏"
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C/C++ 断言
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

一条断言语句指定一个条件，您认为在您的程序中的一个点，则返回 true。  如果该条件不为 true，则断言失败，程序执行中断，并将[断言失败对话框中](../debugger/assertion-failed-dialog-box.md)出现。  
  
 Visual C\+\+ 支持基于下列构造的断言语句：  
  
-   MFC 程序的 MFC 断言。  
  
-   [ATLASSERT](../Topic/ATLASSERT.md) 的程序的使用 atl。  
  
-   使用 C 运行时库的程序的 CRT 断言。  
  
-   ANSI [断言函数](/visual-cpp/c-runtime-library/reference/assert-macro-assert-wassert)其他 C\/c \+ \+ 程序。  
  
 可以使用断言来捕捉逻辑错误、 检查操作的结果和测试错误条件，应已处理。  
  
##  <a name="BKMK_In_this_topic"></a> 本主题中  
 [断言的工作原理](#BKMK_How_assertions_work)  
  
 [在调试和发布版本中的断言](#BKMK_Assertions_in_Debug_and_Release_builds)  
  
 [使用断言的负面影响](#BKMK_Side_effects_of_using_assertions)  
  
 [CRT 断言](#BKMK_CRT_assertions)  
  
 [MFC 断言](#BKMK_MFC_assertions)  
  
-   [MFC ASSERT_VALID 和 CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  
  
-   [AssertValid 的限制](#BKMK_Limitations_of_AssertValid)  
  
 [使用断言](#BKMK_Using_assertions)  
  
-   [捕捉逻辑错误](#BKMK_Catching_logic_errors)  
  
-   [检查结果](#BKMK_Checking_results_)  
  
-   [查找未处理的错误](#BKMK_Testing_error_conditions_)  
  
##  <a name="BKMK_How_assertions_work"></a> 断言的工作原理  
 当调试器由于 MFC 或 C 运行时库断言而暂停时，然后如果源代码可用，调试器定位到在源文件中的断言发生点。  断言消息同时出现在[输出窗口](../ide/reference/output-window.md) 和 **断言失败**对话框。  您可以将断言消息从复制**输出**窗口到文本窗口中，如果您想要将其保存以供将来参考。  **输出**窗口可能还包含其它错误信息。  仔细检查这些消息，因为它们提供了有关确定断言失败原因的线索。  
  
 请使用断言，可以在开发过程中检测到错误。  通常，使用每个假设一个断言。  例如，如果您假定参数不为 NULL，使用断言来测试这一假定。  
  
 [本主题中](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> 在调试和发布版本中的断言  
 断言语句编译时才`_DEBUG`定义。  否则，编译器将作为空语句的断言。  因此，断言语句强加任何开销或性能成本在最终发布程序中，并允许您避免使用`#ifdef`指令。  
  
##  <a name="BKMK_Side_effects_of_using_assertions"></a> 使用断言的负面影响  
 当向代码添加断言时，请确保这些断言没有副作用。  例如，请考虑以下断言修改`nM`值：  
  
```  
ASSERT(nM++ > 0); // Don't do this!  
  
```  
  
 因为`ASSERT`在程序的发行版中未计算表达式  `nM`将在调试和发布版本具有不同的值。  若要避免此问题，在 MFC 中的，您可以使用[验证](../Topic/VERIFY.md) 宏，而不是  `ASSERT`.   `VERIFY`在所有版本中的表达式的计算结果，但不检查结果的发布版本中。  
  
 应特别小心断言语句中使用函数调用，因为计算函数可能会有意外的副作用。  
  
```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  
  
 `VERIFY`调用  `myFnctn`在调试和发行版本中，因此是可以接受的使用。  但是，使用`VERIFY`在发布版本中不必要的函数调用的开销。  
  
 [本主题中](#BKMK_In_this_topic)  
  
##  <a name="BKMK_CRT_assertions"></a> CRT 断言  
 CRTDBG。H 头文件中定义 [\_ASSERT 和 \_ASSERTE 宏](/visual-cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros)的断言检查。  
  
|宏|结果|  
|-------|--------|  
|`_ASSERT`|如果指定的表达式的计算结果为 FALSE 时，文件名和行号的 `_ASSERT`.|`_ASSERTE`|  
|`_ASSERTE`|作为同一 `_ASSERT`，加上所断言的表达式的字符串表示形式。|  
  
 `_ASSERTE`因为它可以报告被证明是假的断言的表达式是功能更强大。  这可能不足以识别问题的源代码引用。  但是，您的应用程序的调试版本将包含断言使用的每个表达式的字符串常量 `_ASSERTE`.  如果您使用多个`_ASSERTE`宏，这些字符串表达式将占用相当数量的内存。  如果有问题，请使用`_ASSERT`以节省内存。  
  
 当`_DEBUG`定义，  `_ASSERTE`宏的定义如下：  
  
```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  
  
 如果断言的表达式的计算结果为 FALSE 时，  [\_CrtDbgReport](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) 调用报告断言失败 （默认情况下，使用消息对话框中）。  如果您选择**重试** 在消息对话框中，  `_CrtDbgReport`返回 1 和  `_CrtDbgBreak`调用调试器通过  `DebugBreak`.  
  
### 检查堆损坏  
 下面的示例使用 [\_CrtCheckMemory](/visual-cpp/c-runtime-library/reference/crtcheckmemory) 检查堆损坏：  
  
```  
_ASSERTE(_CrtCheckMemory());  
```  
  
### 检查指针有效性  
 下面的示例使用 [\_CrtIsValidPointer](/visual-cpp/c-runtime-library/reference/crtisvalidpointer) 验证给定的内存范围无效，读取或写入。  
  
```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  
  
 下面的示例使用 [\_CrtIsValidHeapPointer](/visual-cpp/c-runtime-library/reference/crtisvalidheappointer) 若要验证一个指针，指向本地堆中的内存 （堆创建，并由 C 运行时库的此实例 — DLL 可以有它自己的实例的库中，因此它自己堆，外部应用程序的堆）。  此断言捕获不只为空或超出边界的地址，但也为静态变量、 堆栈变量，以及任何其他非本地内存的指针。  
  
```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  
  
### 检查内存块  
 下面的示例使用 [\_CrtIsMemoryBlock](/visual-cpp/c-runtime-library/reference/crtismemoryblock) 以验证内存块在本地堆中，并且具有有效的块类型。  
  
```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  
  
 [本主题中](#BKMK_In_this_topic)  
  
##  <a name="BKMK_MFC_assertions"></a> MFC 断言  
 MFC 定义 [ASSERT](../Topic/ASSERT%20\(MFC\).md) 宏检查断言。  它还定义了`MFC ASSERT_VALID`和  `CObject::AssertValid`方法可以检查内部状态的  `CObject`\-派生的对象。  
  
 如果 MFC 的参数`ASSERT`宏计算结果为零或假，宏将暂停程序执行并警告用户 ； 否则，执行继续。  
  
 当断言失败时，一个消息对话框显示的源文件和行号声明的名称。  如果您选择重试在对话框中，对的调用 [AfxDebugBreak](../Topic/AfxDebugBreak%20\(MFC\).md) 使得执行中断到调试器。  此时，您可以检查调用堆栈和其他调试器功能用于确定断言失败的原因。  如果您启用了[在实时调试](../debugger/just-in-time-debugging-in-visual-studio.md)，并且调试器已不在运行，该对话框可以启动调试器。  
  
 下面的示例演示如何使用`ASSERT`检查函数的返回值：  
  
```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  
  
 您可以使用 ASSERT 与 [IsKindOf](../Topic/CObject::IsKindOf.md) 函数来提供类型检查函数参数：  
  
```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  
  
 `ASSERT`宏会在发行版本中的没有代码。  如果您需要在发布版本中的表达式进行求值，则使用[验证](../Topic/VERIFY.md)宏，而不是断言。  
  
###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT\_VALID 和 CObject::AssertValid  
 [CObject::AssertValid](../Topic/CObject::AssertValid.md) 方法提供了运行时检查的对象的内部状态。  虽然不要求您重写`AssertValid`时，派生类从  `CObject`，您可以使您的类更可靠这样。  `AssertValid`应执行断言，所有对象的成员变量，以验证它们包含有效的值。  例如，它应检查指针成员变量不能为空。  
  
 下面的示例演示如何声明`AssertValid`函数：  
  
```  
class CPerson : public CObject  
{  
protected:  
    CString m_strName;  
    float   m_salary;  
public:  
#ifdef _DEBUG  
    // Override  
    virtual void AssertValid() const;  
#endif  
    // ...  
};  
  
```  
  
 当您重写 `AssertValid`，请调用基类版本的  `AssertValid`在执行您自己的检查之前。  然后使用 ASSERT 宏检查您的派生类特有的成员如下所示：  
  
```  
#ifdef _DEBUG  
void CPerson::AssertValid() const  
{  
    // Call inherited AssertValid first.  
    CObject::AssertValid();  
  
    // Check CPerson members...  
    // Must have a name.  
    ASSERT( !m_strName.IsEmpty());  
    // Must have an income.  
    ASSERT( m_salary > 0 );  
}  
#endif  
  
```  
  
 如果所有的成员变量存储的对象，则可以使用`ASSERT_VALID`宏，以测试其内部的有效性 （如果它们的类重写  `AssertValid`）。  
  
 例如，考虑一个类 `CMyData`，哪些商店  [coblist）](/visual-cpp/mfc/reference/coblist-class) 在其成员变量之一。   `CObList`变量中，   `m_DataList`，存储的集合  `CPerson`对象。  简化的声明`CMyData`如下所示：  
  
```  
class CMyData : public CObject  
{  
    // Constructor and other members ...  
    protected:  
        CObList* m_pDataList;  
    // Other declarations ...  
    public:  
#ifdef _DEBUG  
        // Override:  
        virtual void AssertValid( ) const;  
#endif  
    // And so on ...  
};  
  
```  
  
 `AssertValid`在重写  `CMyData`如下所示：  
  
```  
#ifdef _DEBUG  
void CMyData::AssertValid( ) const  
{  
    // Call inherited AssertValid.  
    CObject::AssertValid( );  
    // Check validity of CMyData members.  
    ASSERT_VALID( m_pDataList );  
    // ...  
}  
#endif  
  
```  
  
 `CMyData`使用  `AssertValid`测试存储其数据成员中的对象的有效性的机制。  重写`AssertValid`的  `CMyData`调用  `ASSERT_VALID`宏为自己的 m\_pDataList 成员变量。  
  
 有效性测试不会停止在这一级别因为类`CObList`还重写  `AssertValid`.  此重写执行附加有效性测试列表的内部状态。  因此，有效性测试`CMyData`对象会导致内部状态的存储附加有效性测试  `CObList`list 对象。  
  
 一些更多的工作，还可以添加对的有效性测试`CPerson`也存储在列表中的对象。  无法派生类`CPersonList`从  `CObList`和重写  `AssertValid`.  在重写中，您就可以调用 `CObject::AssertValid`，然后循环访问列表，调用  `AssertValid`每个  `CPerson`存储在列表中的对象。   `CPerson`已经在本主题的开始处显示的类重写  `AssertValid`.  
  
 当为调试生成时，这是一种功能强大的机制。  当您接着为发布生成时，机制是自动关闭。  
  
###  <a name="BKMK_Limitations_of_AssertValid"></a> AssertValid 的限制  
 触发的断言指示对象一定有误，并且执行将停止。  但是，缺少断言只指示将未找到任何问题，但不是保证对象是好。  
  
 [本主题中](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Using_assertions"></a> 使用断言  
  
###  <a name="BKMK_Catching_logic_errors"></a> 捕捉逻辑错误  
 条件必须都为真，根据程序的逻辑上，可以设置断言。  除非发生逻辑错误，则肯定不起作用。  
  
 例如，假设您正在模拟容器中，并且该变量中的气体分子`numMols`表示分子总数。  此数字不能小于零，因此可以包含 MFC 断言语句如下：  
  
```  
ASSERT(numMols >= 0);  
  
```  
  
 或者，您可以包含如下的 CRT 断言：  
  
```  
_ASSERT(numMols >= 0);  
```  
  
 如果您的程序正常运行这些语句不执行任何操作。  如果出现逻辑错误导致`numMols` 小于零，但是，断言将暂停程序执行并显示  [“断言失败”对话框](../debugger/assertion-failed-dialog-box.md).  
  
 [本主题中](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Checking_results_"></a> 检查结果  
 断言很有价值的测试的操作的结果不明显的快速目测检验。  
  
 例如，请考虑下面的代码，这将更新变量`iMols`所指向的链接列表的内容基于  `mols`::  
  
```  
/* This code assumes that type has overloaded the != operator  
 with const char *   
It also assumes that H2O is somewhere in that linked list.   
Otherwise we'll get an access violation... */  
while (mols->type != "H2O")  
{  
 iMols += mols->num;  
 mols = mols->next;  
}  
ASSERT(iMols<=numMols); // MFC version  
_ASSERT(iMols<=numMols); // CRT version  
```  
  
 由计数的分子数`iMols`必须始终小于或等于分子，总数  `numMols`.  目测检验循环不会显示这一定是这种情况，因此，断言语句在循环后用来测试该条件。  
  
 [本主题中](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Testing_error_conditions_"></a> 查找未处理的错误  
 可以使用断言来测试代码中的错误条件的点位置的任何错误应已处理。  在下面的示例中，一个图形例程将返回错误代码或零表示成功。  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* Code to handle errors and  
   reset myErr if successful */  
  
ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  
  
 如果错误处理代码工作正确，应已处理错误和`myErr`重置为零，在到达断言之前。  如果`myErr`有另一个值，则断言失败，程序暂停，并将  [“断言失败”对话框](../debugger/assertion-failed-dialog-box.md)出现。  
  
 断言语句不但是错误处理代码的替代方案。  下面的示例显示一条断言语句在最终发布代码的问题可能会：  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* No Code to handle errors */  
  
ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  
  
 此代码依赖于断言语句来处理错误条件。  因此，任何错误代码返回的`myGraphRoutine`将在最终发布代码中未经处理。  
  
 [本主题中](#BKMK_In_this_topic)  
  
## 请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [调试本机代码](../debugger/debugging-native-code.md)   
 [托管代码中的断言](../debugger/assertions-in-managed-code.md)