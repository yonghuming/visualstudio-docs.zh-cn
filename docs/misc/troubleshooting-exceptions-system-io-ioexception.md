---
title: "关于异常的疑难解答：System.IO.IOException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IOException 类"
ms.assetid: 87812daa-0784-43dc-b3dc-6652a960c362
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.IO.IOException
如果发生 I\/O 错误（如读写文件失败），则会引发 <xref:System.IO.IOException>。  
  
## 相关提示  
 **确保文件和目录存在。**  
 验证尝试进行读写的目录是否存在。 验证尝试进行读取的文件是否存在。  
  
### 备注  
 <xref:System.IO.IOException> 是在使用流、文件和目录访问信息时引发的异常的基类。  
  
 该基类库包含以下类型，其中每个类型都是 <xref:System.IO.IOException> 的派生类：  
  
-   <xref:System.IO.DirectoryNotFoundException>  
  
-   <xref:System.IO.EndOfStreamException>  
  
-   <xref:System.IO.FileNotFoundException>  
  
-   <xref:System.IO.FileLoadException>  
  
-   <xref:System.IO.PathTooLongException>  
  
## 请参阅  
 <xref:System.IO.IOException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [NOTINBUILD 如何：创建 CLR 控制台应用程序](http://msdn.microsoft.com/zh-cn/b8af4197-e65f-4b17-b18e-b9e92965d026)