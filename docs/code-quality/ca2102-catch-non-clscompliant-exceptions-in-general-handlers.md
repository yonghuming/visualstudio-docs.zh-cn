---
title: "CA2102：在常规处理程序中捕捉非 CLSCompliant 异常 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2102"
  - "CatchNonClsCompliantExceptionsInGeneralHandlers"
helpviewer_keywords: 
  - "CA2102"
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2102：在常规处理程序中捕捉非 CLSCompliant 异常
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|类别|Microsoft.Security|  
|是否重大更改|非重大更改|  
  
## 原因  
 程序集中未标记为 <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> 或标记为 `RuntimeCompatibility(WrapNonExceptionThrows = false)` 的某个成员包含一个处理 <xref:System.Exception?displayProperty=fullName> 的 catch 块，并且不包含紧跟其后的一般 catch 块。  此规则忽略 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 程序集。  
  
## 规则说明  
 处理 <xref:System.Exception> 的 catch 块会捕获所有符合公共语言规范 \(CLS\) 的异常。  但是，它不捕获不符合 CLS 的异常。  不符合 CLS 的异常可以从本机代码中引发，或者从 Microsoft 中间语言 \(MSIL\) 汇编程序生成的托管代码中引发。  请注意，C\# 和 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 编译器不允许引发不符合 CLS 的异常，并且 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 不捕获不符合 CLS 的异常。  如果 catch 块的目的是处理所有异常，请使用下面的一般 catch 块语法。  
  
-   C\#：`catch {}`  
  
-   C\+\+：`catch(...) {}` 或 `catch(Object^) {}`  
  
 当从 catch 块中移除以前允许的权限时，未处理的、不符合 CLS 的异常将变成安全隐患。  因为不符合 CLS 的异常不被捕获，所以引发不符合 CLS 异常的恶意方法将可以用提升的权限运行。  
  
## 如何解决冲突  
 若要在目标是捕获所有异常的情况下修复此与规则的冲突，请替代或添加一般 catch 块或者将程序集标记为 `RuntimeCompatibility(WrapNonExceptionThrows = true)`。  如果移除了 catch 块中的权限，请复制一般 catch 块中的功能。  如果目标不是处理所有异常，请将处理 <xref:System.Exception> 的 catch 块替换为处理具体异常类型的 catch 块。  
  
## 何时禁止显示警告  
 如果 try 块不包含任何可能生成不符合 CLS 的异常的语句，可以安全地禁止显示此规则发出的警告。  因为任何本机代码或托管代码都可能引发不符合 CLS 的异常，所以这要求了解可以在 try 块的所有代码路径中执行的所有代码。  请注意，不符合 CLS 的异常不是由公共语言运行时引发的。  
  
## 示例  
 下面的示例演示引发不符合 CLS 的异常的 MSIL 类。  
  
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
  
## 示例  
 下面的示例演示一个包含满足此规则的一般 catch 块的方法。  
  
 [!code-cs[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 按以下方式编译前面的示例。  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## 相关规则  
 [CA1031：不要捕捉一般异常类型](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)  
  
## 请参阅  
 [异常和异常处理](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe（IL 汇编程序）](../Topic/Ilasm.exe%20\(IL%20Assembler\).md)   
 [Overriding Security Checks](http://msdn.microsoft.com/zh-cn/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [语言独立性和与语言无关的组件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)