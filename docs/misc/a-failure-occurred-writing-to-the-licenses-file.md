---
title: "A failure occurred writing to the licenses file | Microsoft Docs"
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
  - "vs.tasklisterror.fail_writing_licenses_file"
ms.assetid: 7ea1e2ac-fc94-4d53-8ce9-2ae31bcba85d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# A failure occurred writing to the licenses file
项目系统未能写入转换的文件。  作为准备许可证的一部分，项目系统会将文本 .licx 文件转换为 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 授权系统可理解的二进制许可证文件。  
  
 此错误的可能原因包括设备没有剩余的磁盘空间或超出了文件名的 MAX\_PATH 限制。  
  
 **更正此错误**  
  
-   将项目移动到具有较短绝对路径名的其他文件夹中或缩短输出文件名。  
  
     若发生此错误，则生成进程将会失败。  
  
## 请参阅  
 [如何：授予组件和控件许可权限](../Topic/How%20to:%20License%20Components%20and%20Controls.md)