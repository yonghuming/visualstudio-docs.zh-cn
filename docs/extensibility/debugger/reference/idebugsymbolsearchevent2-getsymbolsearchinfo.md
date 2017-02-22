---
title: "IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Docs"
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
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

调用事件处理程序检索有关符号加载的结果进程。  
  
## 语法  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```c#  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### 参数  
 `pModule`  
 \[out\] 表示符号加载的模块的 IDebugModule3 对象。  
  
 `pbstrDebugMessage`  
 \[in, out\] 返回包含从模块的字符串的所有错误消息。  如果没有错误，则此字符串将包含模块名称，但决不能为 null。  
  
> [!NOTE]
>  \[c\+\+\] `pbstrDebugMessage` 不是 `NULL` ，并且必须释放与 `SysFreeString`。  
  
 `pdwModuleInfoFlags`  
 \[out\] 标志的组合。指示任何符号是否的 [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) 枚举的加载的。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  
  
## 备注  
 当处理程序接收 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) 事件时，在尝试加载模块后调试符号，该处理程序可以调用 thismethod 确定该负载的结果。  
  
## 请参阅  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)