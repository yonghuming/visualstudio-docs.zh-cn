---
title: "模板策略和属性窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性窗口中，模板策略"
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 模板策略和属性窗口
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

如果项目包含在企业模板项目中时，该业务模板项目可以强制策略。  模板策略成为可用于设置属性的默认值，隐藏属性，添加特性，\) 的受约束的系统。  
  
 使用模板策略控制信息显示在 **属性** 窗口中与实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>不同。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 处理在组件级别的对象，属性，而模板策略可用于绑定对象属性在解决方案或项目级别。  换句话说  
  
-   执行在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 的方法确定在特定对象的 **属性** 将显示窗口。  
  
-   使用模板策略在解决方案和项目级别确定到指定的对象的 **属性** 将显示窗口。  
  
 使用模板策略有选择地约束。 **属性** 窗口的特定属性，在特定类型的项目项。 **解决方案资源管理器** 中选择很有用于项目工作的开发团队的所有成员。  例如，使用模板策略，在中，您在一个数据库中可以设置所有连接字符串信息的开发人员并使连接字符串是只读的。  在这样，您可以提供了一种简单的方法确保每个开发人员进行数据访问使用正确的路径。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [将属性扩展](../../extensibility/internals/extending-properties.md)