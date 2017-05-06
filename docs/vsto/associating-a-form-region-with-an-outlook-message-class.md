---
title: "将窗体区域与 Outlook 邮件类关联"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTO.NewFormRegionWizard.InvalidMessageClassName"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "窗体区域 [Visual Studio 中的 Office 开发], 邮件类"
  - "FormRegionMessageClassAttribute"
ms.assetid: e2db8d61-fd5f-4059-beec-33b66970f520
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 将窗体区域与 Outlook 邮件类关联
  通过将一个窗体区域与每个显示该窗体区域的 Microsoft Office Outlook 项的邮件类关联，可以指定由哪些项显示该窗体区域。  例如，如果要将一个窗体区域追加到一个邮件项的底部，则可以将该窗体区域与 IPM.Note 邮件类关联。  
  
 若要将一个窗体区域与一个邮件类关联，请在**“新建 Outlook 窗体区域”**向导中指定该邮件类名称或是将一个特性应用于该窗体区域工厂类。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 了解 Outlook 邮件类  
 Outlook 邮件类标识 Outlook 项的类型。  下表列出了八种标准类型的项以及其邮件类名称。  
  
|Outlook 项类型|邮件类名称|  
|-----------------|-----------|  
|AppointmentItem|IPM.Appointment|  
|ContactItem|IPM.Contact|  
|DistListItem|IPM.DistList|  
|JournalItem|IPM.Activity|  
|MailItem|IPM.Note|  
|PostItem|IPM.Post 或 IPM.Post.RSS|  
|TaskItem|IPM.Task|  
  
 还可以指定自定义邮件类的名称。  自定义邮件类标识在 Outlook 中定义的自定义窗体。  
  
> [!NOTE]  
>  对于替换和全部替换窗体区域，可以指定新的自定义邮件类名称。  无需使用现有自定义窗体的邮件类名称。  自定义邮件类的名称必须是唯一的。  确保该名称唯一的一种方式是使用某种命名约定，如：\<*标准邮件类名称*\>.\<*公司*\>.\<*邮件类名称*\>（例如：IPM.Note.Contoso.MyMessageClass）。  
  
## 将窗体区域与 Outlook 邮件类关联  
 可通过两种方式将窗体区域与邮件类关联：  
  
-   使用**“新建 Outlook 窗体区域”**向导。  
  
-   应用类特性。  
  
### 使用“新建 Outlook 窗体区域”向导  
 在**“新建 Outlook 窗体区域”**向导的最后一页上，可以选择标准邮件类，以及键入要将其与窗体区域关联的自定义邮件类的名称。  
  
 如果窗体区域用于替换整个窗体或窗体的默认页面，则不能使用标准邮件类。  只能为将新页面添加到窗体的窗体或是追加到窗体底部的窗体指定标准邮件类名称。  有关更多信息，请参见[如何：向 Outlook 外接程序项目中添加窗体区域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
 若要包含一个或多个自定义邮件类，请在**“哪些自定义邮件类将显示此窗体区域?”**框中键入其名称。  
  
 键入的名称必须符合以下准则：  
  
-   使用完全限定邮件类名称（例如：“IPM.Note.Contoso”）。  
  
-   使用分号分隔多个邮件类名称。  
  
-   不得包含标准 Outlook 邮件类（如“IPM.Note”或“IPM.Contact”）。  只能包含自定义邮件类（如“IPM.Note.Contoso”）。  
  
-   不得指定基邮件类本身（例如：“IPM”）。  
  
-   每个邮件类名称的长度不得超过 256 个字符。  
  
 **“新建 Outlook 窗体区域”**向导会在您单击**“完成”**时验证您的输入的格式。  
  
> [!NOTE]  
>  **“新建 Outlook 窗体区域”**向导不会验证您提供的邮件类名称是否正确或有效。  
  
 在完成该向导时，**“新建 Outlook 窗体区域”**向导会将特性应用于包含指定邮件类名称的窗体区域类。  也可以手动应用这些特性。  
  
### 应用类特性  
 在完成**“新建 Outlook 窗体区域”**向导后便可以将窗体区域与 Outlook 邮件类关联。  若要完成此操作，请将特性应用于窗体区域工厂类。  
  
 下例演示两个 <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> 特性，它们已应用于一个名为 `myFormRegion` 的窗体区域工厂类。  第一个特性将该窗体区域与一个邮件窗体的标准邮件类关联。  第二个特性将该窗体区域与一个名为 `IPM.Task.Contoso` 的自定义邮件类关联。  
  
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/CS/FormRegion1.cs#1)]
 [!code-vb[Trin_Outlook_FR_Attributes#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/VB/FormRegion1.vb#1)]  
  
 特性必须符合以下准则：  
  
-   对于自定义邮件类，请使用完全限定邮件类名称（例如：“IPM.Note.Contoso”）。  
  
-   不得指定基邮件类本身（例如：“IPM”）。  
  
-   每个邮件类名称的长度不得超过 256 个字符。  
  
-   如果窗体区域替换整个窗体或窗体的默认页面，则不得包含标准邮件类的名称。  只能为将新页面添加到窗体的窗体或是追加到窗体底部的窗体指定标准邮件类名称。  有关更多信息，请参见[如何：向 Outlook 外接程序项目中添加窗体区域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
 Visual Studio 会在您生成项目时验证邮件类名称的格式。  
  
> [!NOTE]  
>  Visual Studio 不会验证您提供的邮件类名称是否正确或有效。  
  
## 请参阅  
 [在运行时访问窗体区域](../vsto/accessing-a-form-region-at-run-time.md)   
 [创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)   
 [演练：设计 Outlook 窗体区域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Outlook 窗体区域创建准则](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [有关窗体名称和邮件类](HV01044315)   
 [Outlook 如何窗体，并且项目](HV01044298)  
  
  