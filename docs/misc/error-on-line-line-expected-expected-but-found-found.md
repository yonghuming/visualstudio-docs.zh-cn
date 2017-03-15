---
title: "Error on line &lt;line&gt;. Expected &#39;expected&#39; but found &#39;found&#39; | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_lineerr"
ms.assetid: d78934c9-6d57-42b2-9968-2b0aa4bf05e2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error on line &lt;line&gt;. Expected &#39;expected&#39; but found &#39;found&#39;
这是读取项目文件时的一般性 XML 分析错误。  对于项目文件 \(.vbproj\/.csproj\) 和每个用户的设置文件 \(.vbproj.user\/.csproj.user\)，此错误均可能发生。  项目系统将在 `expected` 和 `found` 参数中提供更多信息。  
  
 此错误很可能由手动编辑项目（或用户）文件引起。  
  
 **更正此错误**  
  
-   再次编辑项目文件，将其恢复为所满意的条件。  
  
     根据错误的严重性，您可能无法打开该项目。  
  
## 请参阅  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-cn/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)