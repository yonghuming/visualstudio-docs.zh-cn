---
title: "The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_no_add_folder"
ms.assetid: 3f6a5aa7-17cc-4e78-93b7-96e0970e111e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt;
从 .vbproj 或 .csproj 文件读取的文件夹无法添加到项目中。  原因包括：  
  
-   无效的名称。  
  
-   路径内的文件。  例如，如果具有相对于项目的路径 Folder1\\Folder2\\Folder3，但是还有一个相对路径为 Folder1\\Folder2 的文件。  
  
-   项已存在。  当一个文件夹在项目文件中列出两次时，此错误发生。  
  
 此错误很可能由手动编辑项目文件引起。  
  
 **更正此错误**  
  
-   从项目文件中移除受影响的文件夹节点。  
  
     不会将为其显示该诊断的任何文件夹或该文件夹下面的任何文件添加到项目中。  
  
## 请参阅  
 [项目文件](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-cn/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)