---
title: "IDebugApplication::StepOutComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.StepOutComplete
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::StepOutComplete"
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::StepOutComplete
通知处理调试管理器一个语言引擎在单个步骤中模式下将返回到其调用方。  
  
## 语法  
  
```  
HRESULT StepOutComplete();  
```  
  
#### 参数  
 此方法没有参数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 这些返回其调用方之前，语言引擎在单个步骤中模式下调用此方法。  进程内调试管理器使用此机会通知其他脚本引擎它们应中断在第一个机会。  此方法是跨语言步进模式的实现方式。  
  
## 请参阅  
 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)