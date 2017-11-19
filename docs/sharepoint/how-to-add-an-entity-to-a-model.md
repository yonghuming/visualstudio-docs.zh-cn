---
title: "如何： 向模型添加实体 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EntityTool
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d8cc1bf4871ef91c5b08cb77963a70e422ee3cdc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-entity-to-a-model"></a>如何：向模型添加实体
  若要创建实体，添加实体控件从 Visual Studio**工具箱**拖动到业务数据连接 (BDC) 设计器。  
  
### <a name="to-add-an-entity-to-the-model"></a>若要将实体添加到模型  
  
1.  创建 BDC 项目，或打开现有 BDC 项目。 有关详细信息，请参阅[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
2.  在**工具箱**，从**BusinessDataCatalog**组中，添加**实体**控件拖到设计器。  
  
     在设计器上将显示新的实体。 Visual Studio 将添加`<Entity>`到你的项目中的 BDC 模型文件的 XML 元素。 实体元素的属性的详细信息，请参阅[实体](http://go.microsoft.com/fwlink/?LinkId=169296)。  
  
3.  在设计器中，打开实体的快捷菜单，选择**添加**，然后选择**标识符**。  
  
     一个新的标识符将出现在该实体。  
  
    > [!NOTE]  
    >  你可以更改实体和中的标识符的名称**属性**窗口。  
  
4.  在类中定义的实体的字段。 你可以向项目添加新类，或使用现有类使用对象关系设计器 （O/R 设计器） 等其他工具创建的。 下面的示例演示一个名为联系人的实体类。  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>另请参阅  
 [如何： 添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何： 添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何： 添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [如何： 添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  