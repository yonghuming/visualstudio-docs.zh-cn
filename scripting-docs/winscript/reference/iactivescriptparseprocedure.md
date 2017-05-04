---
title: "IActiveScriptParseProcedure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParseProcedure 接口"
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure
如果Windows脚本引擎允许程序的源代码文本可以添加到脚本，它实现 `IActiveScriptParseProcedure` 接口。  对于没有独立创作环境，例如VBScript的解释的脚本语言，这会提供一个结构\(除了 `IActiveScriptParse` 或 `IPersist`外\*\)添加脚本程序添加到命名空间。  
  
## Vtable 顺序中的方法  
  
|||  
|-|-|  
|方法|说明|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|分析特定代码程序并添加过程到命名空间。|  
  
## 请参阅  
 [活动脚本接口](../../winscript/reference/active-script-interfaces.md)