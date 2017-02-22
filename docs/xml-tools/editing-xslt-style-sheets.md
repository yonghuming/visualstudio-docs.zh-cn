---
title: "编辑 XSLT 样式表 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 编辑 XSLT 样式表
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML 编辑器还可以用于编辑 XSLT 样式表。可以利用默认的编辑器功能，例如 IntelliSense、大纲、XML 代码段等。此外，还提供了一些新功能，使 XSLT 中的开发更加容易。  
  
## XSLT 功能  
 下表介绍使用 XSLT 样式表时的特定功能。  
  
 **语法着色**  
 XSLT 关键字（例如 `template`、`match` 等）使用“字体和颜色”设置所指定的 XSLT 关键字颜色显示。  
  
 **波浪形下划线**  
 “XML 编辑器”使用已安装的 xslt.xsd 文件验证 XSLT 样式表。验证错误以蓝色的波浪形下划线显示。“XML 编辑器”还在后台编译样式表，并使用相应的波浪形下划线报告编译器错误或警告。  
  
 **对脚本块的支持**  
 XSLT 调试程序支持脚本块中的代码，这样，您可以设置断点并逐行执行脚本块代码。  
  
 **查看 XSLT 输出**  
 可以在“XML 编辑器”中执行 XSL 转换并查看输出。有关更多信息，请参见[如何：在 XML 编辑器中执行 XSLT 转换](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md)。  
  
 **调试 XSLT**  
 可以在“XML 编辑器”中从 XSLT 文件启动 XSLT 调试程序。调试程序支持在 XSLT 文件中设置断点、查看 XSLT 执行状态等。将光标置于 XSLT 变量上，可以显示包含变量值的工具提示。调试程序可以用于调试样式表，也可以用于调试从另一个应用程序调用的已编译 XSLT 转换。有关更多信息，请参见[调试 XSLT](../xml-tools/debugging-xslt.md)。  
  
## 请参阅  
 [XML 编辑器](../xml-tools/xml-editor.md)