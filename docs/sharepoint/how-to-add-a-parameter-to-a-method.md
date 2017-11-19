---
title: "如何： 向方法添加参数 |Microsoft 文档"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
ms.assetid: c5b6fd32-bf85-4b2a-a01e-f9199f0fb26e
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 881eccae253fc07c13eead45ae9d14658f9adf46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-parameter-to-a-method"></a>如何：向方法添加参数
  若要将信息传递到方法或从方法返回信息，请使用参数。 所有方法必须都具有至少一个参数。 有关如何设计用于支持你想要创建的方法的类型的参数的详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
 当向方法添加参数时，Visual Studio 将添加`<Parameter>`到你的项目中的模型文件的 XML 元素。 有关属性的详细信息`<Parameter>`元素，请参阅[参数](http://go.microsoft.com/fwlink/?LinkId=169284)。  
  
### <a name="to-add-a-parameter-to-a-method"></a>向方法添加参数  
  
1.  将方法添加到实体。  
  
2.  在菜单栏上，选择**视图**，**其他窗口**， **BDC 方法详细信息**。  
  
     **BDC 方法详细信息**窗口随即打开。 有关详细信息，请参阅[BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在**BDC 方法详细信息**窗口中，展开的方法节点，然后展开**参数**节点。  
  
4.  在**添加参数**列表中，选择**创建参数**。  
  
     一个新的参数将显示下**参数**节点。  
  
5.  在菜单栏上，选择**视图**，**属性窗口**。  
  
6.  在**属性**窗口中，设置**名称**为有意义的任何名称的属性。 例如，如果该方法将返回客户，你可能会将该方法**GetCustomers**。  
  
7.  在**BDC 方法详细信息**窗口中，打开个方向的参数，显示的列表，然后选择**中**， **InOut**，**出**，或**返回**。  
  
     有关方向选择要创建的类型方法的详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
8.  修改参数的类型描述符。 有关详细信息，请参阅[如何： 定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
## <a name="see-also"></a>另请参阅  
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何： 向模型添加实体](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何： 定义参数的类型描述符](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [如何： 定义方法实例](../sharepoint/how-to-define-a-method-instance.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  