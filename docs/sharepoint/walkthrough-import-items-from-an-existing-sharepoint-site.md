---
title: "演练：从现有的 SharePoint 网站导入项"
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
  - "导入项 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 导入项"
ms.assetid: faac3309-88d7-4fb2-8392-feda07fc00e5
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 演练：从现有的 SharePoint 网站导入项
  本演练演示如何将项目从现有的 SharePoint 网站导入到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 项目中。  
  
 本演练将演示以下任务：  
  
-   通过添加自定义网站栏（也称作“字段”）来自定义 SharePoint 网站。  
  
-   将 SharePoint 网站导出到 .wsp 文件中。  
  
-   使用 .wsp 导入项目将 .wsp 文件导入到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 中。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   支持的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## 自定义 SharePoint 网站  
 对于此示例，您将通过以下方法创建并自定义一个 SharePoint 子网站：向该子网站中添加新的网站栏，并创建另一个子网站以供以后使用。  稍后，将第一个子网站导出到 .wsp 文件中，再使用 .wsp 导入项目将自定义网站栏导入到第二个子网站中。  
  
#### 创建并自定义 SharePoint 网站  
  
1.  使用 Web 浏览器打开一个 SharePoint 网站，如 http:\/\/*system name*\/SitePages\/Home.aspx。  
  
2.  通过打开**“网站操作”**菜单，从主 SharePoint 网站创建一个子网站，然后选择**“新建网站”**。  
  
3.  在网站的 **创建** 对话框中，选择 **空白网站** 类型。  
  
4.  在**“标题”**框中输入“网站栏测试 1”；在**“URL 名称”**框中输入“columntest1”；保留其他设置为其默认值，然后选择**“创建”**。  
  
5.  创建网站后，在浏览器中导航回主网站，即 http:\/\/*system name*\/SitePages\/Home.aspx。  
  
6.  再次通过打开**“网站操作”**菜单，从主 SharePoint 网站创建一个空白子网站，选择**“新建网站”**然后选择**“空白网站”**。  
  
7.  在**“标题”**框中输入“网站栏测试 2”；在**“URL 名称”**框中输入“columntest2”；保留其他设置为其默认值，然后选择**“创建”**按钮。  
  
8.  导航回第一个子网站，即 http:\/\/*SystemName*\/columntest1\/default.aspx。  
  
9. 在**“网站操作”**菜单，选择**“网站设置”**以显示“网站设置”页。  
  
10. 在**“库”**部分中，选择**“网站栏”**链接。  
  
11. 在**“网站栏库”**页顶部，选择**“创建”**按钮。  
  
12. 在 **列名**框中，输入"测试栏"，保留其他默认值，然后选择 **确定**。  
  
13. **“测试栏”**栏将显示在“网站栏库”中的“自定义栏”标题下。  
  
## 导出 SharePoint 网站  
 接下来，将获取 SharePoint 安装程序 \(.wsp\) 文件，该文件包含要导入到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 项目中的 SharePoint 项和元素。  如果还没有 .wsp 文件，则必须从现有的 SharePoint 网站创建一个这样的文件。  对于此示例，将默认的 SharePoint 网站导出到 .wsp 文件中。  
  
> [!IMPORTANT]  
>  如果您在执行以下过程时接收到运行时错误，则必须在具有对 SharePoint 网站的访问权的系统上执行该过程。  
  
#### 导出现有的 SharePoint 网站  
  
1.  在 SharePoint 站点中，选择**“网站操作”**选项卡上的**“网站设置”**以显示“网站设置”页。  
  
2.  在“网站设置”页的**“网站操作”**部分中，选择**“将网站另存为模板”**链接。  
  
3.  在**“文件名”**框中输入 ExampleSite，在**“模板名称”**框中输入“示例网站”。  
  
4.  对于此示例，将保留**“包括内容”**复选框为清除状态。  
  
     如果选中此框，则 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 会将所有列表和文档库及其内容都保存到 .wsp 文件中。  尽管这在某些情况下非常有用，但在此示例中不需要这样做。  
  
5.  成功完成操作时，选择**“用户解决方案库”**链接可查看 .wsp 文件。  
  
     若要以后查看“解决方案库”页，打开**“网站操作”**菜单，选择**“网站设置”**，再选择**“网站集管理”**部分中的**“转到首要网站设置”**链接，然后选择**“库”**部分中的**“解决方案”**链接。  
  
6.  在解决方案库中，选择 **ExampleSite** 链接。  
  
7.  在 **文件下载** 对话框中，选择 **保存** 按钮保存在本地文件系统中，默认情况下，在下载文件夹中。  
  
## 导入 .wsp 文件  
 现在有了一个包含要重用的项（自定义网站栏“测试栏”）的 .wsp 文件，就可以导入该 .wsp 文件以进行访问了。  
  
#### 导入 .wsp 文件  
  
1.  在菜单栏上的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]依次选择**“文件”**，**“新建”**，**“项目”**以显示**新建项目**对话框。  如果您的 IDE 设置为使用 Visual Basic 开发设置，请在菜单上选择“文件”“新建项目”。  
  
2.  展开**“Visual C\#”**或**“Visual Basic”**下的**“SharePoint”**节点，然后选择**“2010”**节点。  
  
3.  在**“模板”**窗格中选择**“导入 SharePoint 解决方案包”**，保留项目的名称为“WspImportProject1”，然后选择**“确定”**按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  
  
4.  在**“指定用于调试的站点和安全级别”**页上，为您先前创建的第二个 SharePoint 子站点输入 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]。  您将添加新的自定义字段项 http:\/\/*system name*\/columntest2，到该子网站。  
  
5.  在**“此 SharePoint 解决方案的信任级别是什么?”**部分，将所选内容保持为**“部署为沙盒解决方案”**。  
  
6.  在**“指定新项目源”**页上，浏览到系统上您先前保存 .wsp 文件的位置，然后选择**“下一步”**按钮。  
  
    > [!NOTE]  
    >  如果选择 **完成** 按钮，此页面在 .wsp 文件中的所有可用项将导入。  
  
7.  在**“选择要导入的项”**框中，清除列表中除**“测试栏”**外的所有复选框，然后选择**“完成”**按钮。  
  
     由于列表包含很多项，您可以使用键 Ctrl \+ A选择列表中的所有项，选择空格键清除所有复选框，然后只选择 **测试列** 项旁边的复选框。  
  
     完成导入操作后，将创建一个名为**“WspImportProject1”**的新项目，其中包含一个名为**“Fields”**的文件夹。  此文件夹中包含自定义网站栏**“测试栏”**及其定义文件 Elements.xml。  
  
## 部署项目  
 最后，将**“WspImportProject1”**部署到您先前创建的第二个 SharePoint 子网站，以查看自定义网站栏。  
  
#### 部署项目  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，选择 F5 键以部署和运行导入项目的 .wsp 。  
  
2.  在 SharePoint 网站上，打开 **网站操作** 菜单，然后选择 **站点设置** 以显示"网站设置"页。  
  
3.  在**“库”**部分中，选择**“网站栏”**链接。  
  
4.  向下滚动到**“自定义栏”**部分。  
  
     请注意，您从第一个 SharePoint 网站导入的自定义网站栏将显示在列表中。  
  
## 请参阅  
 [从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  