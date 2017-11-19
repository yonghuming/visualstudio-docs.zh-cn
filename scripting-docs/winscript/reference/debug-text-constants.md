---
title: "DEBUG_TEXT 常量 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5126a9efefaab611cd27d2104c40918f8dc7c7e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debugtext-constants"></a>DEBUG_TEXT 常量
过程中使用[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)。  
  
## <a name="syntax"></a>语法  
  
```  
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>常量  
  
|常量|值|描述|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|指示该文本是而不是语句表达式。 此标志可能会影响某些语言分析文本时的方式。|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|如果返回值可用时，它将使用由调用方。|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|不允许副作用。 如果设置此标志，对表达式求值应更改任何运行时状态。|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|允许文本求值时的断点。 如果未设置此标志，然后将求值的文本时忽略断点。|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|文本的求值时允许错误报告。 如果未设置此标志，然后将不报告错误到主机求值时。|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|指示该表达式将计算为代码上下文，而不是运行该表达式本身。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)