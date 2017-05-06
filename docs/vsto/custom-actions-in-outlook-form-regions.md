---
title: "Outlook 窗体区域中的自定义操作"
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
helpviewer_keywords: 
  - "自定义操作 [Visual Studio 中的 Office 开发]"
  - "窗体区域 [Visual Studio 中的 Office 开发], 自定义操作"
ms.assetid: 583fd5f0-aafa-4858-9c54-38a9fdf3bede
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Outlook 窗体区域中的自定义操作
  操作显示可供用户用来对 Microsoft Office Outlook 项进行响应的按钮。  例如，若要对某个邮件项做出响应，用户可以单击**“答复”**、**“全部答复”**或**“转发”**操作按钮。  每个操作都会创建一个新邮件项，并使用原始项中的信息来填充该项的字段。  
  
 可以创建能够打开任何类型的 Outlook 项的自定义操作。  例如，可以添加用来打开一个新约会或任务项的自定义操作。  设置自定义操作的属性或使用自定义代码来填充新项的字段。  自定义操作显示在 Outlook 检查器窗口中的打开项的**“自定义操作”**下拉列表中。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 向窗体区域中添加自定义操作  
 若要将自定义操作添加到窗体区域中，请使用**“自定义操作”**对话框。  通过展开 **清单** 节点，选择 **CustomActions** 属性，然后单击省略号按钮以在 **解决方案资源管理器** 的 **自定义操作** 对话框 \(![ASP.NET 移动设计器中的省略号](../sharepoint/media/mwellipsis.png "ASP.NET 移动设计器中的省略号")\)。  
  
 使用**“自定义操作”**对话框可以指定目标窗体。  目标窗体是当用户执行自定义操作时显示的窗体。  
  
 使用**“自定义操作”**对话框还可以指定原始项中的信息在目标窗体中的显示方式。  
  
 下表介绍**“自定义操作”**对话框中提供的属性。  
  
|属性|描述|  
|--------|--------|  
|**AddressLike**|指定如何对目标窗体进行寻址。|  
|**Body**|指定原始项的正文如何追加到目标窗体。|  
|**Enabled**|指示是否启用自定义操作。  如果此属性设置为 **false**，则禁用自定义操作。|  
|**方法**|指定当执行自定义操作时可用响应的类型。  自定义操作可以发送窗体、打开窗体或提示用户是否希望发送或打开窗体。|  
|**名称**|指定可用在代码中引用此自定义操作的内部名称。|  
|**ShowOnRibbon**|指示是否在原始项的功能区中显示自定义操作。|  
|**SubjectPrefix**|指定在目标窗体的主题行的开头插入的文本。|  
|**TargetForm**|指定目标窗体的邮件类名称。  例如，键入 **IPM.Task** 可以打开任务窗体。|  
|**标题**|指定自定义操作按钮的标签。|  
  
## 在运行时自定义一个自定义操作  
 使用代码也可以将行为添加到自定义操作中。  例如，可以添加获取电子邮件收件人姓名的代码，并将这些姓名作为与会者添加到新约会项中。  为此，请处理 [Action](HV05247650) 对象的 [CustomAction](HV05247448) 事件。  
  
## 请参阅  
 [创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)   
 [演练：设计 Outlook 窗体区域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [将窗体区域与 Outlook 邮件类关联](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  