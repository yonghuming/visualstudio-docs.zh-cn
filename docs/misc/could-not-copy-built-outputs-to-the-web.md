---
title: "未能将生成输出复制到 Web | Microsoft Docs"
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
  - "vs.tasklisterror.cantcopyoutputstoweb"
ms.assetid: 59cf714b-cf7d-4df9-81ae-d3254969d5bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 未能将生成输出复制到 Web
项目系统无法将一个或多个生成输出文件（例如，生成的 DLL、PDB 或附属程序集）复制到 Web 服务器。  
  
 此错误指示一个或多个生成输出文件未被复制到 Web 服务器。  
  
 当生成的输出文件被锁定或在服务器上为只读模式时通常会出现此错误。 如果文件在服务器上被锁定，则表明 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 运行时未能正确复制服务器上当前存在的程序集、附属项或调试符号。  
  
 还有可能是服务器的磁盘空间不足或网络问题阻碍 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将文件上传到 Web。  
  
### 更正此错误  
  
1.  检查磁盘空间。  
  
2.  如果某个文件被锁定，则重新启动 Web 服务器以释放受影响文件上的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 锁。  
  
## 请参阅  
 [PDB Files](http://msdn.microsoft.com/zh-cn/1761c84e-8c2c-4632-9649-b5f99964ed3f)