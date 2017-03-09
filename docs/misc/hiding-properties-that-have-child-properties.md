---
title: "隐藏具有子属性的属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性 [Visual Studio SDK], 隐藏"
  - "属性窗口, 隐藏具有子属性的属性"
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# 隐藏具有子属性的属性
您需要隐藏具有子属性的属性:  
  
-   如果嵌套父项目以编程方式控制子项的某些方面的项目。  
  
-   如果使用具有专用的设计器的控件，并且不希望为完全访问权限的开发人员控件的所有属性。  
  
-   如果您具有对象的大小所有权并希望限制属性视图。  
  
### 隐藏具有子属性的属性  
  
1.  将 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> 的 `pfDisplay` 参数传递给 `FALSE`。  
  
2.  将 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> 的 `pfHide` 参数传递给 `TRUE`。  
  
## 请参阅  
 [显示属性网格](../extensibility/internals/properties-display-grid.md)