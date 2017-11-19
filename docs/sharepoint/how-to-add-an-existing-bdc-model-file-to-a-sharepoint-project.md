---
title: "如何： 向 SharePoint 项目中添加现有 BDC 模型文件 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
ms.assetid: e843738a-f936-4dcd-be35-249407573b74
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d0ae7190d0b55dec593e8d9f7c20542d5a7d5bc6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>如何：向 SharePoint 项目添加现有 BDC 模型文件
  通过使用 Visual Studio 将模型文件 (.bdcm) 添加到任何 SharePoint 场项目，可以自定义、打包和重新部署业务数据连接 (BDC) 模型。 有关详细信息，请参阅[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>将 BDC 模型文件添加到 SharePoint 项目  
  
1.  在**解决方案资源管理器**，选择 SharePoint 项目的文件夹。  
  
2.  在菜单栏上，选择**项目**，**添加现有项**。  
  
3.  在**添加现有项**对话框中，浏览到你想要添加到你的项目，选择该文件，然后选择的模型定义文件的位置**添加**按钮。  
  
     如果该模型没有定义*.NET 程序集类型的业务线 (LOB) 系统*、**添加.NET 程序集 LobSystem**对话框随即打开。  
  
4.  如果显示此对话框，请执行以下步骤之一：  
  
    -   如果你想要编写自定义代码和使用设计器来定义导入模型的元数据，请选择**是**按钮，命名系统，，然后选择**确定**按钮。  
  
    -   否则，请选择**否**按钮，，然后选择**确定**按钮。  
  
     **业务数据连接模型**项添加到项目。  
  
## <a name="see-also"></a>另请参阅  
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何： 创建 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [如何： 使用资源文件来指定本地化的名称、 属性和权限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [如何： 在 BDC 功能中包含自定义程序集](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  