---
title: "IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::CreateInstanceInServer"
helpviewer_keywords: 
  - "IDebugCoreServer3::CreateInstanceInServer"
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

创建一个调试引擎的实例上的。  
  
## 语法  
  
```cpp#  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```c#  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### 参数  
 `szDll`  
 \[in\] 实现 CLSID 的 dll 的路径。 `clsidObject` 参数指定了。  如果这是 `NULL`，则 COM 的 `CoCreateInstance` 函数调用。  
  
 `wLangId`  
 \[in\] 调试引擎的区域设置。  ，如果 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) 方法不应调用，这可能是 0。  
  
 `clsidObject`  
 \[in\] 创建的调试引擎的 CLSID。  
  
 `riid`  
 \[in\] 检索的特定接口的接口 ID 从类的对象。  
  
 `ppvObject`  
 \[out\] 从实例化的对象的 `IUnknown` 接口。  转换或封送到所需接口将此对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)