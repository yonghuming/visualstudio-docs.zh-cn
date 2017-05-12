---
title: "IRemoteDebugApplicationThreadEx:EnumGlobalContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThreadEx:EnumGlobalContexts
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThreadEx:EnumGlobalContexts"
ms.assetid: a6c0bc3f-4afc-41e1-b734-06e252c5b171
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IRemoteDebugApplicationThreadEx:EnumGlobalContexts
枚举运行在此线程的所有语言的全局表达式上下文。  
  
## 语法  
  
```  
HRESULT EnumGlobalExpressionContexts(  
   IEnumDebugExpressionContexts**  ppEnum  
);  
```  
  
#### 参数  
 `ppEnum`  
 \[in\]列表运行在此线程的所有语言的全局表达式上下文的枚举器。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注