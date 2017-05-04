---
title: "演练：创建基本网站定义项目 | Microsoft Docs"
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
  - "Visual Studio 中的 SharePoint 开发，网站定义"
  - "网站定义 [Visual Studio 中的 SharePoint 开发]"
ms.assetid: b0df5b0e-5fa0-43d8-a339-6d92f1276764
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# 演练：创建基本网站定义项目
  本演练演示如何创建包含一个可视 Web 部件（此部件上有一些控件）的基本网站定义。  为了清楚起见，创建的可视 Web 部件只具有几个控件。  不过，您可以创建包括更多功能的更复杂的 SharePoint 网站定义。  
  
 本演练将演示以下任务：  
  
-   使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 项目模板创建一个网站定义。  
  
-   使用 SharePoint 中的网站定义创建一个 SharePoint 网站。  
  
-   向解决方案中添加一个可视 Web 部件。  
  
-   对网站的 default.aspx 页进行自定义，在其中添加新的可视 Web 部件。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   支持的 Microsoft Windows 和 SharePoint 版本。  有关更多信息，请参见“开发 SharePoint 解决方案的要求”。  
  
-   Visual Studio。  
  
## 创建网站定义解决方案  
 首先，在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中创建网站定义项目。  
  
#### 创建网站定义项目  
  
1.  在菜单栏上，依次选择**“文件”**、**“新建”**、**“项目”**。  如果您的 IDE 设置为使用 Visual Basic 开发设置，请在菜单上选择“文件”“新建项目”。  
  
     此时将出现**“新建项目”**对话框。  
  
2.  展开 **Visual C\#** 节点或 **Visual Basic** 节点，展开 **SharePoint** 节点，然后选择 **2010** 节点。  
  
3.  在 **模板** 列表中，选择 **SharePoint 2010 项目** 模板。  
  
4.  在**“名称”**框中，输入TestSiteDef ，然后选择“确定”按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  
  
5.  在**“指定用于调试的网站和安全级别”**页上，输入要在其中调试网站定义的 SharePoint 网站的 URL，或者使用默认位置 \(http:\/\/*System Name*\/\)。  
  
6.  在“此 SharePoint 解决方案的信任级别是什么?”部分中，选中“部署为场解决方案”选项按钮。  
  
     所有网站定义项目都必须部署为场解决方案。  有关沙盒化解决方案与场解决方案的更多信息，请参见[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  选择**“完成”**按钮。  
  
     该项目将显示在**“解决方案资源管理器”**中。  
  
8.  在**“解决方案资源管理器”**中，选择项目节点，然后在菜单栏上选择**“项目”**，再选择**“添加新项”**。  
  
9. 展开**“Visual C\#”**或**“Visual Basic”**下的**“SharePoint”**节点，然后选择**“2010”**节点。  
  
10. 在 **模板** 窗格中，选择 **网站定义** 模板，将 **名称** 设置为 **SiteDefinition1**，然后选择 **添加** 按钮。  
  
## 创建可视 Web 部件  
 接下来，创建一个可视 Web 部件以显示在网站定义的主页上。  
  
#### 创建可视 Web 部件  
  
1.  在**“解决方案资源管理器”**中，选择**“显示所有文件”**按钮。  
  
2.  选择 **SiteDefinition1** 项目节点，然后，菜单栏上，选择 **项目**，选择 **添加新项**。  
  
     **“添加新项”**对话框随即出现。  
  
3.  展开 **Visual C\#** 节点或 **Visual Basic** 节点，展开 **SharePoint** 节点，然后选择 **2010** 节点。  
  
4.  在模板列表中，选择 **可视 Web 部件** 模板，保留默认名称 VisualWebPart1，然后选择 **添加** 按钮。  
  
     VisualWebPart1.ascx 文件打开。  
  
5.  将以下标记添加到 VisualWebPart1.ascx 底部，从而将三个控件（文本框、按钮和标签）添加到窗体中：  
  
    ```  
    <table>  
      <tr>  
        <td>  
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>  
        </td>  
        <td>  
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>  
        </td>  
        <td>  
          <asp:Label runat="server" ID="lblName"></asp:Label>  
        </td>  
      </tr>  
    </table>  
    ```  
  
6.  位于 VisualWebPart1.ascx 之下，打开 VisualWebPart1.ascx.cs文件（针对 [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]）或 VisualWebPart1.ascx.vb（针对 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]），然后添加以下代码：  
  
     [!code-csharp[SP_SimpleSiteDef#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_simplesitedef/cs/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_SimpleSiteDef#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_simplesitedef/vb/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
     此代码将添加 Web 部件的按钮单击功能。  
  
## 向默认 ASPX 页中添加可视 Web 部件  
 接下来，将可视 Web 部件添加到网站定义的默认 ASPX 页中。  
  
#### 向默认 ASPX 页中添加可视 Web 部件  
  
1.  打开 default.aspx 页，然后将以下行添加到 `WebPartPages` 标记下面。  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     此行代码将名称 MyWebPartControls 与 Web 部件及其代码相关联。  *Namespace* 参数与在 VisualWebPart1.ascx 代码文件中的命名空间匹配。  
  
2.  在 `</asp:Content>` 元素后面，用以下代码替换整个 `ContentPlaceHolderId="PlaceHolderMain"` 部分及其内容。  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     此代码将创建对您先前创建的可视 Web 部件的引用。  
  
3.  在**“解决方案资源管理器”**中，打开**SiteDefinition1**节点的快捷菜单，然后选择**“设置为启动项”**。  
  
## 部署并运行网站定义解决方案  
 接下来，将项目部署到 SharePoint，然后运行项目。  
  
#### 部署并运行网站定义  
  
-   在菜单栏上，选择**“生成”**，再选择**部署TestSiteDef**。  
  
-   选择 F5 键。  
  
     Visual Studio 将编译代码、添加代码功能、将所有文件打包到SharePoint 解决方案 （WSP） 文件中，并将 WSP 文件部署到 SharePoint Server。  然后，SharePoint 将安装相关文件并激活相关功能。  
  
## 基于网站定义创建网站  
 接下来，将使用新网站定义来创建网站。  
  
#### 使用网站定义创建网站  
  
1.  在 SharePoint 网站上，将出现“新建 SharePoint 网站”页。  
  
2.  在**“标题和说明”**部分中，输入“我的新网站”作为标题并输入有关网站的说明。  
  
3.  在**“网站地址”**部分中，将 mynewsite 输入到**“URL 名称”**框中。  
  
4.  在 **模板** 部分中，选择 **SharePoint 自定义** 选项卡。  
  
5.  在 **选择模板** 列表中，选择 **SiteDefinition1**。  
  
6.  将其他设置保留为其默认值，然后选择**“创建”**按钮。  
  
     新网站将出现。  
  
## 测试新网站  
 接下来，将测试新网站以确认它能够正常工作。  
  
#### 测试新网站  
  
-   在默认 ASPX 页中，输入一些文本，然后选择该文本框旁边的**改变标签文本**按钮。  
  
     相应文本将显示在按钮右侧的标签中。  
  
## 请参阅  
 [如何：创建事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  