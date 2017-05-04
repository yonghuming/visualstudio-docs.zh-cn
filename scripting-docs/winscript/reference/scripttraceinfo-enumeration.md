---
title: "SCRIPTTRACEINFO 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTTRACEINFO 枚举
表示要跟踪的脚本事件。  使用在 [IActiveScriptSiteTraceInfo::SendScriptTraceInfo 方法](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)。  
  
## 语法  
  
```  
typedef enum tagSCRIPTTRACEINFO {    
    SCRIPTTRACEINFO_SCRIPTSTART = 0,    
    SCRIPTTRACEINFO_SCRIPTEND   = 1,    
    SCRIPTTRACEINFO_COMCALLSTART    = 2,    
    SCRIPTTRACEINFO_COMCALLEND  = 3,    
    SCRIPTTRACEINFO_CREATEOBJSTART  = 4,    
    SCRIPTTRACEINFO_CREATEOBJEND    = 5,    
    SCRIPTTRACEINFO_GETOBJSTART = 6,    
    SCRIPTTRACEINFO_GETOBJEND   = 7,    
} SCRIPTTRACEINFO ;  
```  
  
## 枚举值  
  
|||  
|-|-|  
|SCRIPTTRACEINFO\_SCRIPTSTART|脚本的开头。|  
|SCRIPTTRACEINFO\_SCRIPTEND|结束的脚本。|  
|SCRIPTTRACEINFO\_COMCALLSTART|COM的开始时调用。|  
|SCRIPTTRACEINFO\_COMCALLEND|COM的结尾调用。|  
|SCRIPTTRACEINFO\_CREATEOBJSTART|对象创建开头。|  
|SCRIPTTRACEINFO\_CREATEOBJEND|对象创建的末尾。|  
|SCRIPTTRACEINFO\_GETOBJSTART|GetObject的开始时调用。|  
|SCRIPTTRACEINFO\_GETOBJEND|GetObject的结尾调用。|