---
title: "属性窗口概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0094accca0feb026fca02c78bf6e86fe512ce981
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="properties-window-overview"></a>属性窗口概述
**属性**窗口用于显示在 windows 中提供两种主要类型中选择的对象的属性[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE)。 Windows 这两种类型是：  
  
-   如解决方案资源管理器、 类视图和对象浏览器的工具窗口  
  
-   包含此类编辑器和窗体设计器、 XML 编辑器和 HTML 编辑器设计器的文档窗口  
  
## <a name="using-the-properties-window"></a>使用属性窗口  
 **属性**窗口将显示一个或多个选定的项的属性。 如果选择了多个项，将显示所有选定对象的所有属性的交集。  
  
 与窗体设计窗口或 HTML 编辑器使用 COM + 元数据内的所选对象相关的事件显示在**属性**窗口。 例如，你可以选择一个按钮，并显示其关联的事件，如`OnClick`事件，可链接到该按钮。  
  
 显示在事件**属性**窗口主要用于绑定到代码的对象。 如果你正在编辑不具有任何内容如何处理代码的文件格式，将不会有任何事件。 事件仅显示在**属性**窗口时运行代码和具有特定对象关联的某些事件之间的绑定。 此示例将在该对象将被激活时执行的所选对象背后的代码。  
  
 下表列出了使用的主接口**属性**窗口。  
  
|接口名称|描述|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|提供的类别对列表**属性**窗口，并将每个属性映射到类别。|  
|[IDispatch 接口](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)|公开对象的方法和为编程工具和其他应用程序支持自动化的属性。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|提供的省略号 （...） 按钮调用*生成器*打开模式对话框 windows 实现的对象本身。 在文本字段中用户无法轻松地键入一个值时使用。 例如，它可能用于打开颜色选取器，它为你确定的 RGB 值。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|提供用于更新中显示的信息的对象的访问权限**属性**窗口。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>是为每个窗口，其中包含要显示相关属性与可选择对象实现的 Vspackage。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|提供接口和结构的字段的信息 （例如方法） 的对象的类型。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|使 Vspackage 可以接收通知的选择事件，以及如何检索有关当前项目层次结构、 项、 元素值和命令 UI 上下文的信息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|提供有权访问多个选择的环境。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|用于提供对中显示某些属性的本地化的名称**属性**窗口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|通知当前所选内容，元素值或命令 UI 上下文发生更改的已注册的 Vspackage。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|发送通知的环境中当前所选内容的更改，并提供对与新的选择相关的层次结构和项信息的访问。|  
  
 有关详细信息`IDispatch`，请参阅 MSDN 库。  
  
## <a name="see-also"></a>另请参阅  
 [扩展属性](../../extensibility/internals/extending-properties.md)   
 [属性窗口字段和界面](../../extensibility/internals/properties-window-fields-and-interfaces.md)