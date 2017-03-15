---
title: "关于异常的疑难解答：Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
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
  - "Microsoft.VisualStudio.Tools.Applications.Runtime.ControlNotFoundException 异常"
ms.assetid: d780b8cc-c3f1-45ed-8f8e-3f8728a4b770
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException
当 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> 无法使用指定的格式分析行时，将引发 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> 异常。  
  
 异常对象的 `Error Line` 属性包含导致错误的行的文本。  
  
## 相关提示  
 **请检查以确保 TextFieldType 和 Delimiter 的参数定义是正确的**  
 `TextFieldType`（分隔或固定宽度）必须与文件的格式相匹配。 如果 `TextFieldType` 为 `FixedWidth`，请检查 `FieldWidths` 属性的设置是否正确。 如果 `TextFieldType` 为 `Delimited`，请检查 `Delimiters` 属性的设置是否正确。  
  
## 请参阅  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>   
 [使用 TextFieldParser 对象分析文本文件](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object)   
 [如何：读取逗号分隔的文本文件](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [如何：读取固定宽度的文本文件](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)