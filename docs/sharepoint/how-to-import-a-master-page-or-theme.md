---
title: "如何：导入母版页或主题 | Microsoft Docs"
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
helpviewer_keywords: 
  - "导入项 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 导入项"
ms.assetid: 8b446cca-2adb-457b-bbfd-891209290e80
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：导入母版页或主题
  您可以通过创建和使用母版页和主题为 SharePoint 站点上的页面提供一致的外观。  虽然 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 不为这些元素提供模板，但您可以在 SharePoint Designer 中创建这些模板，然后将它们导入到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中。  有关更多信息，请参见 Microsoft 网站上[生成块：页面和用户界面](http://go.microsoft.com/fwlink/?LinkID=182095)。  
  
### 导入母版页或主题  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中打开或创建一个 SharePoint 项目。  
  
     有关如何创建 SharePoint 项目的更多信息，请参见[SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在菜单栏上，依次选择**“项目”**、**“添加新项”**。  
  
3.  在“添加新项”对话框中，展开“SharePoint” 节点，然后选择“2010”节点。  
  
4.  在 SharePoint 模板列表中，选择 **模块** 模板，然后为模块指定名称。  
  
     模块包含文件（如母版页或主题文件）部署到 SharePoint 中的指定位置的容器。  
  
5.  在模块中，删除默认的名为 Sample.txt 的文件。  
  
6.  选择“模块”节点。  
  
7.  在菜单栏上，依次选择 **项目**，**添加现有项**，然后选择母版页或主题文件。  
  
     母版页文件具有 .master 扩展，而主题文件具有 .thmx 文件扩展名。  
  
8.  如果添加了母版页，请将其 **部署冲突解决方法** 模块的属性设置为 **自动**。  
  
    > [!NOTE]  
    >  如果该母版页的名称与标记为“默认母版页”或“自定义母版页”的现有母版页的名称相同，则可能会出现错误。  有关如何解决此问题的信息，请参见[演练：导入带有图像的自定义母版页和网站页](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md)。  
  
9. 在模块中，打开 Elements.xml。  
  
     您必须将 Elements.xml 文件更新为引用您已添加的母版页或主题。  
  
10. 对于母版页，将现有模块标记替换为以下标记。  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     对于主题，将现有模块标记替换为以下标记。  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     务必将占位符值替换为模块和母版页或主题的实际名称。  
  
     特性 `Type="GhostableInLibrary"` 指示将项目添加到内容数据库中，模块的 `Url` 特性指定在 SharePoint 内容数据库中存储文件的位置。  
  
11. 若要更改母版页的部署范围，请在 **解决方案资源管理器**中打开在功能设计器的功能文件，然后从 **范围** 列表中选择新的部署范围。  
  
     **“Web”**的值表示母版页仅适用于当前在项目中指定的网站。  **“网站”**的值表示母版页适用于当前网站集；这包括所有子网站和根网站。  其他值不适用。  
  
    > [!NOTE]  
    >  因为主题仅适用于网站集级别，所以建议不要将主题范围设置为**“网站”**以外的任何值。  如果子网站中使用了主题，则可能出现错误。  
  
12. 在菜单栏上，依次选择**“生成”**、**“部署解决方案”**。  
  
13. 若要验证文件是否部署正确，请打开 SharePoint 站点，选择 **网站操作** 菜单中，选择 **站点设置** 命令，然后选择 **母版页** 链接或 **主题** 链接。  
  
     母版页或主题列表和包含导入的母版页或主题。  
  
## 请参阅  
 [母版页](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [为 SharePoint 创建页](../sharepoint/creating-pages-for-sharepoint.md)   
 [使用模块包括解决方案中的文件](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  