---
title: "属性窗口对象列表 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性窗口中，对象列表"
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 属性窗口对象列表
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 **属性** 窗口对象列表允许您更改选择到其他对象可在一个或多个所选窗口中的下拉列表。  选择不同的对象从此的内部列表触发器对 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> 通知该环境新的对象的部分。  然后将 **属性** 窗口中显示的信息显示属性与新选定的对象。  
  
## 对象列表  
 对象列表包含两个字段:对象名 \(显示在加粗\) 和对象类型。  
  
 在左侧显示的对象名目标类型粗体从对象中检索使用 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> 接口提供的 `Name` 属性。  <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>，在 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>的唯一方法，此方法返回该接口的 coclass 的 <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> 。  **属性** windows 使用 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> 获取 coclass 的名称，都显示为的对象名 " 下拉列表。  
  
 如果对象不具有 `Name` 属性，名称中的名称区域不显示对象列表。  可以将这些名称添加到对象属性是否希望在的名称显示对象列表。  
  
 如果 COM 对象不实现 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>， **属性** 窗口在对象名位置显示接口名称列表中的左侧。  
  
## 请参阅  
 [将属性扩展](../../extensibility/internals/extending-properties.md)