---
title: "CA2109：检查可见的事件处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2109"
  - "ReviewVisibleEventHandlers"
helpviewer_keywords: 
  - "CA2109"
  - "ReviewVisibleEventHandlers"
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2109：检查可见的事件处理程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ReviewVisibleEventHandlers|  
|CheckId|CA2109|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 检测到公共事件处理方法或受保护事件处理方法。  
  
## 规则说明  
 某外部可见的事件处理方法带来了需要检查的安全问题。  
  
 除非绝对必要，否则不应公开事件处理方法。  只要事件处理程序和事件签名匹配，就可以将调用已公开方法的该事件处理程序（委托类型）添加到任何事件。  事件可能会由任何代码引发，并经常为响应单击按钮等用户操作由高度信任的系统代码不断引发。  将安全检查添加到事件处理方法并不影响代码注册调用该方法的事件处理程序。  
  
 某请求无法可靠地保护由事件处理程序调用的方法。  通过检查调用堆栈上的调用方，安全请求有助于保护来自不受信任调用方的代码。  在事件处理程序的方法运行时，调用堆栈上不需要有将事件处理程序添加到事件的代码。  因此，在调用事件处理程序方法时调用堆栈可能只有高度受信任的调用方。  这导致事件处理程序方法发出的请求成功。  另外，在调用该方法时可能断言了所要求的权限。  由于上述原因，只能在检查事件处理方法后评估不修复与该规则的冲突的风险。  在检查代码时，请考虑下列问题：  
  
-   事件处理程序是否执行危险或可利用的任何操作，例如断言权限或取消非托管代码权限？  
  
-   如果代码只能由堆栈上高度受信任调用方随时运行，则对代码的安全威胁和来自代码的安全威胁有哪些？  
  
## 如何解决冲突  
 要修复与该规则的冲突，请检查该方法并评估以下条件：  
  
-   是否可以使事件处理方法成为非公共的？  
  
-   是否可以将所有危险的功能移出事件处理程序？  
  
-   如果设定了安全请求，是否可以通过一些其他方式完成此请求？  
  
## 何时禁止显示警告  
 仅在经过仔细安全检查以确保代码不构成安全威胁后，才禁止显示此规则发出的警告。  
  
## 示例  
 下面的代码演示可以被恶意代码误用的事件处理方法。  
  
 [!code-cs[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## 请参阅  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 [Security Demands](http://msdn.microsoft.com/zh-cn/324c14f8-54ff-494d-9fd1-bfd20962c8ba)