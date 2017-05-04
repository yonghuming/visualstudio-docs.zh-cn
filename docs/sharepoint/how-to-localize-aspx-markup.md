---
title: "如何：本地化 ASPX 标记 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "本地化 XML [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 本地化"
ms.assetid: 9559a1d1-6558-4c24-a51e-c6ee79432778
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：本地化 ASPX 标记
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] \(.aspx\) 页通常使用硬编码的字符串值。  若要本地化这些字符串，请将它们替换为引用本地化资源的表达式。  
  
## 本地化 ASPX 标记  
  
#### 本地化 ASPX 标记  
  
1.  添加单独的资源文件：一个用于默认语言，另一个用于每种本地化语言。  
  
     如果要仅本地化标记而不本地化代码，请添加“全局资源文件”项目项。  如果要本地化代码和标记，请添加“资源文件”项目项。  
  
    1.  若要添加全局资源文件，在 **解决方案资源管理器**中，打开 SharePoint 项目项的快捷菜单，再选择 **添加**，**新建项**。  在 **2010** 的 SharePoint 节点下，选择 **全局资源文件** 模板。  
  
    2.  若要添加资源文件，在 **解决方案资源管理器**中，打开 SharePoint 项目项的快捷菜单，再选择 **添加**，**新建项**。  在**Visual Basic** 或 **Visual C\#**节点下，选择 **资源文件** 模板。  
  
    > [!NOTE]  
    >  确保将资源文件添加到 SharePoint 项目项以启用“部署类型”属性。  本过程后面需要此属性。  如果您的解决方案中没有 SharePoint 项目项，则可添加一个空白 SharePoint 项目，并删除其默认 Elements.xml 文件。  
  
2.  为默认语言资源文件指定一个附带有 .resx 扩展名的所选名称，例如 MyAppResources.resx。  为每个本地化资源文件使用同一基名称，但需要添加区域性[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]。  例如，将德语本地化资源命名为 MyAppResources.de\-DE.resx。  
  
3.  将每个资源文件的**“部署类型”**属性的值更改为**“AppGlobalResource”**，使每个文件都部署到服务器的 App\_GlobalResources 文件夹。  
  
4.  如果要使用资源来本地化除 ASPX 标记外的代码，请将每个文件的**“生成操作”**属性的值设置保留为**“嵌入的资源”**。  如果您仅使用资源文件来本地化标记，则可以选择将文件的该属性值更改为**“内容”**。  有关详细信息，请参阅[本地化 SharePoint 解决方案](../sharepoint/localizing-sharepoint-solutions.md)。  
  
5.  打开每个资源文件并添加本地化的字符串（在每个文件中使用相同的字符串 ID）。  
  
6.  在 ASPX 页或控件的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 标记中，将硬编码的字符串替换为使用以下格式的值：  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     例如，若要本地化应用程序页上某个标签控件的文本，您将更改：  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     设置为  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  选择 F5 键生成并运行项目。  
  
8.  在 SharePoint 中，更改默认显示语言。  
  
     本地化的字符串将出现在应用程序中。  若要显示本地化资源，SharePoint 服务器必须安装了与该资源文件的区域特点相匹配的语言包。  
  
## 请参阅  
 [本地化 SharePoint 解决方案](../sharepoint/localizing-sharepoint-solutions.md)   
 [如何：本地化功能](../sharepoint/how-to-localize-a-feature.md)   
 [如何：添加资源文件](../sharepoint/how-to-add-a-resource-file.md)   
 [如何：本地化代码](../sharepoint/how-to-localize-code.md)  
  
  