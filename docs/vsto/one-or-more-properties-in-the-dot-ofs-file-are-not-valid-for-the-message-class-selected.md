---
title: ".ofs 文件中的一个或多个属性对于选定的消息类无效 | Microsoft Docs"
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
  - "VSTO.NewFormRegionWizard.OFSPropertyError"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: ca9e2ec1-df96-45ca-9611-cec47edfe1e4
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# .ofs 文件中的一个或多个属性对于选定的消息类无效
  如果导入在 Outlook 中设计的窗体区域，但是该窗体区域的一个或多个字段与在“新建窗体区域”向导最后一页上选择的邮件类不兼容，则会出现此错误。  
  
 例如，你可能在“新建窗体区域”向导最后一页上选择了“任务\(IPM.Task\)”。 如果窗体区域包含“办公地址”字段，则会出现此错误，这是因为任务是没有办公地址的。 因此，“办公地址”字段与 IPM.Task 邮件类不兼容。  
  
### 更正此错误  
  
-   在“新建窗体区域”向导最后一页上，选择与窗体区域上的字段兼容的邮件类。  
  
-   在 Outlook 的窗体设计器中，删除与要在“新建窗体区域”向导最后一页上选择的邮件类不兼容的字段。  
  
## 请参阅  
 [演练：导入在 Outlook 中设计的窗体区域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  