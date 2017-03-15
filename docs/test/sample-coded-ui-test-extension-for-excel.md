---
title: "适用于 Excel 的示例编码的 UI 测试扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编码的 UI 测试, 适用于 Excel 的扩展"
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 13
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 13
---
# 适用于 Excel 的示例编码的 UI 测试扩展
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本示例的扩展组件在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 编码 UI 测试进程中运行，在层次结构上大致与 `ExtensionPackage` 类同处基层。  `TechnologyManager`、 `ActionFilter` 和 `PropertyProvider` 类处于下一层，控件元素则处于顶层。  
  
 ![Excel 测试扩展体系结构](../test/media/excel_extarch.png "Excel\_ExtArch")  
Excel 扩展体系结构  
  
## 扩展点  
 这些类表示在示例中实现的扩展点，这些扩展点用于为 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 启用编码 UI 测试。  
  
### ExtensionPackage  
 从 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> 类继承，这是编码 UI 测试扩展的入口点。  实现此抽象类可让编码 UI 测试框架从内部访问自定义 UI 测试技术管理器、UI 测试属性提供程序和用于测试新 UI 的 UI 测试操作筛选器。  有关更多信息，请参见[ExtensionPackage 类](../test/sample-excel-extension-extensionpackage-class.md)。  
  
### TechnologyManager  
 从 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> 类继承，此类提供用于测试录制和播放的技术管理器。  有关更多信息，请参见[TechnologyManager 类](../test/sample-excel-extension-technologymanager-class.md)。  
  
### ActionFilter  
 从 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> 类继承，此类提供用于将类似测试操作结果聚合为单一测试结果的基类。  有关更多信息，请参见[ActionFilter 类](../test/sample-excel-extension-actionfilter-class.md)。  
  
### 技术元素  
 从 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 类继承的基类为 UI 测试中可以录制和播放的技术元素提供了基础。  有关更多信息，请参见[Element 类](../test/sample-excel-extension-element-classes.md)。  
  
### PropertyProvider  
 从 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> 类继承，此类为支持用于测试录制和播放的 UI 元素属性提供了基类。  有关更多信息，请参见[PropertyProvider 类](../test/sample-excel-extension-propertyprovider-class.md)。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [ExtensionPackage 类](../test/sample-excel-extension-extensionpackage-class.md)   
 [TechnologyManager 类](../test/sample-excel-extension-technologymanager-class.md)   
 [ActionFilter 类](../test/sample-excel-extension-actionfilter-class.md)   
 [Element 类](../test/sample-excel-extension-element-classes.md)   
 [PropertyProvider 类](../test/sample-excel-extension-propertyprovider-class.md)