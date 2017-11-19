---
title: "如何： 实现 Windows Communication Foundation 协定操作 （旧版） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02d6a544b660a110c618bdcb7d3b778fd82ceaaa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>如何：实现 Windows Communication Foundation 协定操作（旧版）
本主题介绍如何使用面向 [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] 或 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 的旧 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 来实现 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 协定操作。  
  
 拖动之后**ReceiveActivity**到工作流设计图面上活动从工具箱中的，您将创建一个新[!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]协定或导入现有协定和实现操作。 选择和/或创建您的协定和通过其操作[选择操作对话框 （旧版）](../workflow-designer/choose-operation-dialog-box-legacy.md)。  
  
### <a name="to-implement-a-wcf-contract-operation"></a>实现 WCF 协定操作  
  
1.  双击**ReceiveActivity**活动设计器中的，或单击省略号旁边**ServiceOperationInfo**中的属性**属性**窗格。  
  
2.  执行下列操作之一：  
  
    -   单击**添加协定**右上角的对话框。 这将为您创建新的 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] 协定和操作。  
  
         - 或 -  
  
    -   单击**导入**右上角的对话框。 [浏览并选择.NET 类型对话框 （旧版）](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)打开。 搜索包含所需协定的程序集或项目。 选择该协定，然后单击**确定**。  
  
     在创建或导入协定后，您可以为创建或导入的协定添加新操作。 若要添加新的操作，请选择该协定，然后单击**添加操作**右上角的对话框。 完成添加操作后，请继续步骤 3。  
  
3.  选择你想要将与相关联的操作**ReceiveActivity**活动。 您可以更改操作的名称、参数、属性和权限设置，从而对该操作的定义进行操作。  
  
     若要更改名称，输入中的新名称**操作名称**文本框。  
  
     单击**参数**选项卡可访问操作的参数。 您可以更改参数的名称、类型或方向，也可以在操作中添加或删除参数。  
  
     单击**属性**选项卡可访问该操作的操作保护级别和受支持的消息交换功能。  
  
     单击**权限**选项卡可以指定哪些组有权实现该操作。  
  
4.  单击**确定**和**ReceiveActivity**活动将显示它正在实现的操作的操作名称。  
  
5.  将想要用于该操作的实现的工作流活动**ReceiveActivity**活动。  
  
## <a name="see-also"></a>另请参阅  
 [选择操作对话框 （旧版）](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [如何： 调用 WCF 协定操作 （旧版）](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [旧版工作流活动](../workflow-designer/legacy-workflow-activities.md)