---
title: "CA2102： 在常规处理程序中捕捉非 CLSCompliant 异常 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords: CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a27054ef8732b96d5d71cbc22d567f4509877886
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102：在常规处理程序中捕捉非 CLSCompliant 异常
|||  
|-|-|  
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|类别|Microsoft.Security|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 中未用标记程序集的成员<xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute>或标记`RuntimeCompatibility(WrapNonExceptionThrows = false)`包含处理的 catch 块<xref:System.Exception?displayProperty=fullName>，并且不包含紧跟其后的一般 catch 块。 此规则将忽略[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]程序集。  
  
## <a name="rule-description"></a>规则说明  
 处理的 catch 块<xref:System.Exception>捕获所有的公共语言规范 (CLS) 符合异常。 但是，它不会捕获非 CLS 的异常。 不符合 CLS 可能会引发符合异常，从本机代码或从托管代码生成了 Microsoft 中间语言 (MSIL) 汇编程序。 请注意，C# 和[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]编译器不允许不符合 CLS 引发的异常和[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]不捕捉非 CLS 的异常。 如果在 catch 块的目的是处理所有异常，则使用以下常规 catch 块语法。  
  
-   C#：`catch {}`  
  
-   C + +:`catch(...) {}`或`catch(Object^) {}`  
  
 在 catch 块中删除以前允许的权限时，未处理的非 CLS 符合异常将成为安全问题。 由于不符合 CLS 符合异常未被捕获，引发的异常的不符合 CLS 的恶意方法无法使用提升的权限运行。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突时的目的在于捕捉所有异常，替换或添加的一般 catch 块或标记程序集`RuntimeCompatibility(WrapNonExceptionThrows = true)`。 如果在 catch 块中删除了权限，重复的功能在常规 catch 块。 如果它不是试图处理所有异常，将处理的 catch 块<xref:System.Exception>与都处理特定异常类型的 catch 块。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果 try 块不包含任何可能会生成不符合 CLS 符合异常的语句。 由于任何本机或托管代码可能引发不符合 CLS 符合异常，这需要可以在 try 块内的所有代码路径中执行的所有代码的了解。 请注意，不符合 CLS 符合异常不由公共语言运行时引发。  
  
## <a name="example"></a>示例  
 下面的示例演示引发不符合 CLS 符合异常 MSIL 类。  
  
```  
.assembly ThrowNonClsCompliantException {}  
.class public auto ansi beforefieldinit ThrowsExceptions  
{  
   .method public hidebysig static void  
         ThrowNonClsException() cil managed  
   {  
      .maxstack  1  
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()  
      IL_0005:  throw  
   }  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例演示包含满足该规则的常规 catch 块的方法。  
  
 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 编译前面的示例，如下所示。  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## <a name="related-rules"></a>相关的规则  
 [CA1031：不要捕捉一般异常类型](../code-quality/ca1031-do-not-catch-general-exception-types.md)  
  
## <a name="see-also"></a>另请参阅  
 [异常和异常处理](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe（IL 汇编程序）](/dotnet/framework/tools/ilasm-exe-il-assembler)   
 [重写安全检查](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [语言独立性和与语言无关的组件](http://msdn.microsoft.com/Library/4f0b77d0-4844-464f-af73-6e06bedeafc6)