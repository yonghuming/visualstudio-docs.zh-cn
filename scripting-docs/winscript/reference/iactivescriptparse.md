---
title: "IActiveScriptParse | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParse 接口"
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse
如果Windows脚本引擎允许原始的文本代码scriptlets添加到脚本或允许表达式文本在运行时计算，它实现 `IActiveScriptParse` 接口。  对于没有独立创作环境，例如VBScript的解释的脚本语言，这会提供备用结构\(除了 `IPersist*`\)获取脚本代码添加到脚本引擎和附加脚本片段到各种对象事件。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|初始化脚本引擎。|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|添加一个代码scriptlet到脚本。|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|分析特定代码scriptlet，添加声明添加到命名空间和计算代码根据需要。|  
  
## 请参阅  
 [活动脚本接口](../../winscript/reference/active-script-interfaces.md)