---
title: "如何： 添加和移除附加程序集 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: d9d1e8db-9df2-4e07-ac8d-59ef05d24090
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7b7859738ac1fe70bdca4cdca5d2dff1220a22b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>如何：添加和移除附加程序集
  如果 SharePoint 包依赖于其他程序集的功能或数据，你可以将程序集添加到你的解决方案包 (.wsp)。 这样一来，SharePoint 服务器将确保自定义程序集随包一起安装。  
  
 你还可以添加和更改的安全控件和类使用的程序集相关联的资源文件。  
  
## <a name="adding-additional-assemblies-safe-controls-and-class-resources"></a>添加其他程序集、 安全控件和类资源  
 你可以添加到 SharePoint 解决方案包的其他程序集。 沙盒解决方案中的其他程序集部署到全局程序集缓存中，但在沙盒解决方案中的 SharePoint 项目项添加到内容数据库。 此外可以将安全控件和类资源添加到这些其他的程序集。 安全控件有关的详细信息，请参阅[提供打包和部署信息在项目项中](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)或"创建 SafeControl 条目"中[SharePoint Foundation 中部署 Web 部件](http://go.microsoft.com/fwlink/?LinkId=245505)。  
  
#### <a name="to-add-an-existing-assembly"></a>若要添加的现有程序集  
  
1.  打开**包设计器**。 有关详细信息，请参阅[如何： 自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  选择**高级**选项卡。  
  
3.  选择**添加**按钮，，然后选择**添加现有程序集**从列表中。  
  
     **添加现有程序集**对话框随即出现。  
  
4.  选择省略号 (![ASP.NET 移动设计器椭圆](../sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器椭圆"))，然后选择你想要添加的程序集。 我们建议出于可移植性目的使用选定的程序集的相对路径。  
  
5.  有关**部署目标**，选择**GlobalAssemblyCache**选项按钮以将程序集部署到全局程序集缓存中，或选择**WebApplication**选项若要将程序集部署到运行 SharePoint 服务器上的 web 应用程序文件夹的按钮。  
  
#### <a name="to-add-an-assembly-from-project-output"></a>若要从项目输出中添加程序集  
  
1.  打开**包设计器**。  
  
     有关详细信息，请参阅[如何： 自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  选择**高级**选项卡。  
  
3.  选择**添加**按钮，，然后选择**添加项目输出中的程序集**从列表中。  
  
     **添加项目输出中的程序集**对话框随即出现。  
  
4.  在**源项目**列表，并选择你想要添加的源项目。  
  
5.  有关**部署目标**，选择**GlobalAssemblyCache**选项按钮以将程序集部署到全局程序集缓存中，或选择**WebApplication**选项若要将程序集部署到运行 SharePoint 服务器上的 web 应用程序文件夹的按钮。  
  
#### <a name="to-add-a-safe-control"></a>若要添加安全控件  
  
1.  打开**编辑现有程序集**对话框。 若要完成此操作，打开在包设计器，选择**高级**选项卡上，选择一个程序集，，然后选择**编辑**按钮。  
  
2.  在**安全控件**窗格中，选择**单击此处以添加新项**按钮。  
  
3.  在**程序集名称**列中，输入程序集的名称。  
  
4.  在**Namespace**列中，输入安全控件的命名空间的名称。  
  
5.  在**类型名称**列中，输入类型的名称。  
  
#### <a name="to-add-a-class-resource"></a>若要添加类资源  
  
1.  打开**编辑现有程序集**对话框。 若要完成此操作，打开在包设计器，选择**高级**选项卡上，选择一个程序集，，然后选择**编辑**按钮。  
  
2.  在**类资源**窗格中，选择**单击此处以添加新项**按钮。  
  
3.  在**文件名**列中，选择省略号 (![ASP.NET 移动设计器椭圆](../sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器椭圆"))，并选择你想要添加的类资源。  
  
## <a name="deleting-custom-assemblies"></a>删除自定义程序集  
 你可以从 SharePoint 包，删除程序集，或从现有程序集删除安全控件和类资源。  
  
#### <a name="to-delete-an-existing-assembly"></a>若要删除现有的程序集  
  
1.  打开**包设计器**。 有关详细信息，请参阅[如何： 自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  选择**高级**选项卡。  
  
3.  在**其他程序集**窗格中，选择你想要删除的自定义程序集。  
  
4.  选择**删除**按钮。  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>若要删除的程序集的安全控件  
  
1.  打开**编辑现有程序集**对话框。 若要完成此操作，打开在包设计器，选择**高级**选项卡上，选择一个程序集，，然后选择**编辑**按钮。  
  
2.  选择你想要删除的安全控件。  
  
3.  选择删除键。  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>若要删除类资源的程序集  
  
1.  打开**编辑现有程序集**对话框。 若要完成此操作，打开在包设计器，选择**高级**选项卡上，选择一个程序集，，然后选择**编辑**按钮。  
  
2.  选择你想要删除的类资源。  
  
3.  选择删除键。  
  
## <a name="see-also"></a>另请参阅  
 [创建 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)   
 [如何： 自定义 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：在 SharePoint 功能中添加和删除项](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
  
  