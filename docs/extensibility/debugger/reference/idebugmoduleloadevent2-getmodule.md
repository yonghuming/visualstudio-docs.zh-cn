---
title: "IDebugModuleLoadEvent2::GetModule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModuleLoadEvent2::GetModule"
helpviewer_keywords: 
  - "IDebugModuleLoadEvent2::GetModule"
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取加载或卸载的模块。  
  
## 语法  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```c#  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### 参数  
 `pModule`  
 \[out\] 返回表示模块加载或卸载的 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 对象。  
  
 `pbstrDebugMessage`  
 \[in, out\] 返回描述此事件的可选消息。  如果此参数是一个空值，消息未请求。  
  
 `pbLoad`  
 \[in, out\] 非零 \(`TRUE`\)，如果模块加载和零 \(0\)`FALSE`\)，如果卸载模块。  如果此参数是一个空值，状态未请求。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)