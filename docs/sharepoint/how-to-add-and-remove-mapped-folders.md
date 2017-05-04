---
title: "如何：添加和移除映射文件夹 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.MappedFolder"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "映射文件夹 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 映射文件夹"
ms.assetid: 115c8b00-7d4c-4fbe-b42c-e82dca944504
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 如何：添加和移除映射文件夹
  SharePoint中的一些常用文件夹（如 Images 和 Layouts 文件夹）深深地嵌套在文件层次结构中。  您可以将这些文件夹映射到 SharePoint 项目中，这样便能够更轻松地访问它们。  映射文件夹是 SharePoint 项目中的文件夹，这些文件夹与 SharePoint Server 安装中的文件的物理位置相对应。  
  
 在部署 SharePoint 应用程序时，解决方案包 \(.wsp\) 会将映射文件夹及其所有子文件夹的内容复制到运行 SharePoint 的 Server 上的 SharePoint文件夹树中的指定位置。  此位置由为映射文件夹设置的 **Deployment Location** 属性决定。  映射文件夹中的任何子文件夹都与映射文件夹的 **Deployment Location** 相关。  请注意，只有 **Deployment Location** 属性才能确定项的部署位置，映射文件夹的名称不能做到这一点。  
  
 您可以使用项目的菜单栏或快捷菜单上的命令将映射文件夹添加到项目中。  您可以使用 **将 SharePoint 的“图像”映射文件夹** 和 **将 SharePoint 的“Layouts”文件夹** 命令添加到经常使用的映射的文件夹。  您可以映射其他可用 SharePoint 文件夹的任何项目到您的工程中，使用 **添加 SharePoint 映射文件夹** 命令的快捷菜单，然后在**添加 SharePoint 映射文件夹** 对话框中指定文件夹。  
  
## 向项目中添加映射文件夹  
 下面的过程描述如何将两个映射文件夹添加到一个视觉对象Web部件项目中。  首先，创建可视 Web 部件项目  
  
#### 向项目中添加映射文件夹  
  
1.  在菜单栏上，依次选择**“文件”**、**“新建”**、**“项目”**。  
  
2.  在“新建项目”对话框中，展开“Visual Basic”或“Visual C\#”结点，展开“Office\/SharePoint”结点，然后选择“SharePoint 解决方案”结点。  
  
3.  在项目模板列表中，选择 **SharePoint 2013 Visual Web 部件** 模板。  
  
4.  在**“名称”**框中，输入“TestProject1”，然后选择“确定”按钮。  
  
5.  在 **SharePoint 自定义向导**中，选择 **完成** 按钮保留默认设置。  
  
6.  在**“解决方案资源管理器”**中，选择项目结点，然后在菜单栏上选择**“项目”**，**“添加SharePoint ‘图片’ 映射文件夹”**。  
  
     名为 **图像** 的文件夹在项目中显示并包含一个名为 TestProject1 的子文件夹。  此映射文件夹包含可视 Web 部件项目的图像。  
  
7.  在“解决方案资源管理器”中，选择项目节点，然后在菜单栏中选择“项目”，**“添加SharePoint 映射文件夹”**以显示**“添加 SharePoint 映射文件夹”**对话框。  
  
8.  在可用于映射的文件夹的树视图中，选择 **资源** 文件夹，然后选择 **确定** 按钮。  
  
     名为 **资源** 的文件夹显示在项目中。  此文件夹可以存储例如字符串资源文件等项目。  子文件夹对于组织映射文件夹的内容很有用，但在您使用**“添加SharePoint 映射文件夹”**命令添加映射文件夹时，不会自动创建子文件夹。  若要添加子文件夹，请选择 **资源** 文件夹，然后在菜单栏上，选择 **项目**，**新建文件夹**。  
  
## 更改映射文件夹的部署位置  
 默认情况下，映射文件添加到相对于 SharePoint 根目录安装（由标记 {SharePointRoot} 表示）的路径。  不过，您可以通过更改映射文件夹的 **Deployment location** 属性来更改此位置。  每个映射文件夹都具有自己的 **Deployment location** 属性。  
  
#### 更改映射文件夹的部署位置  
  
1.  在先前创建的项目中，选择一个映射文件夹。  
  
2.  在**“属性”**窗口中，选择 **Deployment location** 属性旁的省略号按钮 \(![ASP.NET 移动设计器中的省略号](../sharepoint/media/mwellipsis.png "ASP.NET 移动设计器中的省略号")\)。  
  
3.  在**“添加 SharePoint 映射文件夹”**对话框中，浏览找到要将映射文件夹指向的文件夹。  
  
4.  选择节点，然后选择“确定”按钮。  
  
## 重命名或移除映射文件夹  
  
#### 重命名或移除映射文件夹  
  
1.  在先前创建的项目中，选择一个映射文件夹。  
  
2.  若要重命名映射文件夹，打开快捷菜单，选择**“重命名”**，输入新名称，然后选择Enter键。  
  
     或者，您可以选择重命名的映射文件夹，打开 **属性** 窗口，然后将 **Folder name** 属性的值更改为新名称。  
  
3.  若要从项目中移除映射文件夹，打开快捷菜单，选择**“删除”**，然后在相应的对话框中单击**“确定”**按钮以确认移除。  
  
## 请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  