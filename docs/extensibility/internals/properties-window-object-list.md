---
title: "属性窗口对象列表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dad79623bbc721c67c19a37436d2bf5e64b93c59
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="properties-window-object-list"></a>属性窗口对象列表
中的对象列表**属性**窗口是下拉列表，您可以将所选内容更改为一个或多个选择的 windows 中可用的其他对象。 选择在此列表中的不同对象触发调用<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>以通知环境已选择新的对象。 中显示的信息**属性**窗口然后更改为显示与新选择的对象关联的属性。  
  
## <a name="the-object-list"></a>对象列表  
 对象列表包含两个字段: （以粗体显示） 的对象名称和对象类型。  
  
 以粗体显示的对象类型的左侧显示的对象名称检索从对象本身使用`Name`由提供属性<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>接口。 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>上的唯一方法<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>，返回<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>为该接口的组件类。 **属性**窗口使用<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>若要获取的组件类，显示为下拉列表中的对象名称的名称。  
  
 如果对象不具有`Name`对象列表的名称区域中不显示属性，一个名称。 如果你想在对象列表中显示的名称，可以向对象中添加一个 Name 属性。  
  
 如果 COM 对象没有实现<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>、**属性**窗口在左侧的列表显示代替对象名称的接口名称。  
  
## <a name="see-also"></a>另请参阅  
 [扩展属性](../../extensibility/internals/extending-properties.md)