---
title: "IDebugEngine3::LoadSymbols | Microsoft Docs"
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
  - "IDebugEngine3::LoadSymbols"
helpviewer_keywords: 
  - "IDebugEngine3::LoadSymbols"
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine3::LoadSymbols
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

加载 \(根据需要\) 此调试引擎正在调试的所有模块的符号。  
  
## 语法  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```c#  
int LoadSymbols();  
```  
  
#### 参数  
 无。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则返回错误代码。  
  
## 备注  
 这将加载此调试引擎引用的所有模块的调试符号。  ，仅当用户尚未加载，符号加载。  符号在对 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)的调用中设置的路径来搜索。  
  
## 请参阅  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)