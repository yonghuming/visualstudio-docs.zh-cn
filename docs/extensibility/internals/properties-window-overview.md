---
title: "属性窗口概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 11
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1ec1a650c72fbd181d176aea84b228c9973ad526
ms.lasthandoff: 02/22/2017

---
# <a name="properties-window-overview"></a>属性窗口概述
**属性**窗口用于显示在 windows 中提供的两个主要类型中选择的对象的属性[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE)。 Windows 这两种类型是︰  
  
-   如解决方案资源管理器、 类视图和对象浏览器的工具窗口  
  
-   包含此类编辑器和设计器为窗体设计器、 XML 编辑器和 HTML 编辑器的文档窗口  
  
## <a name="using-the-properties-window"></a>使用属性窗口  
 **属性**窗口将显示一个或多个选定的项的属性。 如果选择了多个项，将显示所有选定对象的所有属性的交集。  
  
 中会显示在窗体设计窗口或 HTML 编辑器使用 COM + 元数据中所选对象相关联的事件**属性**窗口。 例如，您可以选择一个按钮，显示其关联的事件，如`OnClick`事件，可以将链接到该按钮。  
  
 中显示事件**属性**窗口主要用于绑定到代码的对象。 如果正在编辑不会不会有任何如何处理代码的文件格式，您将不会有任何事件。 中仅显示事件**属性**窗口时运行代码，并具有特定对象关联的某些事件之间的绑定。 此示例将激活该对象后执行的所选对象背后的代码。  
  
 下表列出了使用的主接口**属性**窗口。  
  
|接口名称|描述|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties></xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|提供的类别对列表**属性**窗口，并将每个属性映射到某个类别。|  
|[IDispatch 接口](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|公开对象的方法和属性添加到编程的工具和其他支持自动化应用程序。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder></xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|提供了名为的省略号 （...） 按钮*生成器*打开模式对话框窗口本身的对象实现。 在文本字段中的用户不方便地键入一个值时使用。 例如，它可能用于打开颜色选取器，用于确定为您的 RGB 值。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer></xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|提供用于更新中所示信息的对象的访问**属性**窗口。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>由实现 VSPackages 迁移为每个窗口，其中包含具有要显示的相关属性的可选择对象。</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo></xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|提供有关如方法的对象类型的一个接口和结构的字段的信息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|使 Vspackage 接收选择事件的通知并检索有关当前项目层次结构、 项、 元素值和命令 UI 上下文信息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect></xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|提供有权访问多个选择的环境。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing></xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|用于对显示在某些属性提供本地化的名称**属性**窗口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|通知已注册的 VSPackages 迁移到当前所选内容、 元素的值或命令 UI 上下文的更改。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|发送通知的环境中当前所选内容的更改，并提供对与新的所选内容相关的层次结构和项信息的访问。|  
  
 有关详细信息`IDispatch`，请参阅 MSDN 库。  
  
## <a name="see-also"></a>另请参阅  
 [将属性扩展](../../extensibility/internals/extending-properties.md)   
 [属性窗口字段和接口](../../extensibility/internals/properties-window-fields-and-interfaces.md)
