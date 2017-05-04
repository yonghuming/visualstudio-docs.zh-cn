---
title: "DEBUG_TEXT 常量 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# DEBUG_TEXT 常量
使用在 [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)过程。  
  
## 语法  
  
```  
typedef DWORD DEBUG_TEXT;  
  
```  
  
## 常量  
  
|常量|值|描述|  
|--------|-------|--------|  
|DWORD DEBUG\_TEXT\_ISEXPRESSION|0x00000001|指示该文本是表达式与语句相对。  此标记会影响该文本由某些语言分析的方式。|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|如果返回值可用，它将被调用方使用。|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|不要允许副作用。  如果此标志设置，该表达式的计算不应更改运行时状态。|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|在文本的计算时允许断点。  如果此未设置任何标志，则断点在文本的计算时将被忽略。|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|在文本的计算时允许错误报告。  如果此未设置任何标志，则会显示错误不会将托管报告在计算时。|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|指示该表达式将计算为代码上下文 \(而非运行该表达式。|  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)