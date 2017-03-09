---
title: "Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_write_gen_output"
ms.assetid: eafcee9e-186b-4019-9042-8d8f9fc0925a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt;
项目系统未能将自定义工具的输出写入指定的文件。  
  
 如果自定义工具的输入的文件名保持不变，则自定义工具的输出将被写入到同一文件中。  如果生成的输出被锁定在磁盘上，则发生此错误。  
  
 **更正此错误**  
  
-   重新启动 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，右击受影响的文件，然后从快捷菜单中选择**“运行自定义工具”**以重新运行自定义工具。  
  
     因为项目系统未能将其更新，所以生成的文件可能已过期。