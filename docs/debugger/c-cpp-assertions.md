---
title: "C/c + + 断言 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eaa6ba7a5ba88d3a7f5ff2b8f9f7571c26a3baf4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="cc-assertions"></a>C/C++ 断言
断言语句指定您希望在程序中点应满足的条件。 如果该条件不为 true，则断言失败，程序的执行被中断，和[断言失败对话框](../debugger/assertion-failed-dialog-box.md)显示。  
  
 Visual c + + 支持基于以下构造的断言语句：  
  
-   MFC 程序的 MFC 断言。  
  
-   [ATLASSERT](http://msdn.microsoft.com/Library/98e3e0fc-77e2-499b-a6f6-b17a21c6fbd3)的程序的使用 atl。  
  
-   使用 C 运行时库的程序的 CRT 断言。  
  
-   ANSI [assert 函数](/cpp/c-runtime-library/reference/assert-macro-assert-wassert)其他 C/c + + 程序。  
  
 可以使用断言捕捉逻辑错误、 检查操作的结果和测试应已处理的错误条件。  
  
##  <a name="BKMK_In_this_topic"></a> 主题内容  
 [断言的工作原理](#BKMK_How_assertions_work)  
  
 [调试和发布版本中的断言](#BKMK_Assertions_in_Debug_and_Release_builds)  
  
 [使用断言的副作用](#BKMK_Side_effects_of_using_assertions)  
  
 [CRT 断言](#BKMK_CRT_assertions)  
  
 [MFC 断言](#BKMK_MFC_assertions)  
  
-   [MFC ASSERT_VALID 和 CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  
  
-   [AssertValid 的限制](#BKMK_Limitations_of_AssertValid)  
  
 [使用断言](#BKMK_Using_assertions)  
  
-   [捕捉逻辑错误](#BKMK_Catching_logic_errors)  
  
-   [检查结果](#BKMK_Checking_results_)  
  
-   [查找未经处理的错误](#BKMK_Testing_error_conditions_)  
  
##  <a name="BKMK_How_assertions_work"></a>断言的工作原理  
 当调试器暂停由于 MFC 或 C 运行时库断言时，然后源是否可用，如果调试器导航到断言的发生位置的源文件中的点。 断言消息同时出现在[输出窗口](../ide/reference/output-window.md)和**断言失败**对话框。 你可以复制断言消息从**输出**窗口文本窗口中，如果你想要将其保存以供将来参考。 **输出**窗口可能包含其他错误信息。 这些消息仔细检查，因为它们提供了断言失败的原因的线索。  
  
 使用断言，以在开发过程中检测错误。 一般来说，为每个假设使用一个断言。 例如，当你假定参数不为 NULL，使用断言测试这一假定。  
  
 [主题内容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a>调试和发布版本中的断言  
 断言语句编译仅当`_DEBUG`定义。 否则，编译器将断言视为 null 语句。 因此，断言语句在施加无开销或性能成本在最终版本程序中，并允许你可以避免使用`#ifdef`指令。  
  
##  <a name="BKMK_Side_effects_of_using_assertions"></a>使用断言的副作用  
 当将断言添加到你的代码时，请确保断言不具有副作用。 例如，考虑以下的断言，修改`nM`值：  
  
```  
ASSERT(nM++ > 0); // Don't do this!  
  
```  
  
 因为`ASSERT`程序，发行版中未计算表达式`nM`将在调试和发布版本具有不同的值。 若要避免此问题在 MFC 中的，可以使用[验证](http://msdn.microsoft.com/Library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96)宏而不是`ASSERT`。  `VERIFY`在所有版本中的表达式的计算结果，但不会检查的版本中的结果。  
  
 应特别小心断言语句中使用函数调用，因为计算函数可能会产生意外的副作用。  
  
```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  
  
 `VERIFY`调用`myFnctn`在调试和发布版本中，因此它是可接受的使用。 但是，使用`VERIFY`有一定的发行版中的不必要的函数调用的开销。  
  
 [主题内容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_CRT_assertions"></a>CRT 断言  
 CRTDBG。H 标头文件中定义[_ASSERT 和 _ASSERTE 宏](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros)有关断言检查。  
  
|宏|结果|  
|-----------|------------|  
|`_ASSERT`|如果指定的表达式的计算结果为 FALSE 时，文件名称和行号的`_ASSERT`。|`_ASSERTE`|  
|`_ASSERTE`|与相同`_ASSERT`，加上的字符串表示形式所断言的表达式。|  
  
 `_ASSERTE`因为它可以报告断言的表达式结果为 FALSE，则是更强大。 这可能是足够可以识别问题，而不会引用的源代码。 但是，你的应用程序的调试版本将包含断言使用每个表达式的字符串常量`_ASSERTE`。 如果使用许多`_ASSERTE`宏，这些字符串表达式将占用大量的内存。 如果，证明是问题，使用`_ASSERT`以节省内存。  
  
 当`_DEBUG`定义，`_ASSERTE`宏的定义如下：  
  
```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  
  
 如果断言的表达式的计算结果为 FALSE， [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)调用以报告断言失败 （默认情况下，使用一个消息对话框）。 如果你选择**重试**在消息对话框中，`_CrtDbgReport`返回 1 和`_CrtDbgBreak`调用通过调试器`DebugBreak`。  
  
### <a name="checking-for-heap-corruption"></a>检查堆损坏  
 下面的示例使用[_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory)检查堆损坏：  
  
```  
_ASSERTE(_CrtCheckMemory());  
```  
  
### <a name="checking-pointer-validity"></a>检查指针有效性  
 下面的示例使用[_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer)验证给定的内存范围是否有效的读取或写入。  
  
```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  
  
 下面的示例使用[_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer)要验证是否指针指向本地堆中的内存 (堆创建和管理由 C 运行时库的此实例-DLL 只能有自己的库中，实例和因此自己的堆，外部应用程序堆）。 此断言不捕获仅 null 或超出边界的地址，但还对静态变量，堆栈变量以及任何其他非本地内存的指针。  
  
```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  
  
### <a name="checking-a-memory-block"></a>检查的内存块  
 下面的示例使用[_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock)若要验证的本地堆中的内存块，并且具有有效的块类型。  
  
```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  
  
 [主题内容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_MFC_assertions"></a>MFC 断言  
 MFC 定义[断言](http://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)的宏，断言检查。 它还定义`MFC ASSERT_VALID`和`CObject::AssertValid`方法可以检查的内部状态`CObject`-派生对象。  
  
 如果 MFC 的自变量`ASSERT`宏计算结果为零或 false，宏会停止程序执行，通知用户; 否则，执行会继续运行。  
  
 当一个断言失败时，消息对话框中显示的名称的源文件和断言的行号。 如果你在对话框中选择重试框中，调用[AfxDebugBreak](http://msdn.microsoft.com/Library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30)会导致执行中断到调试器。 此时，你可以检查调用堆栈和其他调试器功能用于确定断言失败的原因。 如果已启用[中实时调试](../debugger/just-in-time-debugging-in-visual-studio.md)，并且调试器已不在运行，该对话框可以启动调试器。  
  
 下面的示例演示如何使用`ASSERT`要检查的函数的返回值：  
  
```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  
  
 你可以使用与 ASSERT [IsKindOf](/cpp/mfc/reference/cobject-class.md#CObject__IsKindOf)函数以提供类型检查的函数自变量：  
  
```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  
  
 `ASSERT`宏生成发行版中的任何代码。 如果你需要计算该表达式的发行版中，使用[验证](http://msdn.microsoft.com/Library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96)宏而不是断言。  
  
###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a>MFC ASSERT_VALID 和 CObject::AssertValid  
 [CObject::AssertValid](/cpp/mfc/reference/cobject-class.md#CObject__AssertValid)方法提供了运行时检查的对象的内部状态。 尽管你无需重写`AssertValid`从您的类派生时`CObject`，你可以使您的类更可靠通过执行此操作。 `AssertValid`上的所有对象的成员变量，以验证它们包含有效的值，应都执行断言。 例如，它应检查指针成员变量不为 NULL。  
  
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
  
 当你重写`AssertValid`，调用的基类版本`AssertValid`执行您自己的检查之前。 然后使用 ASSERT 宏检查成员唯一的派生类中，如下所示：  
  
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
  
 如果任何成员变量存储对象，则可以使用`ASSERT_VALID`宏来测试其内部的有效性 (如果它们的类重写`AssertValid`)。  
  
 例如，考虑一个类`CMyData`，哪些存储[CObList](/cpp/mfc/reference/coblist-class)一个其成员变量中。 `CObList`变量， `m_DataList`，存储的集合`CPerson`对象。 简化的声明`CMyData`如下所示：  
  
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
  
 `AssertValid`中重写`CMyData`如下所示：  
  
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
  
 `CMyData`使用`AssertValid`机制以测试在其数据成员中存储的对象的有效性。 重写`AssertValid`的`CMyData`时，将调用`ASSERT_VALID`自己 m_pDataList 成员变量的宏。  
  
 有效性测试不会停止在此级别因为类`CObList`还将重写`AssertValid`。 此替代执行附加有效性测试列表的内部状态。 因此，有效期测试`CMyData`对象导致存储的内部状态的其他有效性测试`CObList`列表对象。  
  
 一些更多的工作，还可以添加对的有效性测试`CPerson`也存储在列表中的对象。 无法派生一个类`CPersonList`从`CObList`，并重写`AssertValid`。 重写时，将调用`CObject::AssertValid`，然后循环访问列表中，调用`AssertValid`上每个`CPerson`列表中存储的对象。 `CPerson`类显示在本主题开头已重写`AssertValid`。  
  
 为调试生成时，这是功能强大的机制。 当你随后生成版本时，机制被自动关闭。  
  
###  <a name="BKMK_Limitations_of_AssertValid"></a>AssertValid 的限制  
 触发的断言指示该对象是一定有误且将停止执行。 但是，缺少断言仅指示将未找到任何问题，但该对象不能保证无法正常工作。  
  
 [主题内容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Using_assertions"></a>使用断言  
  
###  <a name="BKMK_Catching_logic_errors"></a>捕捉逻辑错误  
 你可以按照在必须为 true 根据你的程序逻辑的条件设置断言。 断言无任何影响，除非发生逻辑错误。  
  
 例如，假设你正在模拟一个容器，而变量中的天然气分子`numMols`表示分子总数。 此数字不能小于零，因此你可能会包括 MFC 断言语句如下：  
  
```  
ASSERT(numMols >= 0);  
  
```  
  
 或者，你可能会包括如下的 CRT 断言：  
  
```  
_ASSERT(numMols >= 0);  
```  
  
 如果你的程序正常运行，这些语句将不执行任何操作。 如果逻辑错误导致`numMols`能小于零，但是，则断言暂停程序的执行并显示[断言失败对话框](../debugger/assertion-failed-dialog-box.md)。  
  
 [主题内容](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Checking_results_"></a>检查结果  
 断言很有价值用于测试其结果并非明显来自快速 visual 检查的操作。  
  
 例如，考虑下面的代码，这将更新变量`iMols`基于链接列表指向的内容`mols`:  
  
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
  
 通过计数的分子数`iMols`必须始终小于或等于分子，总数`numMols`。 Visual 检查的循环不会显示，这一定会这种情况，因此断言语句循环后使用来测试该条件。  
  
 [主题内容](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Testing_error_conditions_"></a>查找未经处理的错误  
 可以使用断言要测试在的点处的错误情况你的代码在其中的任何错误应已处理。 在下面的示例中，图形例程返回错误代码或零表示成功。  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* Code to handle errors and  
   reset myErr if successful */  
  
ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  
  
 如果错误处理代码可以正常工作，应处理该错误和`myErr`重置为零之前断言为止。 如果`myErr`具有另一个值，则断言失败，程序暂停，和[断言失败对话框](../debugger/assertion-failed-dialog-box.md)显示。  
  
 断言语句不是替代的错误处理代码，但是。 下面的示例演示可能导致在最终发行代码中的问题的断言语句：  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* No Code to handle errors */  
  
ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  
  
 此代码依赖于断言语句来处理错误条件。 因此，任何返回错误代码`myGraphRoutine`将在最终发行代码中未经处理。  
  
 [主题内容](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>另请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [调试本机代码](../debugger/debugging-native-code.md)   
 [托管代码中的断言](../debugger/assertions-in-managed-code.md)