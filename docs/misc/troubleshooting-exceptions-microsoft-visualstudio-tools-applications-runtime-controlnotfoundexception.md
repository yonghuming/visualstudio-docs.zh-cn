---
title: "关于异常的疑难解答：Microsoft.VisualStudio.Tools.Applications.Runtime.ControlNotFoundException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Microsoft.VisualStudio.Tools.Applications.Runtime.ControlNotFoundException 异常"
ms.assetid: 87995c5e-5831-474d-a5f8-d991a9abe126
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：Microsoft.VisualStudio.Tools.Applications.Runtime.ControlNotFoundException
当代码尝试访问不在文档上的控件时，引发 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ControlNotFoundException> 异常。 控件可能已被最终用户或其他代码移除。 尝试访问控件之前，无法检查该控件是否存在；如果控件已被移除，则解决方案将不工作。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ControlNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)