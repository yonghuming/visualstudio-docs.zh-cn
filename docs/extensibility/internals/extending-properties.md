---
title: "将属性扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: abf254aa21be5ec4b7401e21afa5f9bcca00e011
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="extending-properties"></a>扩展属性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **属性**时段 COM 和 COM + 组件的通用的属性浏览器，并且支持所有[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]产品。 **属性**窗口配合`ITypeInfo`类型信息和 COM + 元数据以列出在集成的开发环境 (IDE) 中的任何其他窗口中的当前所选对象的设计时属性。  
  
 **属性**窗口中，可以通过在键盘上，按 F4 或选择打开**属性窗口**上**视图**菜单上，用来查看和编辑独立于配置的设计时属性和所选对象的事件。 解决方案和项目，与关联的依赖于配置的属性显示在[属性页](../../extensibility/internals/property-pages.md)。 有关详细信息，请参阅[NIB： 项目属性](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)，[管理配置选项](../../extensibility/internals/managing-configuration-options.md)，和[NIB： 项管理项目中](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0)。  
  
 ![属性窗口概述](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
“属性”窗口  
  
 本部分提供如何的单独的区域与关联的详细的信息**属性**窗口和必须实现的接口，并调用来填充窗口。  
  
## <a name="in-this-section"></a>本节内容  
 [属性窗口概述](../../extensibility/internals/properties-window-overview.md)  
 说明用途的**属性**相对于工具窗口和文档窗口的窗口。  
  
 [模板策略和属性窗口](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 讨论如何将项目包含在企业模板项目中，以及如何该企业级模板项目可以强制执行策略。  
  
 [属性窗口字段和界面](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 说明选择确定在显示的信息的基础**属性**窗口。  
  
 [属性窗口对象列表](../../extensibility/internals/properties-window-object-list.md)  
 描述的目的**属性**窗口对象列表中，描述如何操作，当此列表中的不同对象触发调用时，环境将得到通知，已选择新的对象。  
  
 [属性窗口按钮](../../extensibility/internals/properties-window-buttons.md)  
 说明用途的四个默认按钮上显示**属性**窗口工具栏。  
  
 [属性显示网格](../../extensibility/internals/properties-display-grid.md)  
 说明的属性名称和属性值字段找到在网格中。  
  
## <a name="related-sections"></a>相关章节  
 [项目类型](../../extensibility/internals/project-types.md)  
 作为构建基块讨论项目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
 [编译和生成](../../ide/compiling-and-building-in-visual-studio.md)  
 介绍如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]进行连续测试和调试应用程序，在你生成的平台。  
  
 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)  
 描述`IDispatch`接口，最初旨在支持自动化，提供了一个后期绑定机制来访问和检索有关方法和对象的属性的信息。  
  
 [管理应用程序设置 (.NET)](../../ide/managing-application-settings-dotnet.md)  
 提供允许你配置应用程序，以使属性值存储在外部配置文件而不是应用程序的已编译代码的应用程序设置概述。  
  
 [解决方案和项目](../../ide/solutions-and-projects-in-visual-studio.md)  
 说明如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]有效地管理引用、 数据连接、 文件夹和文件所需的开发工作解决方案和项目通过等项。  
  
 [扩展 Visual Studio 的其他部分](../../extensibility/extending-other-parts-of-visual-studio.md)  
 说明如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]服务来创建匹配的其余部分的 UI 元素[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。