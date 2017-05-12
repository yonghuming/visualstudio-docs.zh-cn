---
title: "IDebugApplication::CreateAsyncDebugOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.CreateAsyncDebugOperation
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::CreateAsyncDebugOperation"
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::CreateAsyncDebugOperation
提供对特定同步异步访问调试操作。  
  
## 语法  
  
```  
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### 参数  
 `psdo`  
 \[in\]同步调试操作对象。  
  
 `ppado`  
 \[in\]异步调试操作对象。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法允许语言引擎异步计算表达式，而无需显式与同步调试器线程。  有关更多信息，请参见[IDebugSyncOperation 接口](../../winscript/reference/idebugsyncoperation-interface.md)和 [IDebugAsyncOperation 接口](../../winscript/reference/idebugasyncoperation-interface.md)。  
  
## 请参阅  
 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugSyncOperation 接口](../../winscript/reference/idebugsyncoperation-interface.md)   
 [IDebugAsyncOperation 接口](../../winscript/reference/idebugasyncoperation-interface.md)