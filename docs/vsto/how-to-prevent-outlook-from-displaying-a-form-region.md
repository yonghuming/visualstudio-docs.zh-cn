---
title: "如何：防止 Outlook 显示窗体区域 | Microsoft Docs"
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
  - "取消窗体区域显示"
  - "窗体区域 [Visual Studio 中的 Office 开发], 取消显示"
ms.assetid: 82a25def-776a-476a-a72d-d0a48a827d3c
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：防止 Outlook 显示窗体区域
  在某些情况下，您可能不希望 Microsoft Office Outlook 显示特定项的窗体区域。  例如，如果某一联系人项不包含办公地址，则您可以阻止在图中显示办公地址的窗体区域显示出来。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### 阻止 Outlook 显示窗体区域  
  
1.  打开要修改的窗体区域的代码文件。  
  
2.  展开**“窗体区域工厂”**代码区域。  
  
3.  向 `FormRegionInitializing` 事件处理程序添加代码，将 <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> 类的 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 属性设置为 **true**。  
  
 在此示例中，如果联系人项不包含地址，则将 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 属性设置为 **true**，窗体区域将不会显示。  
  
## 示例  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
## 请参阅  
 [创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)   
 [演练：设计 Outlook 窗体区域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [如何：向 Outlook 外接程序项目中添加窗体区域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [演练：设计 Outlook 窗体区域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [演练：导入在 Outlook 中设计的窗体区域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  