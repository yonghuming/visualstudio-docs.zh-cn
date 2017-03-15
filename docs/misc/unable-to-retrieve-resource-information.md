---
title: "Unable to retrieve resource information | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.resx_scan_failed"
ms.assetid: e4389ff0-eb64-4c31-b32f-5216c73fadfb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to retrieve resource information
扫描 .resx 文件的层次结构失败。  
  
 作为在**“输出”**窗口中显示的 `Preparing resources` 生成步骤的一部分，项目系统将扫描项目层次结构，以查找所有扩展名为 .resx 的文件。  这个操作将产生一个 .resx XML 文件的列表，这些文件需要先转换为 .resources 二进制文件，然后才可以作为资源包括在项目的输出中。  
  
 **更正此错误**  
  
-   重新启动 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  如果该方法无效，请打电话给“Microsoft 产品支持服务”以报告此问题。  
  
     此错误将导致生成进程失败。  
  
## 请参阅  
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/zh-cn/f793852c-da06-4d52-a826-65f635844772)