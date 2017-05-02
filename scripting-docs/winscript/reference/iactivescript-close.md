---
title: "IActiveScript::Close | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Close
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Close"
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::Close
使脚本引擎丢弃所有当前加载的脚本，丢失它们必须其他对象的其状态和释放任何接口指针，因此输入一个关闭状态。  事件接收器、立即执行的脚本文本和正在进行的宏调用在状态转换\(使用 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) 之前退出运行的脚本线程\)。  在释放接口避免循环引用问题之前，必须先创建的宿主调用此方法。  
  
## 语法  
  
```  
HRESULT Close(void);  
```  
  
## 返回值  
 返回下列值之一：  
  
|值|含义|  
|-------|--------|  
|`S_OK`|成功。|  
|`E_UNEXPECTED`|调用非预期\(例如，脚本引擎已处于已关闭状态\)。|  
|`OLESCRIPT_S_PENDING`|方法成功排入队列，但是，该状态未更改。  在状态发生更改时，网站将调用 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 方法。|  
|`S_FALSE`|方法成功的，但是，该脚本已关闭。|  
  
## 请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)