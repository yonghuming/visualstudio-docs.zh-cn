---
title: "At least one startup service is missing the &#39;attribute&#39; attribute | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_missing_ss_attrib"
ms.assetid: 987c42dc-4394-4b07-b7fa-a8e7afc6fdfb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one startup service is missing the &#39;attribute&#39; attribute
启动服务需要 ID 特性，但未在 `<Service>` 元素上找到该特性。  例如：  
  
```  
<Service ID="{0000-0000-0000-00000000-000000000000}"/>  
```  
  
 这指示项目文件已损坏。  
  
 此错误很可能由手动编辑项目文件引起。  
  
 **更正此错误**  
  
-   保存项目文件。  
  
     有缺陷的节将不会被写出，并且下次您打开该项目时将不会发生此错误。  
  
## 请参阅  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-cn/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)