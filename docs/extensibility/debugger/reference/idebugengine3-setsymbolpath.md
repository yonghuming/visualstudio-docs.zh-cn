---
title: "IDebugEngine3::SetSymbolPath | Microsoft Docs"
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
  - "IDebugEngine3::SetSymbolPath"
helpviewer_keywords: 
  - "IDebugEngine3::SetSymbolPath"
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

设置中搜索调试符号的路径或路径。  
  
## 语法  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```c#  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|`szSymbolSearchPath`|\[in\] 字符串包含符号搜索路径或路径。  请参见 “备注”了解详细信息。  不能为 null。|  
|`szSymbolCachePath`|\[in\] 字符串包含可缓存符号的本地路径。  不能为 null。|  
|`Flags`|\[in\] 不使用;始终设置为 0。|  
  
## 返回值  
 如果成功，则返回 S\_OK;否则返回错误代码。  
  
## 备注  
 该字符串`szSymbolSearchPath` 是一个或多个路径列表，由分号分隔，搜索符号。  这些路径可以是本地路径、 UNC 路径样式或 URL。  这些路径可能也不同类型的组合。  如果是 UNC 路径 \(例如， \\\\Symserver\\Symbols\)，然后调试引擎应确保路径是否到符号服务器，并应能够将该服务器加载符号，缓存它们在 `szSymbolCachePath`指定的路径。  
  
 符号路径可能还包含一个或多个缓存位置。  缓存按优先级顺序，具有最高优先级的缓存和分隔的 \* 符号最前面。  例如：  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) 方法执行符号的实际负载。  
  
## 请参阅  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)