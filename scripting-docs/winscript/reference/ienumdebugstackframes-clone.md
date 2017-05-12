---
title: "IEnumDebugStackFrames::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Clone
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Clone"
ms.assetid: 9d9e01a3-0be3-4336-832a-f065af388571
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Clone
创建与当前枚举器包含相同状态的一个枚举器。  
  
## 语法  
  
```  
HRESULT Clone(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### 参数  
 `ppedsf`  
 \[in\]返回枚举数的克隆的 `IEnumDebugStackFrames`接口。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法创建包含状态和枚举当前枚举数相同的枚举数。  
  
## 请参阅  
 [IEnumDebugStackFrames 接口](../../winscript/reference/ienumdebugstackframes-interface.md)