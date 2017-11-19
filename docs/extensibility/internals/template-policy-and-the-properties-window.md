---
title: "模板策略和属性窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72460f39cf63346106c2ccd81dc9ab16f8af78b9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="template-policy-and-the-properties-window"></a>模板策略和属性窗口
当项目包含在企业级模板项目中时，则该企业级模板项目可强制实施策略。 模板策略将成为一个约束的系统，可用来设置属性的默认值、 隐藏属性，添加属性，依次类推。  
  
 使用模板策略来控制中的信息显示**属性**窗口是不同的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>处理在组件级别的对象属性，而模板策略可以用于约束解决方案或项目级别的对象属性。 换而言之  
  
-   在实现方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>以确定中显示的内容**属性**为特定对象的窗口  
  
-   使用模板的解决方案和项目级别决定中显示的内容**属性**以前指定的对象的窗口  
  
 使用模板策略来有选择地限制中的特定属性**属性**窗口具有指定类型的项目项时选择中**解决方案资源管理器**将是有益的所有成员开发团队在项目中工作。 例如，使用模板的策略，可以设置所有的连接字符串信息在数据库中你的开发人员，请将连接字符串为只读。 以这种方式，你可以提供一种简单的方法，以确保每个开发人员使用正确的路径进行数据访问。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [扩展属性](../../extensibility/internals/extending-properties.md)