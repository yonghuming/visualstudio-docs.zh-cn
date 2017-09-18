---
title: "IDebugCoreServer3::EnableAutoAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
helpviewer_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

启用自动附加指定的调试引擎。  
  
## 语法  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```c#  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### 参数  
 `rgguidSpecificEngines`  
 \[in\] 数组每个的 GUID 调试引擎标记为自动附加。  
  
 `celtSpecificEngines`  
 \[in\] 在 `rgguidSpecificEngines`指定的引擎的数目。  
  
 `pszStartPageUrl`  
 \[in\] 使用的起始 URL，则自动附加时。  
  
 `pbstrSessionID`  
 \[out\] 自动附加会话的 ID。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  错误代码是 `E_AUTO_ATTACH_NOT_REGISTERED`，指示自动附加类工厂未注册。  
  
## 备注  
 当程序与指定的 URL 启动时，指定的调试引擎自动启动并附加。  
  
## 请参阅  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)