---
title: "如何： 本地化 ASPX 标记 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 9559a1d1-6558-4c24-a51e-c6ee79432778
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39d72d4807f61adcab1321b6471c2bea31f048a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-localize-aspx-markup"></a>如何：本地化 ASPX 标记
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)](.aspx) 页通常使用硬编码的字符串值。 若要本地化这些字符串，将其替换引用本地化的资源的表达式。  
  
## <a name="localizing-aspx-markup"></a>本地化 ASPX 标记  
  
#### <a name="to-localize-aspx-markup"></a>若要本地化 ASPX 标记  
  
1.  添加单独的资源文件： 一个用于默认语言，另一个用于每个本地化语言。  
  
     如果本地化仅标记而非代码时，添加全局资源文件的报表项。 如果你要本地化代码和标记，添加资源文件的报表项。  
  
    1.  若要添加全局资源文件，在**解决方案资源管理器**，打开 SharePoint 项目项的快捷菜单，然后选择**添加**，**新项**。 在 SharePoint **2010年**节点，选择**全局资源文件**模板。  
  
    2.  若要添加资源文件，在**解决方案资源管理器**，打开 SharePoint 项目项的快捷菜单，然后选择**添加**，**新项**。 下**Visual Basic**或**Visual C#**节点，选择**资源文件**模板。  
  
    > [!NOTE]  
    >  请确保将资源文件添加到 SharePoint 项目项以启用部署类型属性。 稍后在此过程需要使用此属性。 如果你的解决方案不具有 SharePoint 项目项，你可以添加空 SharePoint 项目和删除其默认 Elements.xml 文件。  
  
2.  为默认语言资源文件提供一个带.resx 扩展名，例如 MyAppResources.resx 追加你选择的名称。 对每个本地化资源文件使用同一基名称，但添加区域性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]。 例如，名称 MyAppResources.de DE.resx 德语本地化的资源。  
  
3.  更改的值**部署类型**到每个资源文件的属性**AppGlobalResource**以使其部署到服务器的 App_GlobalResources 文件夹。  
  
4.  如果你使用的资源来本地化除 ASPX 标记之外的代码，将的值保留**生成操作**作为每个文件的属性**嵌入的资源**。 如果将资源文件来本地化标记，可以根据需要更改的文件的属性值**内容**。 有关详细信息，请参阅[本地化 SharePoint 解决方案](../sharepoint/localizing-sharepoint-solutions.md)。  
  
5.  打开每个资源文件并添加每个文件中使用的相同字符串 Id 的本地化的字符串。  
  
6.  在[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]ASPX 页或控件的标记将硬编码字符串替换为使用以下格式的值：  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     例如，若要本地化的应用程序页上的标签控件的文本，请更改：  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     更改为  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  选择 F5 生成并运行应用程序。  
  
8.  在 SharePoint 中，更改默认的显示语言。  
  
     应用程序中出现的本地化的字符串。 若要显示本地化的资源，SharePoint 服务器必须具有匹配资源文件的区域性的语言包安装。  
  
## <a name="see-also"></a>另请参阅  
 [本地化 SharePoint 解决方案](../sharepoint/localizing-sharepoint-solutions.md)   
 [如何： 本地化功能](../sharepoint/how-to-localize-a-feature.md)   
 [如何： 将一个资源文件](../sharepoint/how-to-add-a-resource-file.md)   
 [如何：本地化代码](../sharepoint/how-to-localize-code.md)  
  
  