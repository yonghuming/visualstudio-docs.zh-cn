---
title: "BREAKRESUMEACTION 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: BREAKRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b830d314b1db40d7b83557d894ad6f8751bdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="breakresumeaction-enumeration"></a>BREAKRESUMEACTION 枚举
描述从断点继续的方法。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|中止应用程序。|  
|BREAKRESUMEACTION_CONTINUE|继续运行。|  
|BREAKRESUMEACTION_STEP_INTO|单步执行过程。|  
|BREAKRESUMEACTION_STEP_OVER|逐过程执行过程。|  
|BREAKRESUMEACTION_STEP_OUT|跳出当前过程。|  
|BREAKRESUMEACTION_IGNORE|继续运行状态。|  
|BREAKRESUMEACTION_STEP_DOCUMENT|进入下一个文档。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)