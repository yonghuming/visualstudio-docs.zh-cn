---
title: "示例 Excel 扩展：TechnologyManager 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# 示例 Excel 扩展：TechnologyManager 类
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此类扩展 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> 类并负责为 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 扩展提供核心服务。  该基类具有许多方法，但本示例仅使用了这些方法的一个子集。  
  
 某些方法仅返回属性值。  许多方法旨在允许开发人员将默认算法生成重写到编码的 UI 测试引擎中。  这些方法会引发 <xref:System.NotSupportedException> 或返回 `null`，从而指示框架使用默认算法。  
  
 根据基础技术的不同复杂程度，开发技术管理器代码可能需要几周到几个月的时间。  Excel 提供了创建可能十分广泛的技术管理器的机会。  此示例有意限制为 Excel 工作表和单元格，并使用有限的格式设置。  
  
 如果可能，技术管理器代码将使用由 `Communicator` 类打开的 .NET 远程处理通道从运行在 Excel 进程中的外接程序提取信息。  
  
## COM 可见性  
 请注意，此类以及扩展 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 类的每个元素类都具有值为 `true` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute>，以确保这些类对 COM 可见。  
  
## TechnologyName 属性  
 这种对 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> 属性的重写必须提供一个唯一且有意义的名称来标识该扩展的每个其他组件的基础技术。  对于此扩展，该值为“Excel”。  
  
## GetControlSupportLevel 方法  
 这种对 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> 方法的重写返回一个数字，该数字指示出技术管理器可为由所提供的句柄表示的控件提供的支持级别。  返回的值越大，技术管理器对控件的支持程度就越高。  在本例中，该方法检查包含控件的窗口，如果该窗口为 Excel 工作表，则该方法返回最大值；否则，该方法返回 0，表示不提供任何支持。  
  
## 用于获取元素的方法  
 编码的 UI 测试框架使用多个重要方法来获取该技术的特定元素，包括提供句柄、屏幕上的点或其他技术中的元素。  这些方法的代码一目了然。  基方法如下：  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## ParseQueryId 方法  
 创建编码的 UI 测试时，用户可以为该测试中的部分或全部控件指定属性值。  测试框架将使用这些属性值来创建称为搜索属性的名称\/值对，以用于在测试期间查找特定 UI 控件。  所有这些搜索属性一起表示包含每个控件的技术中每个元素的 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> 属性的值。  由于在测试期间可能必须多次查找某个控件，因此该方法为技术管理器提供了一个对给定控件的搜索属性分析进行优化的方法。  该方法还返回一个 Cookie，框架可使用该 Cookie 对该控件进行后续搜索。  这种方法实现使用 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> 方法来分析搜索属性。  
  
## MatchElement 方法  
 若要通过技术管理器执行控件搜索，可以实现 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> 方法以返回可能匹配项的数组，或引发 <xref:System.NotSupportedException>，后一方式将指示框架使用其自己的搜索算法。  无论采用哪种方式，都必须实现 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> 方法，在这种方法中，该实现会再次使用 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> 方法。  
  
## 导航方法  
 这些方法从 UI 层次结构获取所提供元素的父级、子级或同级。  代码十分简单并进行了清晰注释。  
  
## GetExcelElement 内部方法  
 此内部方法获取窗口句柄以及有关 Excel 元素的信息，并返回请求的 Excel 元素。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [扩展编码的 UI 测试和操作录制以支持 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)