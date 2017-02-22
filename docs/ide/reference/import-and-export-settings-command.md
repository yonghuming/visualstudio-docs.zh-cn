---
title: "“导入和导出设置”命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Tools.ImportandExportSettings"
helpviewer_keywords: 
  - "Tools.ImportandExportSettings"
  - "“导入和导出设置”命令"
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “导入和导出设置”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

导入、导出或重置 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 设置。  
  
## 语法  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## 开关  
 \/export:`filename`  
 可选。  将当前设置导出到指定文件。  
  
 \/import:`filename`  
 可选。  导入指定文件中的设置。  
  
 \/reset  
 可选。  重置当前设置。  
  
## 备注  
 不带任何开关运行该命令将打开**“导入和导出设置”**向导。  有关更多信息，请参见 [How to: Share Settings Between Computers or Visual Studio Versions](http://msdn.microsoft.com/zh-cn/1131fb10-35c1-42da-9cd8-91aa3235b882)。  
  
## 示例  
 下面的命令将当前设置导出到文件 `MyFile.vssettings`。  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## 请参阅  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)