---
title: "Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.satellite_build_failed"
ms.assetid: c97c589f-cf4d-4f6b-941a-7526a1091fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt;
未能生成特定区域性的附属程序集。  此错误将使生成进程失败。  
  
 出现此错误有两种原因：  
  
1.  系统未安装 ALINK.EXE。  
  
2.  ALINK.EXE 失败，但未返回任何扩展的错误信息。  
  
 **更正此错误**  
  
-   重新安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或只重新安装 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。  
  
-   当报告的 \<原因\> 为“未能启动程序集链接器。  该文件存在。”时，清空用于生成这些文件的 Temp 文件夹（例如，C:\\Documents and Settings\\\<用户\>\\Local Settings\\Temp）。  
  
## 请参阅  
 [Al.exe（程序集链接器）](../Topic/Al.exe%20\(Assembly%20Linker\).md)