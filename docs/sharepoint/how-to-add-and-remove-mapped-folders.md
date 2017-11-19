---
title: "如何： 添加和移除映射的文件夹 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
ms.assetid: 115c8b00-7d4c-4fbe-b42c-e82dca944504
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e54c4f4d95e5f8c23e6768ba3ebd09ef663fee1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-and-remove-mapped-folders"></a>如何：添加和移除映射文件夹
  某些常用的文件夹在 SharePoint 中，如图像和布局，深度嵌套的文件层次结构中。 你可以将这些文件夹映射到 SharePoint 项目，以便更轻松地访问它们。 映射的文件夹是 SharePoint 项目中的 SharePoint 服务器安装的文件的物理位置相对应的文件夹。  
  
 在部署 SharePoint 应用程序时，映射的文件夹和所有子文件夹通过解决方案包 (.wsp) 复制到服务器上的内容在运行 SharePoint 的 SharePoint 文件夹树中的指定位置。 此位置由**部署位置**为映射的文件夹设置的属性。 映射的文件夹中的任何子文件夹都与之相关**部署位置**的映射的文件夹。 请注意，**部署位置**属性，不是名称的映射的文件夹，请确定项的部署位置。  
  
 通过在菜单栏或快捷菜单上的命令用于项目，可以将映射的文件夹添加到项目。 你可以使用**添加 SharePoint"映像"映射文件夹**和**添加 SharePoint"布局"文件夹**命令以将这些文件名添加映射最常使用的文件夹。 你可以通过将任何其他可用的 SharePoint 文件夹映射到你的项目**添加 SharePoint 映射文件夹**命令的快捷菜单上，然后指定在文件夹**添加 SharePoint 映射文件夹**对话框。  
  
## <a name="adding-mapped-folders-to-a-project"></a>将映射的文件夹添加到项目  
 以下过程描述如何将两个映射的文件夹添加到可视 web 部件项目。 若要开始，你可以创建可视 web 部件项目。  
  
#### <a name="to-add-mapped-folders-to-a-project"></a>若要将映射的文件夹添加到项目  
  
1.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
2.  在**新项目**对话框框中，展开**Visual Basic**或**Visual C#**节点，展开**Office/SharePoint**节点，然后选择**SharePoint 解决方案**节点。  
  
3.  在项目模板列表中，选择**SharePoint 2013 可视 Web 部件**模板。  
  
4.  在**名称**框中，输入**TestProject1**，然后选择**确定**按钮。  
  
5.  在**SharePoint 自定义向导**，选择**完成**按钮以保留默认设置。  
  
6.  在**解决方案资源管理器**，选择项目节点，然后，在菜单栏上，选择**项目**，**添加 SharePoint"映像"映射文件夹**。  
  
     名为的文件夹**映像**将出现在你的项目，并包含名为 TestProject1 的子文件夹。 此映射的文件夹将包含可视 web 部件项目的映像。  
  
7.  在**解决方案资源管理器**，选择项目节点，然后，在菜单栏上，选择**项目**，**添加 SharePoint 映射文件夹**以显示**添加SharePoint 映射文件夹**对话框。  
  
8.  在树视图中可用于映射的文件夹中，选择**资源**文件夹，然后选择**确定**按钮。  
  
     名为的文件夹**资源**出现在你的项目。 此文件夹可以用于存储字符串资源文件等文件的项。 子文件夹可能很有用用于组织的内容映射的文件夹，但不是会自动在创建时通过使用添加映射的文件夹**添加 SharePoint 映射文件夹**命令。 若要添加子文件夹，选择**资源**文件夹，然后在菜单栏上，选择**项目**，**新文件夹**。  
  
## <a name="changing-the-deployment-location-of-a-mapped-folder"></a>更改映射的文件夹的部署位置  
 默认情况下，映射的文件夹添加到令牌 {SharePointRoot} 表示的 SharePoint 根安装路径相对的特定位置中。 但是，您可以通过更改来更改此位置**部署位置**映射的文件夹的属性。 每个映射的文件夹都具有其自己**部署位置**属性。  
  
#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>若要更改映射的文件夹的部署位置  
  
1.  在前面创建的项目，选择映射的文件夹。  
  
2.  在**属性**窗口中，选择省略号 (![ASP.NET 移动设计器椭圆](../sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器椭圆")) 上的按钮**部署位置**属性。  
  
3.  在**添加 SharePoint 映射文件夹**对话框中，浏览到要点的映射的文件夹的文件夹。  
  
4.  选择的节点，然后选择**确定**按钮。  
  
## <a name="renaming-or-removing-mapped-folders"></a>重命名或移除映射的文件夹  
  
#### <a name="to-rename-or-remove-a-mapped-folder"></a>若要重命名或移除映射的文件夹  
  
1.  在前面创建的项目，选择映射的文件夹。  
  
2.  若要重命名的映射的文件夹，打开其快捷菜单，选择**重命名**，输入新的名称，然后选择 Enter 键。  
  
     作为替代方法，你可以选择你想要重命名，打开映射的文件夹**属性**窗口中，然后将的值设置**文件夹名称**为新的名称的属性。  
  
3.  若要从项目中移除映射的文件夹，打开其快捷菜单，选择**删除**，然后选择**确定**按钮在对话框中确认该删除。  
  
## <a name="see-also"></a>另请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  