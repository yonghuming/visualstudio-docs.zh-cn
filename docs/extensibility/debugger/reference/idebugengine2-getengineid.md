---
title: "IDebugEngine2::GetEngineID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::GetEngineID"
helpviewer_keywords: 
  - "IDebugEngine2::GetEngineID"
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::GetEngineID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取调试引擎的 GUID \(DE\)。  
  
## 语法  
  
```cpp#  
HRESULT GetEngineID(   
   GUID* pguidEngine  
);  
```  
  
```c#  
int GetEngineID(   
   out Guid pguidEngine  
);  
```  
  
#### 参数  
 `pguidEngine`  
 \[out\] 返回 DE 的 GUID。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 典型的 GUID 的一些示例为 `guidScriptEng`、 `guidNativeEng`或 `guidSQLEng`。  新的调试引擎会创建它们确定自己的 GUID。  
  
## 示例  
 下面的示例演示如何执行简单的 `CEngine` 对象的方法实现 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 接口。  
  
```cpp#  
HRESULT CEngine::GetEngineId(GUID *pguidEngine){    
   if (pguidEngine) {    
      // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.    
      // Other languages would require their own guidDifferentEngine to be  
      //defined in the Batdbg.idl file.    
      *pguidEngine = guidBatEng;    
      return NOERROR; // This is typically S_OK.    
   } else {  
      return E_INVALIDARG;    
   }    
}    
```  
  
## 请参阅  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)