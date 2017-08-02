---
title: "如何：在 BDC 功能中引入自定义程序集"
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
  - "VS.SharePointTools.BDC.Add_Assemblies_Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 开发], 添加引用"
  - "BDC [Visual Studio 中的 SharePoint 开发], 自定义程序集"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 添加引用"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 自定义程序集"
ms.assetid: 2ddf44b9-5f51-4bca-b8bb-94c4bbd1c5f3
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：在 BDC 功能中引入自定义程序集
  您的项目可以从同一解决方案的其他项目中引用程序集。  但是，必须通过使用**“将引用的程序集分配给 LobSystem”**对话框来将这些程序集添加到该项目的功能文件中。  
  
### 在业务数据连接 \(BDC\) 功能中引入自定义程序集  
  
1.  在**“解决方案资源管理器”**中，选择包含 BDC 模型的文件夹。  
  
2.  在**“视图”**菜单上，单击**“属性窗口”**。  
  
3.  在**“属性”**窗口中，选择**“程序集”**属性，然后（单击）省略号按钮 \(![ASP.NET 移动设计器中的省略号](~/docs/sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器中的省略号")\)。  
  
     将出现**“将引用的程序集分配给 LobSystem”**对话框。  
  
4.  在 **选择程序集** 列表中，选择自定义程序集。  
  
    > [!NOTE]  
    >  如果您已经添加对包含程序集的项目的引用，则这些程序集将仅显示在**“将引用的程序集分配给 LobSystem”**对话框中。  有关详细信息，请参阅[如何：使用“添加引用”对话框添加或移除引用](http://msdn.microsoft.com/zh-cn/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。  
  
5.  在**“引用属性”**组中，打开**“LobSystem 范围”**属性显示的列表，选择使用自定义程序集的方法的 LOB 系统，然后选择**“确认”**按钮。  
  
    > [!NOTE]  
    >  若要调试自定义程序集中的代码，您必须将该程序集添加到解决方案包中。  有关详细信息，请参阅[如何：添加和移除附加程序集](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。  
  
## 请参阅  
 [如何：使用资源文件指定本地化名称、属性和权限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [如何：向 SharePoint 项目添加现有 BDC 模型文件](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何：创建 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  