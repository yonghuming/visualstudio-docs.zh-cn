---
title: "Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotcopyscatterassembly"
ms.assetid: 939519c7-741d-4e05-8b63-71e39fb426ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt;
多文件程序集被复制到要运行它们的项目目录的子目录中。  例如，如果输出路径是 c:\\project1\\bin，并且存在名为 Test 且包含 a.dll 和 b.dll 文件的程序集（其 `CopyLocal` 属性为 `true`），则在复制完成之后会有以下文件结构：  
  
```  
c:\project1\bin\Test  
   c:\project1\bin\Test\Test.dll   (main assembly)  
   c:\project1\bin\Test\a.dll       (file a.dll)  
   c:\project1\bin\Test\b.dll       (file b.dll)  
```  
  
 如果未能在磁盘上创建目录 c:\\project1\\bin\\Test，则项目系统显示此错误。  
  
 此错误指示已用完磁盘空间或到达了路径长度的 MAX\_PATH 限制。  
  
 **更正此错误**  
  
-   检查磁盘空间。  
  
-   将项目移到其路径长度小于该项目当前所位于的文件夹的路径长度的文件夹。  
  
-   将输出目录更改为具有更短绝对路径长度的文件夹（仅适用于客户端项目）。  
  
## 请参阅  
 [有关无效的引用的疑难解答](../ide/troubleshooting-broken-references.md)   
 [如何：使用“添加引用”对话框添加或移除引用](http://msdn.microsoft.com/zh-cn/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/zh-cn/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)