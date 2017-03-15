---
title: "无法将文件“filename”复制到运行目录。 &lt;原因&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cant_copy_to_run_dir"
ms.assetid: 80474e62-7cef-48e9-a7c0-820345d5b591
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 无法将文件“filename”复制到运行目录。 &lt;原因&gt;
以下情况下，会显示此错误：  
  
-   如果引用将 `CopyLocal` 属性（请当在解决方案资源管理器中选择引用时参见“属性”窗口）设置为 `true`，则它无法被复制到该项目正从其中运行的目录。  
  
-   将 `CopyLocal` 属性设置为 `true` 的引用的依赖项无法被复制到该项目正从其中运行的目录。  
  
-   需要在本地复制的任何其他文件无法被复制到该项目正从其中运行的目录。  
  
 大多数情况下，错误消息末尾引用的 `reason` 将报告文件正由另一个进程所使用。 很可能该文件被 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的其他内容锁定了。  
  
 可能存在一个与将项目生成到相同输出目录相关的问题。 在这种情况下，应将两个项目生成到不同的目录。 当生成到不同的目录时，项目系统会将所有依赖程序集复制到项目的输出目录。  
  
 将你正在处理的任何项目的输出添加为工具箱项将导致托管的设计程序锁定该引用。  
  
 如果当前该输出正在运行，则项目系统将不能更新输出目录。  
  
 **更正此错误**  
  
-   检查你计算机的可用磁盘空间  
  
-   检查是否已达到文件系统指定的 MAX\_PATH 限制  
  
     这种情况将不会妨碍生成项目。 但是，它可能会阻止项目正常运行，因为此警告表明无法正确更新被引用程序集的私有副本。 虽然项目可能看起来正在运行，但在执行某些代码路径时，你可能会收到类型加载异常或其他意外行为。  
  
## 请参阅  
 [NIB：如何：设置引用的“复制本地”属性](http://msdn.microsoft.com/zh-cn/dfe2ba13-f27f-4356-a481-ea67d5acacbd)