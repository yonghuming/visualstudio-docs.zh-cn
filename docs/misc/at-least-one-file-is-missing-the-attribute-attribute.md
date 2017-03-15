---
title: "At least one file is missing the &#39;attribute&#39; attribute | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_file_attrib"
ms.assetid: 2627974b-c9cd-4d85-9af4-dd3811214ea4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one file is missing the &#39;attribute&#39; attribute
已经从 .vbproj 或 .csproj 文件读取的文件节点缺少项目系统所需要的某些特性。  目前，唯一的此类特性是 `RelPath` 特性，该特性指定文件在项目文件夹下所处的位置。  
  
 此错误很可能由手动编辑项目文件引起。  
  
 **更正此错误**  
  
-   从项目文件中移除受影响的文件节点。  而且，如果该文件仍然在磁盘上，则可以切换到**“显示所有文件”**模式（通过在解决方案资源管理器的工具栏中单击该按钮），右击受影响的文件，然后选择**“包括在项目中”**。  
  
     不会将任何缺少 `RelPath` 特性的文件添加到项目中。  
  
## 请参阅  
 [项目文件](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-cn/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)