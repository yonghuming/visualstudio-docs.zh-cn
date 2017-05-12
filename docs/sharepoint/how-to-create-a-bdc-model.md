---
title: "如何：创建 BDC 模型"
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
  - "BDC [Visual Studio 中的 SharePoint 开发], 创建模型"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发], 创建模型"
ms.assetid: e8b888d4-a531-4d13-9ebf-efbbd33eebc6
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：创建 BDC 模型
  您可以通过使用此类项的模板然后将模型添加到 SharePoint 项目来创建业务数据连接 \(BDC\) 模型。  有关详细信息，请参阅 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  有关如何设计模型的更多信息，请参见 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### 创建 BDC 项目  
  
1.  在菜单栏上，选择**“文件”**，**“新建**、**“项目”**。  
  
    > [!NOTE]  
    >  如果您的 IDE 设置为使用 Visual Basic 开发设置，选择“文件”和“新建项目”。  
  
     将打开**“新建项目”**对话框。  
  
2.  在“Visual Basic”或“Visual C\#”下，依次选择“Office\/SharePoint”、“SharePoint 解决方案”。  
  
3.  在“模板”窗格中，选择“SharePoint 2013 – 空项目”项，然后选择“确定”按钮。  
  
     “SharePoint 自定义向导”打开。  
  
4.  在“指定用于调试的网站和安全级别”页上，指定在本地计算机上 SharePoint 网站的 URL，选择“部署为场解决方案”选项按钮，然后选择“完成”按钮。  
  
     你将在自己指定的 SharePoint 站点上测试模型。  
  
    > [!IMPORTANT]  
    >  必须将该项目部署为场解决方案，因为 BDC 模型仅支持场解决方案。  
  
     已创建一个空 SharePoint 项目。  
  
5.  在菜单栏上，依次选择“项目”、“添加新项”。  
  
6.  在“添加新项”对话框中，选择“Office\/SharePoint”节点。  
  
7.  在 SharePoint 模板列表中，选择“业务数据连接模型（仅场解决方案）”。  
  
8.  在“名称”框中，指定 BDC 模型名称，然后选中“添加”按钮。  
  
     “业务数据连接模型”项便添加到项目中。  默认情况下，模型显示在 BDC 设计器中。  有关详细信息，请参阅 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
## 请参阅  
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何：向 SharePoint 项目添加现有 BDC 模型文件](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [如何：使用资源文件指定本地化名称、属性和权限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [如何：在 BDC 功能中引入自定义程序集](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  