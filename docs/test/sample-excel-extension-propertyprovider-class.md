---
title: "示例 Excel 扩展：PropertyProvider 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# 示例 Excel 扩展：PropertyProvider 类
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此内部类扩展 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> 类并为 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 元素提供属性服务以录制和播放用户界面 \(UI\) 测试。  
  
## GetControlSupportLevel 方法  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> 方法返回一个数字，该数字指示属性提供程序可为所提供的控件提供的支持级别。  返回的值越大，属性提供程序对控件的支持程度就越高。  在此方案中，此方法会检查提供的控件的 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> 属性的值。  如果该值为“Excel”且 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> 指示该值为 `CellElement`，此方法将返回最大值；否则返回零，指示不提供任何支持。  
  
## GetPropertyNames 方法  
 返回受支持 Excel 单元格控件属性的属性名称和属性说明符的字典。  
  
## GetPropertyDescriptor 方法  
 此方法由测试框架调用来获取提供的属性名称的预定义属性说明符。  
  
## GetPropertyValue 和 SetPropertyValue 方法  
 `GetPropertyValue` 方法使用此扩展的 `Communicator` 类从 Excel 返回属性值。  `SetPropertyValue` 方法使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> 类和 `Communicator` 组件设置属性值。  这些方法由测试框架调用。  
  
## 代码生成自定义方法  
 将不对此扩展实现这些方法。  因此，这些方法将返回 `null` 或引发 <xref:System.NotImplementedException>。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [扩展编码的 UI 测试和操作录制以支持 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)