---
title: "示例 Excel 扩展：ActionFilter 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 11
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 11
---
# 示例 Excel 扩展：ActionFilter 类
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此内部类扩展 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> 类并表示用于 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 元素的测试操作的筛选器。  
  
## 简单属性  
 借助这些只读属性，开发人员可以指定编码的 UI 测试框架如何执行此测试操作筛选器。  例如，<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> 属性提供操作筛选器的名称。  其他属性可获取操作筛选器的 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>、此测试操作筛选器筛选的测试操作的 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> 名称。  其他属性指示是否 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> 以及测试操作是否为 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>。  
  
## ProcessRule 方法  
 此方法由编码的 UI 测试框架调用，它针对提供的 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> 执行筛选器。  ，当堆栈中的下一个操作向单元格发送键击时，此特定重写移除鼠标选择到单元格的事件。  此后，它会返回 `false`。  
  
## private 方法  
 `IsLeftClick` 方法确定提供的操作是否表示单击鼠标左键。  `AreActionsOnSameExcelCell` 方法确定是否对 Excel 中的同一单元格执行两个提供的操作。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [扩展编码的 UI 测试和操作录制以支持 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)