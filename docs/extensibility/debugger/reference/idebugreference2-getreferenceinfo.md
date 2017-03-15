---
title: "IDebugReference2::GetReferenceInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::GetReferenceInfo"
helpviewer_keywords: 
  - "IDebugReference2::GetReferenceInfo"
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::GetReferenceInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取描述引用的 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 结构。  保留供将来使用。  
  
## 语法  
  
```cpp#  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```c#  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### 参数  
 `dwFields`  
 \[in\] 确定在 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 框架将填写字段标志的组合。 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) 枚举的。  
  
 `nRadix`  
 \[in\] 格式化任何数值信息基数。  
  
 `dwTimeout`  
 \[in\] 最长时间，以毫秒为单位，在返回等待来自此方法。  使用 `INFINITE` 会无限期地等待。  
  
 `rgpArgs`  
 \[in\] 数组 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 对象。  保留供将来使用;设置为空值。  
  
 `dwArgCount`  
 \[in\] 数字引用在 `rgpArgs` 数组的参数。  保留供将来使用;设置为 0。  
  
 `pReferenceInfo`  
 \[out\] 使用属性的说明填充的 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 结构。  
  
## 返回值  
 始终返回 `E_NOTIMPL`。  
  
## 请参阅  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)