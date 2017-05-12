---
title: "IEnumDebugStackFrames::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Next
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Next"
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Next
检索枚举序列中指定数目的段。  
  
## 语法  
  
```  
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### 参数  
 `celt`  
 \[in\]要检索的段的数目。  
  
 `prgdsfd`  
 \[in\]返回表示检索的段的数组 `DebugStackFrameDescriptor` 接口。  
  
 `pceltFetched`  
 \[in\]枚举数获取的段的实际数目。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法检索段指定数目的枚举序列的。  
  
## 请参阅  
 [IEnumDebugStackFrames 接口](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [DebugStackFrameDescriptor 结构](../../winscript/reference/debugstackframedescriptor-structure.md)