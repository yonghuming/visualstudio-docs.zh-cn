---
title: "IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2::ReloadSymbols"
helpviewer_keywords: 
  - "IDebugModule2::ReloadSymbols 方法"
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

过时。  不要使用。  重新加载此模块的符号。  
  
## 语法  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```c#  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### 参数  
 `pszUrlToSymbols`  
 \[in\] 符号存储区的路径。  
  
 `pbstrDebugMessage`  
 \[out\] 返回一个信息性消息，例如状态或错误消息，在模块窗口的模块名称右侧显示。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  调试引擎应始终返回 `E_FAIL`。  
  
## 备注  
 它不再受支持。  执行 [LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md) 方法。  
  
## 请参阅  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md)