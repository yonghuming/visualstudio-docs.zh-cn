---
title: "演练： 创建基本网站定义项目 |Microsoft 文档"
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
ms.assetid: b0df5b0e-5fa0-43d8-a339-6d92f1276764
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9bea8fec27b0d53fb1cfe3405d39d271a93f5a8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>演练：创建基本网站定义项目
  本演练演示了如何创建基本网站定义包含与上它的某些控件的可视 Web 部件。 为清楚起见，你创建的可视 Web 部件有仅几个控件。 但是，你可以创建包括更多的功能的更复杂的 SharePoint 网站定义。  
  
 本演练演示了下列任务：  
  
-   通过创建站点定义[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]项目模板。  
  
-   通过使用 SharePoint 中的站点定义中创建 SharePoint 站点。  
  
-   将可视 Web 部件添加到解决方案。  
  
-   通过向其添加新的可视 Web 部件，自定义站点的 default.aspx 页。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   支持的 Microsoft Windows 和 SharePoint 版本。 有关详细信息，请参阅有关开发 SharePoint 解决方案的要求。  
  
-   Visual Studio。  
  
## <a name="creating-a-site-definition-solution"></a>创建网站定义解决方案  
 首先，创建中的站点定义项目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
#### <a name="to-create-a-site-definition-project"></a>若要创建网站定义项目  
  
1.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。 如果 IDE 设置为使用 Visual Basic 开发设置，在菜单栏上，选择**文件**，**新项目**。  
  
     此时将出现 “新建项目” 对话框。  
  
2.  展开**Visual C#**节点或**Visual Basic**节点，展开**SharePoint**节点，然后选择**2010年**节点。  
  
3.  在**模板**列表中，选择**SharePoint 2010 项目**模板。  
  
4.  在**名称**框中，输入**TestSiteDef**，然后选择**确定**按钮。  
  
     **SharePoint 自定义向导**显示。  
  
5.  上**指定用于调试的站点和安全性级别**页上，输入想要调试站点定义的 SharePoint 站点的 URL 或使用默认位置 (http://*系统名称*/)。  
  
6.  在**此 SharePoint 解决方案的信任级别是什么？**部分中，选择**部署为场解决方案**选项按钮。  
  
     站点定义的所有项目必须都部署为场解决方案。 有关沙盒解决方案与场解决方案的详细信息，请参阅[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  选择**完成**按钮。  
  
     项目将出现在**解决方案资源管理器**。  
  
8.  在**解决方案资源管理器**，选择项目节点，然后，在菜单栏上，选择**项目**，**添加新项**。  
  
9. 下**Visual C#**或**Visual Basic**，展开**SharePoint**节点，然后选择**2010年**节点。  
  
10. 在**模板**窗格中，选择**站点定义**模板，保留**名称**作为**SiteDefinition1**，然后选择**添加**按钮。  
  
## <a name="create-a-visual-web-part"></a>创建可视 Web 部件  
 接下来，创建要在站点定义的主页上显示的可视 Web 部件。  
  
#### <a name="to-create-a-visual-web-part"></a>若要创建的可视 Web 部件  
  
1.  在**解决方案资源管理器**，选择**显示所有文件**按钮。  
  
2.  选择**SiteDefinition1**项目节点，，然后，在菜单栏上，选择**项目**，**添加新项**。  
  
     “添加新项”对话框随即出现。  
  
3.  展开**Visual C#**节点或**Visual Basic**节点，展开**SharePoint**节点，然后选择**2010年**节点。  
  
4.  在模板列表中，选择**可视 Web 部件**模板，保留默认值将 VisualWebPart1，，然后选择**添加**按钮。  
  
     打开该 VisualWebPart1.ascx 文件。  
  
5.  VisualWebPart1.ascx 底部添加以下标记将三个控件添加到窗体： 一个文本框、 按钮和标签：  
  
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
  
6.  下 VisualWebPart1.ascx，打开 VisualWebPart1.ascx.cs 文件 (对于[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) 或 VisualWebPart1.ascx.vb (有关[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])，然后添加以下代码：  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     此代码将添加为 web 部件的按钮单击的功能。  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>将可视 Web 部件添加到默认 ASPX 页  
 接下来，将可视 Web 部件添加到站点定义的默认 ASPX 页。  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>将可视 Web 部件添加到默认 ASPX 页  
  
1.  打开 default.aspx 页上，，然后添加以下行下的`WebPartPages`标记：  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     此行将名称 MyWebPartControls 与 Web 部件，并且其代码相关联。 *Namespace*参数与匹配 VisualWebPart1.ascx 代码文件中使用的命名空间。  
  
2.  后`</asp:Content>`元素，替换整个`ContentPlaceHolderId="PlaceHolderMain"`部分和其内容替换为以下代码：  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     此代码将创建对前面创建的可视 Web 部件的引用。  
  
3.  在**解决方案资源管理器**，打开快捷菜单**SiteDefinition1**节点，然后选择**设为启动项目**。  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>部署并运行网站定义解决方案  
 接下来，将项目部署到 SharePoint，，然后运行该项目。  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>部署并运行网站定义  
  
-   在菜单栏上，选择**生成**，**部署 TestSiteDef**。  
  
-   选择 F5 键。  
  
     Visual Studio 编译代码、 添加了其功能，为 SharePoint 解决方案 (WSP) 文件，包的所有文件和将 WSP 文件部署到 SharePoint 服务器。 SharePoint 安装文件，然后，然后激活功能。  
  
## <a name="create-a-site-based-on-the-site-definition"></a>创建基于站点定义的网站  
 接下来，使用新的站点定义中创建一个站点。  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>若要创建一个站点使用站点定义  
  
1.  在 SharePoint 站点上，将显示新的 SharePoint 网站页。  
  
2.  在**标题和说明**部分中，输入**我的新站点**标题和站点的描述。  
  
3.  在**网站地址**部分中，输入**mynewsite**中**URL 名称**框。  
  
4.  在**模板**部分中，选择**SharePoint 自定义**选项卡。  
  
5.  在**选择模板**列表中，选择**SiteDefinition1**。  
  
6.  将其他设置保留为其默认值，然后依次**创建**按钮。  
  
     新的站点会显示。  
  
## <a name="test-the-new-site"></a>测试新的站点  
 接下来，测试新站点以验证是否其正常运行。  
  
#### <a name="to-test-the-new-site"></a>若要测试新站点  
  
-   在默认 ASPX 页上，输入一些文本，然后选择**更改标签文本**文本框旁边的按钮。  
  
     将文本显示在右侧的按钮上的标签。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 创建事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  