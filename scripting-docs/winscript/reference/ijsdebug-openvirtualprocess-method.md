---
title: "IJsDebug::OpenVirtualProcess 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebug.OpenVirtualProcess
apilocation: jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebug::OpenVirtualProcess 方法
用于创建新虚拟过程对象的工厂方法。  
  
## 语法  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### 参数  
 `processId`  
 \[in\] 调试器要附加到的进程 ID。  
  
 `runtimeJsBaseAddress`  
 \[in\] JavaScript 运行加载到该目标进程的基址。  
  
 `pDataTarget`  
 \[in\] 提供接口查询进程状态的调试器。  
  
 `ppProcess`  
 \[out\] 新的调试进程对象  
  
## 返回值  
  
## 备注  
 如果 Jscript9diag 和 Jscript9 不匹配，则返回 E\_JsDEBUG\_MISMATCHED\_RUNTIME。  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebug 接口](../../winscript/reference/ijsdebug-interface.md)