---
title: "关于异常的疑难解答：System.IO.FileNotFoundException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "FileNotFoundException 类"
  - "System.IO.FileNotFoundException 异常"
ms.assetid: 6e5ab395-7c81-434e-835f-0fc792b9149d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.IO.FileNotFoundException
如果尝试访问磁盘上不存在的文件或目录，则会引发 <xref:System.IO.FileNotFoundException> 异常。  
  
## 相关提示  
 **验证文件是否存在于指定位置。**  
 如果文件不存在，则会引发此异常。 有关详细信息，请参阅<xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A>。  
  
 **使用相对路径时，请确保当前目录是正确的。**  
 如果当前目录不正确，相对路径也会不正确。  
  
## 请参阅  
 <xref:System.IO.FileNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)