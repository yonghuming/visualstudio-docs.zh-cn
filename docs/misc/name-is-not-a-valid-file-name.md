---
title: "&lt;name&gt; is not a valid file name. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS_E_INVALIDFILENAME"
  - "VS.Message.0x00006A72"
ms.assetid: c5969671-3b64-4854-acb6-328e8a30863f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid file name.
当尝试从“命令”窗口中创建新文件，但文件名中包含不支持的字符时，会发生此错误。  
  
 文件名不能包含下列字符：  
  
-   井号 \(\#\)  
  
-   百分号 \(%\)  
  
-   “and”符 \(&\)  
  
-   星号 \(\*\)  
  
-   竖线 \(&#124;\)  
  
-   反斜杠 \(\\\)  
  
-   冒号 \(:\)  
  
-   双引号 \("\)  
  
-   小于号 \(\<\)  
  
-   大于号 \(\>\)  
  
-   句点 \(.\)  
  
-   问号 \(?\)  
  
-   正斜杠 \(\/\)  
  
-   前导或尾随空格（“”）  
  
-   为 Windows 或 DOS 保留的名称 （nul、aux、con、com1、lpt1 等）  
  
### 更正此错误  
  
-   使用不包含上面列出的字符的新文件名输入命令。  
  
## 请参阅  
 [“新建文件”命令](../ide/reference/new-file-command.md)   
 [Visual Studio 命令](../ide/reference/visual-studio-commands.md)