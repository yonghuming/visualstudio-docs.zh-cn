---
title: "CA2118： 检查 SuppressUnmanagedCodeSecurityAttribute 用法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 92728eae21d4a3035f0396957fa643d14ef06e1c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118：检查 SuppressUnmanagedCodeSecurityAttribute 用法
|||  
|-|-|  
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或受保护的类型或成员具有<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>属性。  
  
## <a name="rule-description"></a>规则说明  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>执行使用 COM 互操作或平台调用的非托管的代码的成员更改默认的安全系统行为。 通常情况下，系统会进行[数据和建模](/dotnet/framework/data/index)非托管的代码权限。 此要求为每个成员，运行时将会发生，并且检查权限的调用堆栈中的每个调用方。 当存在该属性时，系统会进行[链接需求](/dotnet/framework/misc/link-demands)的权限： 调用方进行 JIT 编译时，将检查直接调用方的权限。  
  
 该特性主要用于提高性能；不过，提高性能的同时会显著增加安全风险。 如果您将该属性放置在调用本机方法的公共成员时，调用堆栈 （而不是直接调用方） 中的调用方不必执行非托管的代码的非托管的代码权限。 根据公共成员的操作和输入的处理，则可能会使不受信任调用方访问功能通常仅限由可信的代码。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]依赖于安全性检查，以防止调用方直接访问当前进程的地址空间。 此属性会绕过常规安全，因为你的代码将造成严重的威胁，如果可以用于读取或写入到进程的内存。 请注意风险并不局限于有意提供进程内存; 的访问的方法该按钮还出现在任何情况下，其中恶意代码可以访问通过任何方式，例如，通过实现提供令人惊讶、 格式不正确，或无效的输入。  
  
 默认安全策略不到程序集授予托管的代码的权限，除非它正在执行从本地计算机，或者是以下组之一的成员：  
  
-   我计算机区域代码组  
  
-   Microsoft 强名称代码组  
  
-   ECMA 强名称代码组  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 请仔细查看你的代码以确保绝对需要此属性。 如果你不熟悉托管的代码安全或不了解的安全隐患的使用此属性，请在代码中将其删除。 如果该属性是必需的你必须确保调用方不能出于恶意使用你的代码。 如果你的代码不具有执行非托管的代码的权限，此属性不起作用，应删除。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 若要安全地禁止显示此规则的警告，你必须确保你的代码不提供调用方对本机操作或可以以的破坏性方式使用的资源的访问。  
  
## <a name="example"></a>示例  
 下面的示例与该规则冲突。  
  
 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## <a name="example"></a>示例  
 在下面的示例中，`DoWork`方法提供平台调用方法的可公开访问的代码路径`FormatHardDisk`。  
  
 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## <a name="example"></a>示例  
 在下面的示例中的公共方法`DoDangerousThing`导致冲突。 若要解决该冲突，`DoDangerousThing`应设为专用，并对其的访问应通过受安全要求，保护一个公共方法，如图所示`DoWork`方法。  
  
 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [安全编码准则](/dotnet/standard/security/secure-coding-guidelines)   
 [安全优化](http://msdn.microsoft.com/en-us/cf255069-d85d-4de3-914a-e4625215a7c0)   
 [数据和建模](/dotnet/framework/data/index)  
 [链接需求](/dotnet/framework/misc/link-demands)  
  