---
title: "ERRORRESUMEACTION 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ERRORRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 914c1d7aa4d2935ea94322ebd257f4135d79e9c0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="errorresumeaction-enumeration"></a>ERRORRESUMEACTION 枚举
描述如何从运行时错误继续。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|重新执行语句生成错误。|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|允许处理错误的语言引擎。|  
|ERRORRESUMEACTION_SkipErrorStatement|恢复后生成错误的语句的代码中执行。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)