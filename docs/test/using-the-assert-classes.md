---
title: "使用 Assert 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assert 类"
  - "Assert 语句"
  - "单元测试, Assert 语句"
  - "单元测试, Assert 类"
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "mlearned"
manager: "douge"
---
# 使用 Assert 类
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 UnitTestingFramework 命名空间的 Assert 类可对特定功能进行验证。  单元测试方法执行开发代码中的方法代码，但只有包含 Assert 语句时才能报告代码正确性方面的内容。  
  
## Assert 类型  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 命名空间提供若干类型的 Assert 类：  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 在测试方法中，可以调用任意数量的 Assert 类方法，如 Assert.AreEqual\(\)。  Assert 类有很多方法可供选择，其中许多方法具有若干重载。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 使用 CollectionAssert 类可比较对象集合，也可验证一个或多个集合的状态。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 使用 StringAssert 类可对字符串进行比较。  此类包含各种有用的方法，如 StringAssert.Contains、StringAssert.Matches 和 StringAssert.StartsWith。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 只要测试失败，就会引发 AssertFailedException 异常。  如果测试超时，引发意外的异常，或包含生成了 Failed 结果的 Assert 语句，则该测试失败。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 只要测试生成的结果为 Inconclusive，就会引发 AssertInconclusiveException。  通常，向仍在处理的测试添加 Assert.Inconclusive 语句可指示该测试尚未准备好，不能运行。  
  
> [!NOTE]
>  或者可以使用 Ignore 特性标记没有准备好、尚不能运行的测试。  但是，这样做的弊端是无法轻松生成尚要实现的测试数量的报告。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 编写新的 Assert 异常类时使该类从基类 UnitTestAssertException 进行继承，可更方便地将异常标识为断言失败而非从测试或产品代码引发的意外异常。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 如果希望开发代码中的某方法引发异常，又想用测试方法来验证是否真的在该方法中引发了异常，则请用 ExpectedExceptionAttribute 特性来修饰测试方法。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>   
 [针对现有代码创建并运行单元测试](http://msdn.microsoft.com/zh-cn/e8370b93-085b-41c9-8dec-655bd886f173)