---
title: "如何： 创建 BDC 模型 |Microsoft 文档"
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
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
ms.assetid: e8b888d4-a531-4d13-9ebf-efbbd33eebc6
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: da7bb2ea8918a0a01716ed090253af8f2f28dbbe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-bdc-model"></a>如何：创建 BDC 模型
  你可以使用该类型的项的模板，然后将模型添加到任何 SharePoint 项目创建业务数据连接 (BDC) 模型。 有关详细信息，请参阅[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。 有关如何设计模型的详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### <a name="to-create-a-bdc-project"></a>若要创建 BDC 项目  
  
1.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
    > [!NOTE]  
    >  如果 IDE 设置为使用 Visual Basic 开发设置，选择**文件**，**新项目**。  
  
     **“新建项目”** 对话框随即打开。  
  
2.  下**Visual Basic**或**Visual C#**，选择**Office/SharePoint**， **SharePoint 解决方案**。  
  
3.  在**模板**窗格中，选择**SharePoint 2013 的空项目**项，然后依次**确定**按钮。  
  
     **SharePoint 自定义向导**打开。  
  
4.  上**指定用于调试的站点和安全性级别**页上，指定本地计算机上的 SharePoint 站点的 URL，选择**部署为场解决方案**选项按钮，，然后选择**完成**按钮。  
  
     将测试你指定的 SharePoint 站点上的模型。  
  
    > [!IMPORTANT]  
    >  必须将项目部署为场解决方案中，因为 BDC 模型，支持仅场解决方案中。  
  
     创建空 SharePoint 项目。  
  
5.  在菜单栏上，选择**项目**，**添加新项**。  
  
6.  在**添加新项**对话框框中，选择**Office/SharePoint**节点。  
  
7.  在 SharePoint 模板列表中，选择**业务数据连接模型 （仅场解决方案）**。  
  
8.  在**名称**框中，为 BDC 模型中，指定一个名称，然后选择**添加**按钮。  
  
     A**业务数据连接模型**项添加到项目。 默认情况下，模型将出现在 BDC 设计器。 有关详细信息，请参阅[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
## <a name="see-also"></a>另请参阅  
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何： 向 SharePoint 项目中添加现有 BDC 模型文件](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [如何： 使用资源文件来指定本地化的名称、 属性和权限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [如何： 在 BDC 功能中包含自定义程序集](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  