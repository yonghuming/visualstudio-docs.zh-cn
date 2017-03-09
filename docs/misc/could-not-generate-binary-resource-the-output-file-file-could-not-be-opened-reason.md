---
title: "无法生成二进制资源。 无法打开输出文件“file”。 &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.resx_output_locked"
ms.assetid: 9f554bf4-3202-4bd0-9acb-7255386e0954
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 无法生成二进制资源。 无法打开输出文件“file”。 &lt;reason&gt;
项目系统无法删除已过时的 .resources 文件的副本。 作为准备资源过程的一部分，项目系统会将带 .resx 扩展名的 XML 文件转换成二进制 .resources 文件供 .NET 资源管理器使用。  
  
 在错误信息文本的末尾给出了特定于操作系统的原因，在此处提供了最佳信息。  
  
 **更正此错误**  
  
-   重新启动 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
     此错误将导致生成过程失败。  
  
## 请参阅  
 [Visual Studio 和 Visual C\# 中的文件类型和文件扩展名](http://msdn.microsoft.com/zh-cn/f793852c-da06-4d52-a826-65f635844772)