---
title: "编码和换行符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.Encoding"
helpviewer_keywords: 
  - "编辑器, 分行符"
  - "编码"
  - "换行符"
  - "分行符"
  - "Visual Studio, 编码"
  - "Visual Studio, 换行符"
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# 编码和换行符
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 Visual Studio 中，您可以使用**文件\/高级保存选项**想要的设置，以确定字符的分行符的类型。  您还可以更改的文件的编码，使用相同的设置。  
  
> [!NOTE]
>  如果您拥有某些类型的开发设置 （Visual Basic，F\# 中，Web 开发） 您可能看不到**高级保存选项**在菜单上。  若要更改您的设置 （例如为常规），请打开**工具 \/ 导入和导出设置**。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 在 Visual Studio 中的下列字符解释为换行符：  
  
-   CRLF：回车符 \+ 换行符，对应的 Unicode 字符为 000 D \+ 000A  
  
-   LF：换行符，对应的 Unicode 字符为 000A  
  
-   NEL：下一行，对应的 Unicode 字符为 0085  
  
-   LS：行分隔符，对应的 Unicode 字符为 2028年  
  
-   PS：段落分隔符，对应的 Unicode 字符为 2029年  
  
 从其他应用程序复制的文本将保持原始编码和换行符）。  例如，当您从记事本复制文本并将其粘贴到一个文本文件，在 Visual Studio 中，文本具有相同的设置，它在记事本中。  
  
 当打开具有不同的行分隔符字符的文件时，您可能会看到一个对话框，询问是否应规范化不一致的分行符和换行符，若要选择哪一种。