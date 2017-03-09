---
title: "The project file is missing the &#39;section&#39; section | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_sectionerr"
ms.assetid: 516ab410-1b73-4539-9654-6323af6135b2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The project file is missing the &#39;section&#39; section
.vbproj 或 .csproj 文件已损坏。  缺少以下某一节：  
  
-   Build  
  
-   Files  
  
-   VisualStudio  
  
-   VisualBasic 或 CSHARP  
  
 如果缺少 VisualStudio、VisualBasic 或 CSHARP 节，项目将不加载。  如果缺少 Build 或 Files 节，项目文件将按如下方式加载：  
  
-   如果缺少 Build，将丢失所有的生成设置和配置信息。  
  
-   如果缺少 Files，项目中将没有文件。  
  
 **更正此错误**  
  
-   重新创建项目。  
  
## 请参阅  
 [项目文件](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-cn/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)