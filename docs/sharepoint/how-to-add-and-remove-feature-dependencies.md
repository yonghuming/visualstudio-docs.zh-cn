---
title: "如何： 添加和移除功能依赖关系 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, features
ms.assetid: 2b34c8d9-c975-4fe9-b8e0-52db4a6014ea
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d758c5d4f410881989492f64dd7a7e5b8dc73804
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>如何：添加和移除功能依赖项
  你的 SharePoint 功能可能依赖于用于功能或数据的其他功能。 在这些情况下，可以将这些其他功能为您的功能标记为依赖关系。 这种方式，可确保 SharePoint 服务器，激活你的功能之前，激活相关功能。  
  
## <a name="adding-dependencies"></a>添加依赖关系  
 为依赖项，可以在你的解决方案中添加其他功能。 这种方式，可以确保所需的功能已安装并激活之前安装你的功能。  
  
#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>若要添加一项功能在解决方案中的依赖项  
  
1.  打开功能设计器，展开**功能激活依赖关系**节点，然后选择**添加**按钮。  
  
2.  在**添加功能激活依赖关系**对话框框中，选择**添加解决方案中的功能的依赖项**选项按钮，请选择你想要添加为一个依赖项，该功能的标题，然后选择**添加**按钮。  
  
     可以通过在选择 Ctrl 键的同时选择多个标题来添加多个功能。  
  
## <a name="adding-custom-dependencies"></a>添加自定义的依赖关系  
 作为依赖项，可以在 SharePoint 服务器上添加已部署的功能。 这样一来，SharePoint 激活过程将检查以确保安装你的功能之前，激活所有相关的功能。  
  
#### <a name="to-add-a-dependency-by-the-feature-id"></a>若要添加的功能 ID 的依赖项  
  
1.  打开功能设计器，展开**功能激活依赖关系**节点，然后选择**添加**按钮。  
  
2.  在**添加功能激活依赖关系**对话框框中，选择**添加自定义的依赖项**选项按钮。  
  
3.  在**功能 ID**文本框中，输入你想要将标记为激活依赖项，然后选择的功能的 GUID**添加**按钮。  
  
## <a name="editing-custom-dependencies"></a>编辑自定义的依赖关系  
 你可以编辑以前添加的自定义依赖关系。 但是，将在你的解决方案可以仅删除的相关功能不能编辑。  
  
#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>若要更改依赖于解决方案中的功能  
  
1.  打开功能设计器中，，然后展开**功能激活依赖关系**节点。  
  
2.  选择你想要编辑，然后选择功能名称**编辑**按钮。  
  
3.  在**编辑自定义功能激活依赖项**对话框中，更改标题、 功能 ID 或说明，然后依次**提交**按钮。  
  
## <a name="removing-dependencies"></a>删除依赖关系  
  
#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>若要在解决方案中删除在功能上的依赖关系  
  
1.  在功能设计器中，展开**功能激活依赖关系**节点，选择你想要删除，然后选择功能名称**删除**按钮。  
  
## <a name="see-also"></a>另请参阅  
 [创建 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)   
 [如何： 自定义 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：在 SharePoint 功能中添加和删除项](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  