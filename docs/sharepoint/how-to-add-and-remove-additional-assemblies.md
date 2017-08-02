---
title: "如何：添加和移除附加程序集"
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
  - "VS.SharePointTools.RAD.CustomAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发，包"
ms.assetid: d9d1e8db-9df2-4e07-ac8d-59ef05d24090
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：添加和移除附加程序集
  如果 SharePoint 包依赖附加程序集来获得功能或数据，则可以将这些程序集添加到解决方案包 \(.wsp\) 中。  通过这种方式，SharePoint Server 可确保随包一起安装自定义程序集。  
  
 您还可以添加和更改与程序集关联的安全控件和类资源文件。  
  
## 添加附加程序集、安全控件和类资源  
 可以将附加程序集添加到 SharePoint 解决方案包中。  沙盒解决方案中的附加程序集将部署到全局程序集缓存中，而沙盒解决方案中的 SharePoint 项目项将添加到内容数据库中。  还可以将安全控件和类资源添加到这些附加程序集中。  有关安全控件的详细信息，请参阅[在项目项中提供打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) 或“创建SafeControl项在[SharePoint Foundation中部署Web部件](http://go.microsoft.com/fwlink/?LinkId=245505)。  
  
#### 添加现有程序集  
  
1.  打开**“包设计器”**。  有关详细信息，请参阅[如何：自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  选择**“高级”**选项卡。  
  
3.  在列表中选择**添加**按钮，再选择**添加存在的程序集**。  
  
     将出现**“添加现有程序集”**对话框。  
  
4.  选择省略号 \(![ASP.NET 移动设计器中的省略号](~/docs/sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器中的省略号")\)，并选择要添加的程序集。  为了实现可移植性，建议您使用选定程序集的相对路径。  
  
5.  对于**“部署目标”**，选择**“GlobalAssemblyCache”**选择按钮，以将程序集部署到全局程序集缓存中，或选择**“WebApplication”**以将程序集部署到正在运行的 SharePoint Server 的 WebApplication 文件夹中。  
  
#### 从项目输出添加程序集  
  
1.  打开**“包设计器”**。  
  
     有关详细信息，请参阅[如何：自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  选择**“高级”**选项卡。  
  
3.  选择**添加**按钮，在列表中再选择**项目输出中的添加程序集**。  
  
     这将出现**“从项目输出添加程序集”**对话框。  
  
4.  在**源程序**列表中，选择您要添加的源程序。  
  
5.  对于**“部署目标”**，选择**“GlobalAssemblyCache”**选择按钮，以将程序集部署到全局程序集缓存中，或选择**“WebApplication”**以将程序集部署到正在运行的 SharePoint Server 的 WebApplication 文件夹中。  
  
#### 添加安全控件  
  
1.  打开**“编辑现有程序集”**对话框。  为完成此操作，请打开包设计器，选择**“高级”**选项卡，选择程序集，然后单击**“编辑”**按钮。  
  
2.  在**“安全控件”**窗格中，选择**“单击此处添加新项”**按钮。  
  
3.  在**“程序集名称”**列中，键入程序集的名称。  
  
4.  在**“命名空间”**列中，键入安全控件的命名空间的名称。  
  
5.  在**“类型名称”**列中，键入类型的名称。  
  
#### 添加类资源  
  
1.  打开**“编辑现有程序集”**对话框。  为完成此操作，请打开包设计器，选择**“高级”**选项卡，选择程序集，然后选择**“编辑”**按钮。  
  
2.  在**“类资源”**窗格中，选择**“单击此处添加新项目”**按钮。  
  
3.  在**“文件名”**列中，选择省略号 \(![ASP.NET 移动设计器中的省略号](~/docs/sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器中的省略号")\)，并选择您要添加的类资源。  
  
## 删除自定义程序集  
 可以从 SharePoint 包中删除程序集，或从现有程序集中删除安全控件和类资源。  
  
#### 删除现有程序集  
  
1.  打开**“包设计器”**。  有关详细信息，请参阅[如何：自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  选择**“高级”**选项卡。  
  
3.  在**“附加程序集”**窗格中，选择您要删除的自定义程序集。  
  
4.  选择**“删除”**按钮。  
  
#### 删除程序集的安全控件  
  
1.  打开**“编辑现有程序集”**对话框。  为完成此操作，请打开包设计器，选择**“高级”**选项卡，选择程序集，然后选择**“编辑”**按钮。  
  
2.  选择您要删除的安全控件。  
  
3.  选择 Delete 键。  
  
#### 删除程序集的类资源  
  
1.  打开**“编辑现有程序集”**对话框。  为完成此操作，请打开包设计器，选择**“高级”**选项卡，选择程序集，然后选择**“编辑”**按钮。  
  
2.  选择您要删除的类资源。  
  
3.  选择 Delete 键。  
  
## 请参阅  
 [创建 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)   
 [如何：自定义 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：在 SharePoint 功能中添加和移除项](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [NIB: Building SharePoint Solutions with Team Foundation Server](http://msdn.microsoft.com/zh-cn/700a570a-e98e-4425-aadd-34c014868d43)  
  
  