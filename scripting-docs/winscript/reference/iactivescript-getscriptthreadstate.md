---
title: "IActiveScript::GetScriptThreadState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadState"
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadState
检索脚本线程的当前状态。  
  
## 语法  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### 参数  
 `stidThread`  
 \[in\]该状态希望线程以下特殊线程标识符的标识符或之一：  
  
|值|含义|  
|-------|--------|  
|SCRIPTTHREADID\_BASE|基本线程;即脚本引擎实例化的线程。|  
|SCRIPTTHREADID\_CURRENT|当前执行线程。|  
  
 `pstsState`  
 \[in\]接收指示线程的状态变量的地址。  状态由 [SCRIPTTHREADSTATE 枚举](../../winscript/reference/scriptthreadstate-enumeration.md) 枚举定义的某个命名常量值表示。  如果此参数不确定当前线程，状态可能在\+任何\+时间更改。  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_POINTER`|无效指针指定了。|  
|`E_UNEXPECTED`|调用非预期\(例如，脚本引擎尚未加载还未初始化\)。|  
  
## 备注  
 此方法可以从非基础线程调用未导致非基础出站承载对象或到 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 接口。  
  
## 请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)