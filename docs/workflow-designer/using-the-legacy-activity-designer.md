---
title: "使用旧版活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 65510d727fdf0640ca8efa646a14d0814951cd4b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="using-the-legacy-activity-designer"></a>使用旧版活动设计器
本主题介绍如何使用旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中的活动设计器。 在面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 时，请使用旧设计器。  
  
 通过使用 Activity 设计器，可以创建自己的自定义活动。  
  
## <a name="creating-a-custom-activity"></a>创建一个自定义活动  
 遵循以下步骤使用 Activity 设计器创建一个自定义活动：  
  
1.  上**项目**菜单上，单击**添加活动**。  
  
2.  选择**活动**或**Activity （具有单独的代码）**模板。  
  
    1.  使用**活动**模板来创建一个活动的活动定义和用户代码在同一个代码文件。  
  
    2.  使用**Activity （具有单独的代码）**模板来创建表示为工作流标记和用户代码在单独的代码文件中定义的活动的活动。  
  
3.  键入活动名称或保留默认名称，然后单击**添加**。  
  
 你可以通过创建类型的新项目来创建一组自定义活动**工作流活动库**。 有关此项目类型的详细信息，请参阅[如何： 创建工作流活动库 （旧版）](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)。  
  
## <a name="configuring-an-activity"></a>配置活动  
 当 Activity 设计器处于活动状态时，可以使用属性浏览器来配置下表中列出的属性。  
  
|属性|注释|  
|--------------|--------------|  
|**Name**|活动的名称。|  
|**基类**|从中派生活动的基类。 默认基类是[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)。 在**属性**窗口中，单击**基类**省略号**[…]**以选择另一个基类中的[浏览并选择.NET 类型对话框 （旧版）](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)。|  
|**描述**|用户定义的活动说明。|  
|**启用**|设置为**True**默认情况下以启用活动执行和验证。 设置为**False**可以禁用活动执行和验证。 有关活动执行和验证的信息，请参阅[开发工作流活动](http://go.microsoft.com/fwlink?LinkID=65024)。|  
  
## <a name="adding-child-activities"></a>添加子活动  
 可以将子活动从工具箱拖到正在设计的活动。 然后可以使用属性浏览器配置每个子活动。  
  
## <a name="see-also"></a>另请参阅  
 [开发工作流活动](http://go.microsoft.com/fwlink?LinkID=65024)   
 [创建自定义活动](http://go.microsoft.com/fwlink?LinkID=65021)   
 [旧工作流活动](../workflow-designer/legacy-workflow-activities.md)   
 [自定义活动示例](http://go.microsoft.com/fwlink?LinkID=65022)   
 [如何： 创建工作流活动库 （旧版）](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)   
 [使用旧版工作流设计器](../workflow-designer/using-the-legacy-workflow-designer.md)