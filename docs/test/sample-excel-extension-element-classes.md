---
title: "示例 Excel 扩展：Element 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "mlearned"
manager: "douge"
---
# 示例 Excel 扩展：Element 类
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

扩展使用从 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 派生的类，这些类在 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 中表示工作表控件和单元格控件。  
  
 此扩展的基元素为 `ExcelElement`。  `ExcelWorksheetElement` 类和 `ExcelCellElement` 类从该元素派生  
  
## Element 和 ElementInformation 类  
 `Element`  是 Excel 扩展的所有用户界面元素的基类，它继承自 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 类。  `ElementInformation` 是示例中元素信息类的基类，并且它没有成员。  
  
#### 简单属性和方法  
 这些成员返回简单值，如 `Name` 属性的值或 `ClassName` 属性的值，并且代码清晰易读。  一些值是使用 `Utility` 类返回的，稍后对此进行讨论。  其他成员返回 `null`，因为它们与此示例扩展无关。  有两个成员与其他成员相比更令人感兴趣：<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> 属性和 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> 方法。  
  
#### QueryId 属性  
 此属性返回一个由属性名称\/值对组成的条件，在播放过程中，这些名称\/值对可以唯一地标识控件。  对于每个派生的控件类，开发人员必须重写此属性以返回一个 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> 对象，框架可以使用该对象在 UI 中查找该控件。  
  
#### CacheProperties 方法  
 此方法由测试框架在录制期间调用，以提醒元素保存重要属性的快照。  这样，这些属性在实际 UI 控件不再位于屏幕上时仍然可用。  
  
## WorksheetElement 和 WorksheetInformation 类  
 `WorksheetElement`  类在测试框架中表示 Excel 工作表，该类继承自 `Element` 基类。  将会重写这三个属性以提供有关 Excel 工作表对象的特定信息：<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> 和 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>。  
  
 还可以对此类应用 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 以使其对 COM 可见。  
  
 `WorksheetInformation`  类提供有关 Excel 工作表的信息。  它只有一个成员，即 `SheetName` 属性，这对于本示例而言已足够。  
  
## CellElement 和 CellInformation 类  
 `CellElement`  类表示 Excel 单元格，它继承自 `Element` 基类。  唯一重写的成员是 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> 属性，该属性返回一个使用 `RowIndex` 和 `ColumnIndex` 属性来标识单元格的 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>。  
  
## Utilities 和 ExcelUtilities 类  
 内部 `ExcelUtilities` 类提供一些常量值（如技术名称）和一个方法，该方法可确定提供的窗口句柄是否表示 Excel 工作表。  
  
 `Utilities`  类拥有可以返回各种 UI 相关信息的帮助器方法。  一些方法直接调用外部系统 DLL（如 **USER32.DLL** 和 **OLEACC.DLL**），以便从 UI**.** 获取窗口句柄。  
  
## 请参阅  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [扩展编码的 UI 测试和操作录制以支持 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)