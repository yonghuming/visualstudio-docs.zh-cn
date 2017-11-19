---
title: "了解 SAL |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d1c6ac08b47bd5ad5e6dd84bbf78496c421a21a6
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="understanding-sal"></a>了解 SAL
Microsoft 源代码注释语言 (SAL) 提供一组你可以使用来描述函数如何使用其参数、 有关，它使的假设和它使它完成时的保证的批注。 标头文件中定义批注`<sal.h>`。 C + + 的 visual Studio 代码分析使用 SAL 批注来修改其分析的函数。 适用于 Windows 驱动程序开发 SAL 2.0 的详细信息，请参阅[SAL 2.0 批注的 Windows 驱动程序](http://go.microsoft.com/fwlink/?LinkId=250979)。  
  
 本机，C 和 c + + 提供开发人员的意图并不变性一致地 express 仅有限的方式。 通过使用 SAL 批注，你可以描述更详细地了解函数，以便开发人员使用它们可以更好地了解如何使用它们。  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>什么是 SAL 以及您为何使用它?  
 简言之，SAL 是一种成本较低的方法，让编译器可以为你检查你的代码。  
  
### <a name="sal-makes-code-more-valuable"></a>SAL 使代码更重要  
 SAL 可以帮助你使你的代码设计更易于理解，对于理解和代码分析工具。 请看以下示例显示 C 运行时函数`memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 知道此函数的？ 当实现或调用一个函数时，某些属性必须得到维护，以确保程序正确性。 只需通过查看如示例中的声明时，你不知道这些凭据。 如果没有 SAL 批注，您将必须依赖于文档或代码注释。 下面是有关的 MSDN 文档`memcpy`显示：  
  
> "副本计算 src 到目标的字节的数。 如果源和目标重叠，memcpy 的行为不确定。 Memmove 用于处理重叠区域。   
> **安全说明：**大小等于或大于源缓冲区请确保目标缓冲区是否相同。 有关详细信息，请参阅避免缓冲区溢出。"  
  
 该文档包含几个建议，你的代码必须维护某些属性，以确保程序正确性的位的信息：  
  
-   `memcpy`副本`count`从源缓冲区到目标缓冲区的字节。  
  
-   目标缓冲区必须至少与源缓冲区一样大。  
  
 但是，编译器无法读取该文档或非正式的注释。 它不知道两个缓冲区之间不存在关系和`count`，和它也不能有效地猜测关系。 SAL 无法提供有关的属性和函数，实现更加清晰，如下所示：  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 请注意，这些批注类似于 MSDN 文档中的信息，但它们更简明，它们遵循语义的模式。 当读取此代码时，您可以快速了解此函数的属性以及如何避免缓冲区溢出安全问题。 更理想的做法 SAL 提供的语义模式可以提高效率和在早期的潜在 bug 发现中的自动的代码分析工具的有效性。 假设有人将写入此错误实现的`wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 此实现包含一种常见关闭一个错误。 幸运的是，代码创作者包含的 SAL 缓冲区大小批注-代码分析工具无法通过分析此单独的函数捕获 bug。  
  
### <a name="sal-basics"></a>SAL 基础  
 SAL 定义四种基本类型的参数，按使用模式进行分类。  
  
|类别|参数批注|描述|  
|--------------|--------------------------|-----------------|  
|**输入调用函数**|`_In_`|数据传递给调用的函数，并以只读方式处理。|  
|**输入调用函数，并输出到调用方**|`_Inout_`|可以使用的数据传递给函数，并可能被修改。|  
|**到调用方的输出**|`_Out_`|调用方仅提供要写入的调用函数的空间。 所调用的函数将数据写入到该空间。|  
|**指向调用方的输出**|`_Outptr_`|如**输出到调用方**。 被调用函数返回的值是一个指针。|  
  
 这些四个基本批注可更明确采用各种方法。 默认情况下，带批注的指针参数都被认为是所需-它们必须为非 NULL，当函数为成功。 基本的批注的最常使用变体指示指针参数是可选的-如果它为 NULL，函数可以仍会成功中执行其工作。  
  
 下表显示如何区分必需和可选参数：  
  
||参数是必需的|参数是可选的|  
|-|-----------------------------|-----------------------------|  
|**输入调用函数**|`_In_`|`_In_opt_`|  
|**输入调用函数，并输出到调用方**|`_Inout_`|`_Inout_opt_`|  
|**到调用方的输出**|`_Out_`|`_Out_opt_`|  
|**指向调用方的输出**|`_Outptr_`|`_Outptr_opt_`|  
  
 这些批注帮助识别可能未初始化的值，并以正式且准确的方式使用无效的 null 指针。 将 NULL 传递给所需的参数可能会导致崩溃，或者它可能导致要返回的"失败"的错误代码。 两种方式的函数中执行其作业无法成功。  
  
## <a name="sal-examples"></a>SAL 示例  
 本部分说明的代码示例的基本的 SAL 批注。  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>使用 Visual Studio 代码分析工具查找 Bug  
 在示例中，Visual Studio 代码分析工具用于与 SAL 批注一起查找代码缺陷。 下面介绍了如何执行该操作。  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>使用 Visual Studio 代码分析工具和 SAL  
  
1.  在 Visual Studio 中，打开一个包含 SAL 批注的 c + + 项目。  
  
2.  在菜单栏上，选择**生成**，**对解决方案运行代码分析**。  
  
     请考虑 _In\_本部分中的示例。 如果在其上运行代码分析，则显示此警告：  
  
    > **C6387 无效的参数值**   
    > 点可能是"0": 这不符合函数 InCallee 的规范。  
  
### <a name="example-the-in-annotation"></a>示例： _In\_批注  
 `_In_`批注指示：  
  
-   参数必须是有效，并且将不会修改。  
  
-   该函数仅将从单个元素缓冲区读取。  
  
-   调用方必须提供缓冲区，并对其进行初始化。  
  
-   `_In_`指定"只读"。 一个常见错误，将应用`_In_`到应有的参数`_Inout_`批注相反。  
  
-   `_In_`允许在非指针参数标量分析器但忽略。  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 如果在此示例使用 Visual Studio 代码分析，它会验证调用方将非 Null 指针传递到初始化缓冲区`pInt`。 在这种情况下，`pInt`指针不能为 NULL。  
  
### <a name="example-the-inopt-annotation"></a>示例： _In_opt\_批注  
 `_In_opt_`等同于`_In_`，只不过允许输入的参数为 NULL，因此，该函数应检查这一点。  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Visual Studio 代码分析验证函数检查为空，然后才能访问缓冲区。  
  
### <a name="example-the-out-annotation"></a>示例： 缩小 （_o)\_批注  
 `_Out_`支持一种常见的方案，在其中传入指向元素缓冲区的非 NULL 指针和函数初始化元素。 调用方无需调用; 之前将缓冲区初始化所调用的函数承诺来返回之前对其进行初始化。  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 Visual Studio 代码分析工具验证调用方将非 NULL 指针传递给缓冲区`pInt`和其返回之前，将缓冲区初始化函数。  
  
### <a name="example-the-outopt-annotation"></a>示例： _Out_opt\_批注  
 `_Out_opt_`等同于`_Out_`，只不过允许参数为 NULL，因此，该函数应检查这一点。  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio 代码分析会验证此函数检查 null 之前`pInt`取消引用，并且如果`pInt`不为 NULL，返回之前，由该函数初始化缓冲区。  
  
### <a name="example-the-inout-annotation"></a>示例： _Inout\_批注  
 `_Inout_`用于对可能会发生更改函数的指针参数进行批注。 指针必须指向有效的调用之前初始化的数据，即使它更改，它仍需返回时必须具有有效的值即可。 批注指定函数可能自由地读取和写入到一个元素缓冲区。 调用方必须提供缓冲区，并对其进行初始化。  
  
> [!NOTE]
>  如`_Out_`，`_Inout_`必须将应用于可修改的值。  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // 'pInt' should not be NULL  
}  
  
