---
title: "将属性扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: fec1140bc90d494a0c611ed84786f364f17f6087
ms.lasthandoff: 02/22/2017

---
# <a name="extending-properties"></a>将属性扩展
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **属性**是 COM 和 COM + 组件的通用属性浏览器窗口，并支持所有[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]产品。 **属性**窗口只处理`ITypeInfo`键入信息和 COM + 元数据以列出在集成的开发环境 (IDE) 中的任何其他窗口中当前选定的对象的设计时属性。  
  
 **属性**窗口中，可以通过在键盘上按 F4 或选择打开**属性窗口**上**视图**菜单上，用来查看和编辑所选对象的独立于配置的、 设计时属性和事件。 解决方案和项目，与关联的依赖于配置的属性显示在[属性页](../../extensibility/internals/property-pages.md)。 有关详细信息，请参阅[NIB︰ 项目属性](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)，[管理配置选项](../../extensibility/internals/managing-configuration-options.md)，和[NIB︰ 项管理项目中](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0)。  
  
 ![属性窗口概述](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
“属性”窗口  
  
 本部分提供相关的各个区域的详细的信息**属性**窗口和必须实现的接口，并调用来填充窗口中。  
  
## <a name="in-this-section"></a>本节内容  
 [属性窗口概述](../../extensibility/internals/properties-window-overview.md)  
 说明用途的**属性**相对于工具窗口和文档窗口的窗口。  
  
 [模板策略和属性窗口](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 讨论如何将一个项目包含在企业级模板项目，以及如何该企业级模板项目可以强制执行策略。  
  
 [属性窗口字段和接口](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 说明来确定哪些信息显示在所选内容的基础**属性**窗口。  
  
 [属性窗口对象列表](../../extensibility/internals/properties-window-object-list.md)  
 描述的目的**属性**窗口对象列表中，描述如何，如果此列表中的不同对象触发的调用，环境会通知已选择一个新的对象。  
  
 [属性窗口的按钮︰](../../extensibility/internals/properties-window-buttons.md)  
 解释上显示的四种默认按钮的用途**属性**窗口的工具栏。  
  
 [显示属性网格](../../extensibility/internals/properties-display-grid.md)  
 介绍了其中的网格中找到的属性名称和属性值字段。  
  
 [宣布属性窗口选定内容跟踪](../../misc/announcing-property-window-selection-tracking.md)  
 描述跟踪所选内容**属性**窗口。  
  
 [隐藏具有子属性的属性](../../misc/hiding-properties-that-have-child-properties.md)  
 说明如何通过实现具有子属性的属性隐藏<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>  
  
 [提供自定义属性窗口](../../misc/providing-a-custom-properties-window.md)  
 详细介绍用于提供您自己的属性浏览器的步骤。  
  
 [从属性窗口中获取字段说明](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 介绍在何处可以找到显示与所选的属性字段相关的信息的说明区域。  
  
 [在“属性”窗口中更新属性值](../../misc/updating-property-values-in-the-properties-window.md)  
 提供演示两种方法要保留的分步说明**属性**窗口与属性值更改保持同步。  
  
## <a name="related-sections"></a>相关章节  
 [项目类型](../../extensibility/internals/project-types.md)  
 探讨如何构建块的形式的项目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
 [编译和生成](../../ide/compiling-and-building-in-visual-studio.md)  
 介绍如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]进行连续测试和调试应用程序，在您生成应用的平台。  
  
 [HTML 文档属性，属性窗口](http://msdn.microsoft.com/Library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 说明如何编辑 HTML 文档直接从属性窗口中，并提供一个表详细列出在属性窗口中的 HTML 文档中的字段。  
  
 [IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 描述`IDispatch`接口，最初旨在支持自动化，提供一个用于访问和检索信息的方法和对象的属性的后期绑定机制。  
  
 [NIB︰ 简介动态属性 (Visual Studio)](http://msdn.microsoft.com/en-us/f5102027-1431-4195-ae40-9b991de46d3a)  
 概述使您可以配置您的应用程序，以使属性值存储在外部配置文件而不是应用程序的已编译代码的动态属性。  
  
 [NIB︰ 作为容器的项目](http://msdn.microsoft.com/en-us/87d40f63-f487-4767-8963-64beec27ba1b)  
 描述在一个解决方案，可以进行逻辑管理、 生成和调试构成应用程序的各个项的容器的项目角色。  
  
 [NIB︰ 项目属性](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 描述如何项目管理，你可以将应用于整个项目的控件属性和也仅限于特定生成配置的项目的属性的设置。  
  
 [解决方案和项目](../../ide/solutions-and-projects-in-visual-studio.md)  
 说明如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]如引用、 数据连接、 文件夹和文件所需的开发工作通过解决方案和项目项可有效地管理。  
  
 [扩展 Visual Studio 的其他部分](../../extensibility/extending-other-parts-of-visual-studio.md)  
 说明如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]服务，以创建匹配的其余部分的 UI 元素[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。
