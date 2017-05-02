---
title: "JsDebugReadMemoryFlags 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugReadMemoryFlags
apilocation: jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsDebugReadMemoryFlags 枚举
读取内存时用于指定行为的标志。  
  
## 语法  
  
```  
enum JsDebugReadMemoryFlags  
{  
   None = 0,  
   JsDebugAllowPartialRead= 0x1  
} JsDebugReadMemoryFlags;  
```  
  
## 成员  
  
### 值  
  
|名称|描述|  
|--------|--------|  
|`JsDebugAllowPartialRead`|如果只有部分的内存读取成功，指示调用方希望此操作将操作成功。  如果进行了设置，只有当“地址”无效时才会引发 E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS 错误。  如果此标志明确，如果请求的内存的任意部分不可读时，将引发 E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS 错误。|  
|`None`|指示调用方希望 ReadMemory 的默认行为。|  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [Windows 脚本接口参考](../../winscript/reference/windows-script-interfaces-reference.md)