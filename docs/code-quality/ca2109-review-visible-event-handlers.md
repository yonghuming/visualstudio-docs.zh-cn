---
title: "CA2109： 检查可见的事件处理程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d558526f89b96c01e8bc7aba593d9c2b7f2654b0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109：检查可见的事件处理程序
|||  
|-|-|  
|TypeName|ReviewVisibleEventHandlers|  
|CheckId|CA2109|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 检测到公共事件处理方法或受保护事件处理方法。  
  
## <a name="rule-description"></a>规则说明  
 外部可见的事件处理方法显示需要查看安全问题。  
  
 除非绝对必要，否则不应公开事件处理方法。 事件处理程序，调用公开的方法的委托类型，可以添加到的任何事件，只要的处理程序和事件的签名匹配。 事件经常引起以响应用户操作，例如单击按钮的高度受信任的系统代码和可能引起的任何代码。 将一种安全检查添加到事件处理方法不会阻止代码注册事件处理程序调用的方法。  
  
 要求不能可靠地保护由事件处理程序调用的方法。 安全请求有助于防止不受信任的调用方的代码，通过检查调用堆栈上的调用方。 事件处理程序的方法运行时，将事件处理程序添加到事件的代码不一定存在调用堆栈上。 因此，调用堆栈可能仅高度受信任的调用方调用事件处理程序方法时。 这将导致发出的事件处理程序方法的成功请求。 此外，调用方法时，可能会声明要求的权限。 出于这些原因，仅可以在查看事件处理方法后评估不修复与此规则的冲突的风险。 当查看你的代码时，请考虑以下问题：  
  
-   事件处理程序是否执行任何危险或利用，如断言权限或禁止显示非托管的代码权限的操作？  
  
-   什么是与你的代码的安全威胁，因为它可以仅高度运行随时与受信任调用方在堆栈上？  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请检查该方法，并评估以下：  
  
-   你可以将此事件处理方法非公共？  
  
-   可以将事件处理程序外的所有危险功能？  
  
-   如果施加安全要求，这可以以某种其他方式？  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 禁止显示此规则警告只有在仔细的安全检查后，若要确保你的代码不会带来的安全威胁。  
  
## <a name="example"></a>示例  
 下面的代码演示了可能被恶意代码误用了事件处理方法。  
  
 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 [安全要求](http://msdn.microsoft.com/en-us/324c14f8-54ff-494d-9fd1-bfd20962c8ba)