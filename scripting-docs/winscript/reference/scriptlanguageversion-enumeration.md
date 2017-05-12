---
title: "SCRIPTLANGUAGEVERSION 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTLANGUAGEVERSION 枚举
指定可的脚本版本。  
  
## 语法  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION  
{  
    SCRIPTLANGUAGEVERSION_DEFAULT = 0,  
    SCRIPTLANGUAGEVERSION_5_7  = 1,  
    SCRIPTLANGUAGEVERSION_5_8  = 2,  
    SCRIPTLANGUAGEVERSION_MAX  = 255  
} SCRIPTLANGUAGEVERSION ;  
  
```  
  
## 枚举值  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION\_DEFAULT|默认版本。  整数值为0。|  
|SCRIPTLANGUAGEVERSION\_5\_7|脚本5.7版的Windows。  整数值为1。|  
|SCRIPTLANGUAGEVERSION\_5\_8|脚本5.8版的Windows。  整数值为2。|  
|SCRIPTLANGUAGEVERSION\_MAX|最大版本。  整数值为255。|  
  
## 请参阅  
 [活动脚本常量、枚举和错误代码](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)