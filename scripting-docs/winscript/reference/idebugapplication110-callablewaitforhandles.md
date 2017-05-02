---
title: "IDebugApplication110::CallableWaitForHandles | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110::CallableWaitForHandles"
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110::CallableWaitForHandles
等待任何指定的句柄信号，则允许跨线程调用时发送到该线程。  必须从调试器线程调用此方法。  
  
> [!IMPORTANT]
>  [IDebugApplication110 接口](../../winscript/reference/idebugapplication110-interface.md) 由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 语法  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
  
```  
  
#### 参数  
 `handleCount`  
 等待句柄的数量。  
  
 `pHandles`  
 设置处理等待。  
  
 `pIndex`  
 当HRESULT值是S\_OK，索引到终止句柄的 `pHandles` 中。  
  
## 请参阅  
 [IDebugApplication110 接口](../../winscript/reference/idebugapplication110-interface.md)