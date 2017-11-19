---
title: "SCRIPTTRACEINFO 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc1902b290a8024679cef12d503e94de4923defb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="scripttraceinfo-enumeration"></a>SCRIPTTRACEINFO 枚举
表示正在跟踪的脚本事件。 在中使用[iactivescriptsitetraceinfo:: Sendscripttraceinfo 方法](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>枚举值  
  
|||  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|脚本的开始日期。|  
|SCRIPTTRACEINFO_SCRIPTEND|脚本的末尾。|  
|SCRIPTTRACEINFO_COMCALLSTART|COM 调用的开始日期。|  
|SCRIPTTRACEINFO_COMCALLEND|COM 调用末尾。|  
|SCRIPTTRACEINFO_CREATEOBJSTART|对象创建开始。|  
|SCRIPTTRACEINFO_CREATEOBJEND|对象创建的结尾。|  
|SCRIPTTRACEINFO_GETOBJSTART|GetObject 调用的开始日期。|  
|SCRIPTTRACEINFO_GETOBJEND|GetObject 调用结束。|