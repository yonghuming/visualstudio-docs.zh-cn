---
title: "IDebugSymbolProviderDirect::GetCurrentModulesInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect::GetCurrentModulesInfo"
  - "GetCurrentModulesInfo"
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugSymbolProviderDirect::GetCurrentModulesInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索有关模块的符号信息在组中。  
  
## 语法  
  
```cpp#  
HRESULT GetCurrentModulesInfo(  
   unsigned long * pCount,  
   GUID *          ppGuids,  
   DWORD *         pADIds,  
   DWORD *         pCurrentState,  
   IUnknown **     ppCDModItfs  
);  
```  
  
```c#  
int GetCurrentModulesInfo(  
   uint       pCount,  
   Guid       ppGuids,  
   uint       pADIds,  
   uint       pCurrentState,  
   out object ppCDModItfs  
);  
```  
  
#### 参数  
 `pCount`  
 \[in\] 模块数。 `ppGuids` 数组。  
  
 `ppGuids`  
 \[in\] 对包含模块的唯一标识符。  
  
 `pADIds`  
 \[in\] 应用程序域的标识符。  
  
 `pCurrentState`  
 \[in\] 符号组的当前状态。  
  
 `ppCDModItfs`  
 \[out\] 返回在符号组中包含模块的对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)