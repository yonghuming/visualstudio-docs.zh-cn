---
title: "示例 Excel 扩展：ExtensionPackage 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "mlearned"
manager: "douge"
---
# 示例 Excel 扩展：ExtensionPackage 类
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此类对 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> 类进行扩展，并为用于测试 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 工作表的编码 UI 测试提供入口点。  
  
## 程序集特性  
 文件以将程序集标识为 UI 测试扩展的程序集特性开头。  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 此特性声明基本类名、包类名称以及自定义扩展包类的完全限定类名。  
  
## 简单属性  
 此类的属性可提供编码的 UI 测试框架用于标识和描述扩展及程序集的值。  有关更多信息，请参见代码注释。  
  
## GetService 方法  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> 方法是由编码的 UI 测试框架使用的单个入口点，用于访问基类为每个对象标识的技术管理器、属性提供程序和操作筛选器。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [扩展编码的 UI 测试和操作录制以支持 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)