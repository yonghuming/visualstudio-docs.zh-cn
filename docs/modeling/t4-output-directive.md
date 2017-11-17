---
title: "T4 输出指令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: "4"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: bf96406356799a0953ee34eb736266267fe74510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="t4-output-directive"></a>T4 输出指令
在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]文本模板，`output`指令用于定义的文件扩展名和编码的转换后的文件。  
  
 例如，如果你[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目包含一个名为的模板文件**MyTemplate.tt**其中包含以下指令：  
  
 `<#@output extension=".cs"#>`  
  
 然后[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]将生成名为的文件**MyTemplate.cs**  
  
 运行时（预处理）文本模板中不需要 `output` 指令。 相反，应用程序通过调用 `TextTransform()` 来获取已生成的字符串。 有关详细信息，请参阅[使用 T4 文本模板的运行时文本生成](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
## <a name="using-the-output-directive"></a>使用输出指令  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 每个文本模板中不应该有多个 `output`。  
  
## <a name="extension-attribute"></a>扩展特性  
 指定生成的文本输出文件的文件扩展名。  
  
 默认值是**.cs**  
  
 示例：  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 可接受的值：  
 任何有效的文件扩展名。  
  
## <a name="encoding-attribute"></a>编码属性  
 指定生成输出文件时要使用的编码。 例如：  
  
 `<#@ output encoding="utf-8"#>`  
  
 默认值为文本模板文件使用的编码。  
  
 可接受的值：  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0`（系统默认）  
  
 一般情况下，可以使用 WebName 字符串或 <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> 返回的任一编码的 CodePage 编号。