```  
  
 Visual Studio 代码分析验证调用方将非 NULL 指针传递到初始化缓冲区`pInt`，而且，在返回时之前,`pInt`仍非 null 和初始化缓冲区。  
  
### <a name="example-the-inoutopt-annotation"></a>示例： _Inout_opt\_批注  
 `_Inout_opt_`等同于`_Inout_`，只不过允许输入的参数为 NULL，因此，该函数应检查这一点。  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio 代码分析会验证此函数检查是否为空，它访问缓冲区中之前，且是否`pInt`不为 NULL，返回之前，由该函数初始化缓冲区。  
  
### <a name="example-the-outptr-annotation"></a>示例： _Outptr\_批注  
 `_Outptr_`用于添加批注具有用于返回指针的参数。  参数本身不应为 NULL，所调用的函数在它返回非 NULL 指针和该指针指向初始化的数据。  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 Visual Studio 代码分析验证调用方传递的非 NULL 指针`*pInt`，并返回之前，将缓冲区初始化函数。  
  
### <a name="example-the-outptropt-annotation"></a>示例： _Outptr_opt\_批注  
 `_Outptr_opt_`等同于`_Outptr_`，只不过该参数是可选-调用方可以传递一个 NULL 指针的参数。  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Visual Studio 代码分析会验证此函数检查 null 之前`*pInt`取消引用，并返回之前，将缓冲区初始化函数。  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>示例： _Success\_批注结合缩小 （_o）\_  
 批注还可应用于大多数对象。  具体而言，还可以批注整个函数。  函数的最明显的特征之一是它可以成功或失败。 但如缓冲区和其大小之间的关联，C/c + + 不能表达函数成功或失败。 通过使用`_Success_`批注，您可以说出哪些成功函数如下所示。  参数`_Success_`批注是仅为 true 指示该函数已成功完成的表达式。 表达式可以是任何批注分析器可以处理。 如果该函数成功，则在函数返回之后的批注的效果才适用。 此示例演示如何`_Success_`与交互`_Out_`以执行正确的操作。 你可以使用关键字`return`来表示的返回值。  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 `_Out_`批注会导致 Visual Studio 代码分析，以验证调用方将非 NULL 指针传递给缓冲区`pInt`，并返回之前，将缓冲区初始化函数。  
  
## <a name="sal-best-practice"></a>SAL 最佳做法  
  
### <a name="adding-annotations-to-existing-code"></a>向现有代码中添加批注  
 SAL 是代码的一种功能强大的技术，可帮助你提高的安全性和可靠性的你。 了解 SAL 后，你可以对您的日常工作应用新的技能。 在新代码中，可以通过在整个; 设计使用基于 SAL 的规范在较旧的代码中，可以以增量方式添加批注和每次更新，从而提高效益。  
  
 已批注 Microsoft 公共标头。 因此，我们建议，在你的项目中首先批注叶节点函数和调用 Win32 Api，以获得最佳结果的函数。  
  
### <a name="when-do-i-annotate"></a>何时批注?  
 以下是一些准则：  
  
-   批注所有指针参数。  
  
-   批注值范围批注，以便代码分析可以确保缓冲区和指针的安全性。  
  
-   批注锁定规则和锁定的副作用。 有关详细信息，请参阅[批注锁定行为](../code-quality/annotating-locking-behavior.md)。  
  
-   批注驱动程序属性和其他特定于域的属性。  
  
 或者，还可以批注整个你的意图更明显并使其更方便地进行检查，进行了批注的所有参数。  
  
## <a name="related-resources"></a>相关资源  
 [代码分析团队博客](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>另请参阅  
 [使用 SAL 批注以减少 C/c + + 代码缺陷](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [对函数参数和返回值进行批注](../code-quality/annotating-function-parameters-and-return-values.md)   
 [对函数行为进行批注](../code-quality/annotating-function-behavior.md)   
 [批注结构和类](../code-quality/annotating-structs-and-classes.md)   
 [对锁定行为进行批注](../code-quality/annotating-locking-behavior.md)   
 [指定何时以及在何处应用批注](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [最佳做法和示例](../code-quality/best-practices-and-examples-sal.md)