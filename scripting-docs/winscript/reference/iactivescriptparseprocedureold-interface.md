---
title: "IActiveScriptParseProcedureOld 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld 接口"
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptParseProcedureOld 接口
允许程序的源代码文本可以添加到脚本。  适用于没有独立创作环境，例如VBScript的解释的脚本语言，这会提供一个备选机制\(除了 `IActiveScriptParse` 或 `IPersist*`\)添加脚本程序添加到命名空间。  
  
> [!NOTE]
>  此接口是否决了 `IActiveScriptParseProcedure` 接口。  
  
## 方法  
 除了从 `IUnknown` 继承的方法之外，`IActiveScriptParseProcedureOld` 接口还公开下面的方法。  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|分析特定代码程序并添加过程到命名空间。|  
  
## 请参阅  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)