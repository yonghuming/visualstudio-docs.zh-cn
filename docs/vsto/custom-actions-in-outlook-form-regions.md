---
title: "在 Outlook 中的自定义操作窗体区域 |Microsoft 文档"
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
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
ms.assetid: 583fd5f0-aafa-4858-9c54-38a9fdf3bede
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74c688d0430b95c54f1f871ad6f82fde6fa781ac
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="custom-actions-in-outlook-form-regions"></a>Outlook 窗体区域中的自定义操作
  操作显示使用户能够对 Microsoft Office Outlook 项做出响应的按钮。 例如，若要响应一封邮件，用户单击**答复**，**全部答复**，或**转发**操作按钮。 每个这些操作创建一个新的邮件项，并使用原始项中的信息填充的项的字段。  
  
 你可以创建自定义操作打开任何种类的 Outlook 项。 例如，你可以添加自定义操作打开新的约会或任务项。 设置自定义操作的属性或使用自定义代码以填充新的项的字段。 自定义操作显示在**自定义操作**下拉列表在 Outlook 检查器窗口中处于打开状态的项。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="adding-custom-actions-to-a-form-region"></a>向窗体区域添加自定义操作  
 若要将自定义操作添加到窗体区域，使用**自定义操作**对话框。 你可以打开**自定义操作**中的对话框**解决方案资源管理器**通过展开**清单**节点，选择**CustomActions**属性，，然后单击省略号按钮 (![ASP.NET 移动设计器椭圆](../sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器椭圆"))。  
  
 你可以使用**自定义操作**对话框可以指定*目标窗体*。 目标窗体是用户执行自定义操作时出现的表单。  
  
 你还可以使用**自定义操作**对话框可以指定希望从原始项目以在目标窗体中显示的信息的方式。  
  
 下表介绍中可用的属性**自定义操作**对话框。  
  
|属性|描述|  
|--------------|-----------------|  
|**AddressLike**|指定将如何解决目标窗体。|  
|**正文**|指定如何与原始项目的正文追加到目标窗体。|  
|**启用**|指示是否启用自定义操作。 如果此属性设置为**false**，自定义操作将被禁用。|  
|**方法**|执行自定义操作时，请指定可用的响应的类型。 自定义操作可以发送该窗体、 打开窗体，或提示用户，他们想要发送还是打开窗体。|  
|**Name**|指定可用于引用此自定义操作代码中的内部名称。|  
|**ShowOnRibbon**|指示是否在原始项的功能区上显示的自定义操作。|  
|**SubjectPrefix**|指定的目标窗体的主题行的开始处插入的文本。|  
|**TargetForm**|指定目标窗体的 message 类名。 例如，键入**IPM。任务**若要打开的任务窗体。|  
|**标题**|指定自定义操作按钮的标签。|  
  
## <a name="customizing-a-custom-action-at-run-time"></a>自定义在运行时的自定义操作  
 你还可以将行为添加到使用代码的自定义操作。 例如，你可以添加代码，它接受电子邮件收件人的名称，并将这些名称添加为与会者中新的约会项。 若要执行此操作，处理[CustomAction](http://msdn.microsoft.com/library/office/ff862186.aspx)事件[MailItem 对象](http://msdn.microsoft.com/library/office/ff861332.aspx)。  
  
## <a name="see-also"></a>另请参阅  
 [创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)   
 [演练： 设计 Outlook 窗体区域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [将窗体区域与 Outlook 邮件类关联](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  