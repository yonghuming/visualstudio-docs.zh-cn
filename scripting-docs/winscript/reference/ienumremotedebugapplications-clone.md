---
title: "IEnumRemoteDebugApplications::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplications.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplications::Clone"
ms.assetid: 762f6dac-1be4-49ec-afda-68c1b29f7a4b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplications::Clone
创建与当前枚举器包含相同状态的一个枚举器。  
  
## 语法  
  
```  
HRESULT Clone(  
   IEnumRemoteDebugApplications**  ppessd  
);  
```  
  
#### 参数  
 `ppessd`  
 \[in\]枚举数的克隆。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法创建包含状态和枚举当前枚举数相同的枚举数。  
  
## 请参阅  
 [IEnumRemoteDebugApplications 接口](../../winscript/reference/ienumremotedebugapplications-interface.md)