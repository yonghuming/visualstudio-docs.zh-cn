---
title: "IRemoteDebugApplication::ResumeFromBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.ResumeFromBreakPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::ResumeFromBreakPoint"
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::ResumeFromBreakPoint
继续当前在断点的应用程序。  
  
## 语法  
  
```  
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### 参数  
 `prptFocus`  
 \[in\]对单步执行模式，将会单步模式的影响的线程。  
  
 `bra`  
 \[in\]执行的操作在还原应用程序。  
  
 `era`  
 \[in\]执行的操作。由于错误，应用程序终止的大小写。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法继续当前在断点的应用程序。  
  
## 请参阅  
 [IRemoteDebugApplication 接口](../../winscript/reference/iremotedebugapplication-interface.md)   
 [BREAKRESUMEACTION 枚举](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION 枚举](../../winscript/reference/errorresumeaction-enumeration.md)