---
title: "如何： 导入母版页或主题 |Microsoft 文档"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
ms.assetid: 8b446cca-2adb-457b-bbfd-891209290e80
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de361711234404e8b83e28aa1875b3549039bce0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-import-a-master-page-or-theme"></a>如何：导入母版页或主题
  你可以通过为提供页你 SharePoint 站点上一致的外观创建和使用母版页和主题。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]不提供模板对这些元素，但是，你可在 SharePoint Designer 中创建它们，然后将其导入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 有关详细信息，请参阅[构建基块： 页和用户界面](http://go.microsoft.com/fwlink/?LinkID=182095)Microsoft 网站上。  
  
### <a name="to-import-a-master-page-or-theme"></a>导入母版页或主题  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，创建或打开 SharePoint 项目。  
  
     有关如何创建一个 SharePoint 项目的信息，请参阅[SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在菜单栏上，选择**项目**，**添加新项**。  
  
3.  在**添加新项**对话框框中，展开**SharePoint**节点，然后选择**2010年**节点。  
  
4.  在 SharePoint 模板列表中，选择**模块**模板，然后指定该模块的名称。  
  
     模块包含用于部署到 SharePoint 中指定的位置的文件 （例如，母版页或主题文件）。  
  
5.  在模块中，删除默认文件中，名为 Sample.txt。  
  
6.  选择模块节点。  
  
7.  在菜单栏上，选择**项目**，**添加现有项**，，然后选择主页面或主题文件。  
  
     母版页文件扩展名为.master，并且主题文件具有.thmx 扩展名。  
  
8.  如果你添加母板页，更改其**部署冲突解决方法**将设置为**自动**中模块的属性。  
  
    > [!NOTE]  
    >  如果主页面的名称的现有的主页面，则标记为默认母版页或自定义母版页的名称相同，则会出现错误。 有关如何解决此问题的信息，请参阅[演练： 导入自定义母版页和网站页与图像](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md)。  
  
9. 在模块中，打开 Elements.xml。  
  
     你必须更新 Elements.xml 文件，以引用母版页或你添加的主题。  
  
10. 为母版页，替换为以下标记的现有模块标记。  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     对于主题，将现有的模块标记替换为以下标记。  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     请确保将占位符值替换为模块的母版页或主题的实际名称。  
  
     该属性`Type="GhostableInLibrary"`指示该项添加到内容数据库和`Url`的模块的属性指定在何处 SharePoint 内容数据库中存储文件。  
  
11. 若要更改在母版页，部署范围**解决方案资源管理器**，在功能设计器中，打开功能文件，然后选择新的部署作用域从**作用域**列表。  
  
     值为**Web**意味着主控页仅适用于当前项目中指定的网站。 值为**站点**意味着母版页到当前站点集合，其中包括所有子站点和根 web 应用。 其他值不会应用。  
  
    > [!NOTE]  
    >  主题仅适用于站点集合级别，因为我们建议你不要设置主题的作用域到的任何内容以外**站点**。 如果在子站点中使用主题，则可能发生错误。  
  
12. 在菜单栏上，选择**生成**，**部署解决方案**。  
  
13. 若要验证是否已正确部署文件，打开 SharePoint 站点中，选择**站点操作**菜单上，选择**站点设置**命令时，，然后选择**母版页**链接或**主题**链接。  
  
     母版页或主题的列表，其中包含母版页或导入的主题。  
  
## <a name="see-also"></a>另请参阅  
 [母版页](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [为 SharePoint 创建页](../sharepoint/creating-pages-for-sharepoint.md)   
 [使用模块包括解决方案中的文件](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  