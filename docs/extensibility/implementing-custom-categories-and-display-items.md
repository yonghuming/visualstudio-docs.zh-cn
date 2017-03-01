---
title: "实现自定义类别和显示项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 25
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
ms.openlocfilehash: d117676515988f1bf7f73ed1e9786c7c2919135e
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-custom-categories-and-display-items"></a>实现自定义类别和显示项
控件的字体和为其文本的颜色，可以提供 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]通过自定义类别和显示项的集成的开发环境 (IDE)。  
  
 自定义类别和显示项位于**字体和颜色**属性页。 若要打开**字体和颜色**属性页上，在**工具**菜单上，单击**选项**。 展开**环境**，然后单击**字体和颜色**。  
  
 当使用此机制，必须实现 Vspackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>接口和其关联的接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
 从原理上讲，这种机制可用来修改所有现有**显示项**和**类别**包含它们。 但是，应该不会使用它来修改**文本 EditorCategory**或其**显示项**。 有关详细信息，请参阅[字体和颜色概述](../extensibility/font-and-color-overview.md)。  
  
 若要实现自定义**类别**或**显示项**，VSPackage 必须︰  
  
-   创建或标识注册表中的类别。  
  
     IDE 的实现**字体和颜色**属性页使用此信息来正确地查询支持给定的类别中的服务。  
  
-   创建或标识组 （可选） 在注册表中。  
  
     可能有必要定义一个组，表示两个或多个类别的并集。 如果定义一个组，则 IDE 将自动合并子类别，并分发显示该组中的项目。  
  
-   实现 IDE 的支持。  
  
-   处理字体和颜色的更改。  
  
 有关信息，请参阅[访问存储的字体和颜色设置](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
## <a name="to-create-or-identify-categories"></a>若要创建或标识类别  
  
-   构造一个特殊类型的类别下的注册表项 [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio 版本&1;>*\FontAndColors\\`<Category>`]  
  
     *\<类别&1;>*是该类别的非本地化名称。  
  
-   填充注册表具有两个值︰  
  
    |名称|类型|数据|说明|  
    |----------|----------|----------|-----------------|  
    |类别|REG_SZ|GUID|一个 GUID 创建来标识该类别。|  
    |包|REG_SZ|GUID|支持类别的 VSPackage 服务的 GUID。|  
  
 在注册表中指定的服务必须提供实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>为相应的类别。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
## <a name="to-create-or-identify-groups"></a>若要创建或标识一组  
  
-   构造一个特殊类型的类别下的注册表项 [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio 版本&1;>*\FontAndColors\\*\<组&1;>*]  
  
     *\<组&1;>*是组的非本地化名称。  
  
-   填充注册表具有两个值︰  
  
    |名称|类型|数据|说明|  
    |----------|----------|----------|-----------------|  
    |类别|REG_SZ|GUID|创建以确定组 GUID。|  
    |包|REG_SZ|GUID|支持类别的服务的 GUID。|  
  
 在注册表中指定的服务必须提供实现`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`为相应的组。  
  
## <a name="to-implement-ide-support"></a>若要实现 IDE 支持  
  
-   实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>，它返回<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>接口或`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`接口为每个 IDE**类别**或组提供的 GUID。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>  
  
-   对于每个**类别**它支持、 VSPackage 实现的单独实例<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
-   通过实现方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>必须提供具有的 IDE:</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
    -   列出的**显示项**中**类别。**  
  
    -   可本地化名称**显示项**。  
  
    -   显示的每个成员的信息**类别**。  
  
    > [!NOTE]
    >  每个**类别**必须包含至少一个**显示项**。  
  
-   IDE 将使用`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`接口来定义几个类别的并集。  
  
     其实现提供了 IDE:  
  
    -   一份**类别**组成一组给定。  
  
    -   实例的访问<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>支持每个**类别**组内。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
    -   可本地化的组名称。  
  
-   正在更新 IDE:  
  
     IDE 将信息缓存有关**字体和颜色**设置。 因此，在 IDE 的任何修改后**字体和颜色**配置，则最好确保缓存是最新。  
  
 更新缓存通过<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>接口，并在可执行全局或仅在所选的项。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
## <a name="to-handle-font-and-color-changes"></a>为句柄字体和颜色更改  
 若要正确地支持 VSPackage 显示的文本的颜色设置，支持 VSPackage 的颜色设置服务必须响应通过所做的用户启动更改**字体和颜色**属性页。 VSPackage 实现此目的︰  
  
-   IDE 生成的事件处理通过实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
     IDE 将调用相应方法按照用户修改的**字体和颜色**页。 例如，它调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>方法，如果选择新的字体。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>  
  
     - 或 -  
  
-   轮询更改 IDE。  
  
     这可以通过系统实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 主要用于支持的持久性，尽管<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>方法可以用于获取字体和颜色信息**显示项**。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 有关详细信息，请参阅[访问存储的字体和颜色设置](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
    > [!NOTE]
    >  若要确保通过轮询中获得的结果是否正确，可能需要使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>接口，以确定是否缓存刷新和更新之前调用的检索方法所需<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A></xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [获取字体和文本着色的颜色信息](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [访问存储的字体和颜色设置](../extensibility/accessing-stored-font-and-color-settings.md)   
 [如何︰ 访问内置字体和配色方案](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [字体和颜色概述](../extensibility/font-and-color-overview.md)
