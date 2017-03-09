---
title: "CA2118：检查 SuppressUnmanagedCodeSecurityAttribute 用法 | Microsoft Docs"
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
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
helpviewer_keywords: 
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2118：检查 SuppressUnmanagedCodeSecurityAttribute 用法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 公共或受保护的类型或成员具有 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> 特性。  
  
## 规则说明  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 为使用 COM 互操作或平台调用执行非托管代码的成员更改默认的安全性系统行为。  一般，系统为非托管代码权限进行 [数据和建模](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)。  在运行阶段对成员的每次调用都会提出此要求，此要求将检查调用堆栈中每个调用方的权限。  如果该特性存在，系统会对为该权限提出 [链接需求](../Topic/Link%20Demands.md)：对调用方进行 JIT 编译时，会检查直接调用方的权限。  
  
 该特性主要用于提高性能；不过，提高性能的同时会显著增加安全风险。  如果将特性放入调用本机方法的公共成员中，则调用堆栈中的调用方（非直接调用方）不需要非托管代码权限即可执行非托管代码。  根据公共成员的操作和输入处理，它可能会允许不可信的调用方访问通常仅限由可信代码访问的功能。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 依赖安全检查来防止调用方获得对当前进程的地址空间的直接访问权限。  由于该特性跳过常规安全性，因此如果可使用它读取或写入进程的内存，那么您的代码可能面临严重威胁。  请注意，风险不仅限于有意提供对进程内存的访问权限的方法；只要恶意代码可通过提供意外、格式不正确或无效输入等任何方式获得访问权限，就存在风险。  
  
 默认安全策略不会将非托管代码权限授予程序集，除非该程序集在本地计算机上或由下列组之一的成员执行：  
  
-   My Computer Zone Code Group  
  
-   Microsoft Strong Name Code Group  
  
-   ECMA Strong Name Code Group  
  
## 如何解决冲突  
 请认真检查代码，确保绝对需要该特性。  如果您不熟悉托管代码安全性，或不了解使用该特性会产生的问题，请将其从您的代码中移除。  如果需要该特性，必须确保调用方不能出于恶意使用您的代码。  如果您的代码不具有执行非托管代码的权限，则该特性将没有作用，应将其移除。  
  
## 何时禁止显示警告  
 若要安全地禁止显示此规则发出的警告，必须确保您的代码不会为调用方提供对可以破坏性的方式加以使用的本机操作或资源的访问权限。  
  
## 示例  
 下面的示例与该规则冲突。  
  
 [!code-cs[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## 示例  
 在下面的示例中，`DoWork` 方法提供指向平台调用方法 `FormatHardDisk` 的可公开访问的代码路径。  
  
 [!code-cs[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## 示例  
 在下面的示例中，公共方法 `DoDangerousThing` 导致冲突。  要解决该冲突，应将 `DoDangerousThing` 设置为私有，并应该通过由安全请求保护的公共方法访问它，如 `DoWork` 方法所示。  
  
 [!CODE [FxCop.Security.TypeInvokeAndSuppress#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress#1)]  
  
## 请参阅  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [代码安全维护指南](../Topic/Secure%20Coding%20Guidelines.md)   
 [Security Optimizations](http://msdn.microsoft.com/zh-cn/cf255069-d85d-4de3-914a-e4625215a7c0)   
 [数据和建模](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)   
 [链接需求](../Topic/Link%20Demands.md)