---
title: "实现自定义类别和显示项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f03dbae8b320161705c50da06d605cfc335074cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-custom-categories-and-display-items"></a>实现自定义类别和显示项
VSPackage 可以提供控件的字体和颜色到其文本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]通过自定义类别和显示项的集成的开发环境 (IDE)。  
  
 自定义类别和显示项位于**字体和颜色**属性页。 若要打开**字体和颜色**属性页，请在**工具**菜单上，单击**选项**。 展开**环境**，然后单击**字体和颜色**。  
  
 当使用此机制，Vspackage 必须实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>接口和其关联的接口。  
  
 原则上，可以使用此机制来修改所有现有**显示项**和**类别**包含它们。 但是，它不应修改**文本 EditorCategory**或其**显示项**。 有关详细信息，请参阅[字体和颜色概述](../extensibility/font-and-color-overview.md)。  
  
 若要实现自定义**类别**或**显示项**，VSPackage 必须：  
  
-   创建或标识注册表中的类别。  
  
     IDE 实现**字体和颜色**属性页使用此信息来正确查询支持给定的类别中的服务。  
  
-   创建或标识注册表中 （可选） 的组。  
  
     它可能会有用定义组中，这表示两个或多个类别的并集。 如果定义一个组，则 IDE 将自动合并子类别，并将分发组内的显示项。  
  
-   实现 IDE 支持。  
  
-   处理字体和颜色的更改。  
  
 有关信息，请参阅[访问存储的字体和颜色设置](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
## <a name="to-create-or-identify-categories"></a>若要创建或标识类别  
  
-   构造一个特殊类型的类别下的注册表项 [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio 版本 >*\FontAndColors\\`<Category>`]  
  
     *\<类别 >*是类别的非本地化名称。  
  
-   填充具有两个值注册表：  
  
    |名称|类型|数据|描述|  
    |----------|----------|----------|-----------------|  
    |类别|REG_SZ|GUID|一个 GUID 创建以标识的类别。|  
    |Package|REG_SZ|GUID|支持类别 VSPackage 服务的 GUID。|  
  
 在注册表中指定的服务必须提供的一个实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>为相应的类别。  
  
## <a name="to-create-or-identify-groups"></a>若要创建或标识组  
  
-   构造一个特殊类型的类别下的注册表项 [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio 版本 >*\FontAndColors\\  *\<组 >*]  
  
     *\<组 >*是组的非本地化名称。  
  
-   填充具有两个值注册表：  
  
    |名称|类型|数据|描述|  
    |----------|----------|----------|-----------------|  
    |类别|REG_SZ|GUID|创建以标识组 GUID。|  
    |Package|REG_SZ|GUID|支持类别服务的 GUID。|  
  
 在注册表中指定的服务必须提供的一个实现`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`为相应的组。  
  
## <a name="to-implement-ide-support"></a>若要实现 IDE 支持  
  
-   实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>，其返回<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>接口或`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`接口为每个 IDE**类别**或组提供的 GUID。  
  
-   为每个**类别**它支持、 VSPackage 实现的单独实例<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>接口。  
  
-   方法通过实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>必须提供具有的 IDE:  
  
    -   列出的**显示项**中**类别。**  
  
    -   可本地化名称**显示项**。  
  
    -   显示的每个成员的信息**类别**。  
  
    > [!NOTE]
    >  每个**类别**必须包含至少一个**显示项**。  
  
-   IDE 使用`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`接口可定义的几个类别的联合。  
  
     其实现提供具有的 IDE:  
  
    -   一份**类别**构成给定的组。  
  
    -   实例的访问<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>支持每个**类别**组内。  
  
    -   可本地化的组名称。  
  
-   更新 IDE:  
  
     IDE 将信息缓存有关**字体和颜色**设置。 因此，在 IDE 的任何修改之后**字体和颜色**配置，则最好确保缓存是最新。  
  
 更新缓存通过<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>接口，并可以执行的全局或仅在所选的项目。  
  
## <a name="to-handle-font-and-color-changes"></a>若要处理字体和颜色更改  
 若要正确支持 VSPackage 显示的文本的着色，支持 VSPackage 的着色服务必须响应通过所做的用户启动更改**字体和颜色**属性页。 VSPackage 做到这一点：  
  
-   IDE 生成的事件处理通过实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>接口。  
  
     IDE 调用相应的方法后的用户修改**字体和颜色**页。 例如，它调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>方法如果选择新的字体。  
  
     - 或 -  
  
-   轮询更改 IDE。  
  
     这可以通过系统实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>接口。 主要用于支持持久性，尽管<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>方法可以用于获取的字体和颜色信息**显示项**。 有关详细信息，请参阅[访问存储的字体和颜色设置](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
    > [!NOTE]
    >  为了确保通过轮询获取的结果是否正确，可能会有用使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>接口来确定缓存刷新和更新是否需要在调用的检索方法之前<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>接口。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [获取字体和文本着色的颜色信息](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [访问存储的字体和颜色设置](../extensibility/accessing-stored-font-and-color-settings.md)   
 [如何： 访问的内置的字体和配色方案](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [字体和颜色概述](../extensibility/font-and-color-overview.md)