---
title: "IJsDebugDataTarget::ReadNullTerminatedString 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadNullTerminatedString
apilocation: jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadNullTerminatedString 方法
从目标读取指定数目的字符。  
  
## 语法  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### 参数  
 `address`  
 \[in\] 要从中读取的地址。  
  
 `characterSize`  
 \[in\] 字符串中每个字符的大小  
  
 `maxCharacters`  
 \[in\] 读取的最大字符数。maxCharacters 应是合理的。  只要请求的内存多于 128MB，该请求就会失败。如果该字符串大于 maxCharacters，结果字符串将在 maxCharacters 后被截断。  
  
 `pString`  
 \[out\] 从目标读取的 BSTR。  
  
## 返回值  
  
## 备注  
 如果截断，则返回 S\_FALSE。  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)