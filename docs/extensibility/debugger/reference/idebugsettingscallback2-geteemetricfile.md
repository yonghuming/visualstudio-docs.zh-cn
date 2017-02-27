---
title: "IDebugSettingsCallback2::GetEEMetricFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetEEMetricFile"
ms.assetid: 3a0bf9e5-bbd2-4d15-840d-8244732787fc
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2::GetEEMetricFile
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索给定的表达式计算器指标文件名称或指标。  
  
## 语法  
  
```cpp#  
HRESULT GetEEMetricFile(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   BSTR*   pbstrValue  
);  
```  
  
```c#  
private int GetEEMetricFile(  
   ref Guid   guidLang,  
   ref Guid   guidVendor,  
   string     pszMetric,  
   out string pbstrValue  
);  
```  
  
#### 参数  
 `guidLang`  
 \[in\] 编程语言的唯一标识符。  
  
 `guidVendor`  
 \[in\] 供应商的唯一标识符。  
  
 `pszMetric`  
 \[in\] 名称的指标。  
  
 `pbstrValue`  
 \[out\] 返回指标文件的内容作为字符串。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)