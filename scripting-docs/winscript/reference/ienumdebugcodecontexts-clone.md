---
title: "IEnumDebugCodeContexts::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugCodeContexts.Clone
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugCodeContexts::Clone"
ms.assetid: eaad6af9-4a0a-49c9-8f73-bccaa42b235c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCodeContexts::Clone
创建与当前枚举器包含相同状态的一个枚举器。  
  
## 语法  
  
```  
HRESULT Clone(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### 参数  
 `ppescc`  
 \[in\]返回枚举数的克隆的 `IEnumDebugCodeContexts` 接口。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法创建包含状态和枚举当前枚举数相同的枚举数。  
  
## 请参阅  
 [IEnumDebugCodeContexts 接口](../../winscript/reference/ienumdebugcodecontexts-interface.md)