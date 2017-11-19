---
title: "如何： 定义方法实例 |Microsoft 文档"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
ms.assetid: f0c8a686-c0de-414e-8de9-f228f59d1eb3
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9316eaa48b11342891584e448f8bb67bdce6f682
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-define-a-method-instance"></a>如何：定义方法实例
  您的模型中，必须定义至少一个方法实例对于每个方法。  
  
 通过将添加方法实例**BDC 方法详细信息**窗口。 添加方法实例时，Visual Studio 将添加`<MethodInstance>`到你的项目中的模型文件的 XML 元素。 有关属性的详细信息`<MethodInstance>`元素，请参阅[实例，但](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
### <a name="to-define-a-method-instance"></a>若要定义方法实例  
  
1.  在**BDC 方法详细信息**窗口中，展开的方法节点，然后展开**实例**节点。  
  
2.  在**添加方法实例**列表中，选择**创建 Finder 实例**。  
  
     下方显示一个新的方法实例**实例**节点。  
  
3.  在菜单栏上，选择**视图**，选择**属性窗口**。  
  
4.  在**属性**窗口中，设置方法实例的属性。 有关每个属性的详细信息，请参阅[实例，但](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
## <a name="see-also"></a>另请参阅  
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何： 向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何： 向方法添加参数](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何： 定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  