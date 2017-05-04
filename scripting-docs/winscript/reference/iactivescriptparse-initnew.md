---
title: "IActiveScriptParse::InitNew | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.InitNew
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_InitNew"
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::InitNew
初始化脚本引擎。  
  
## 语法  
  
```  
HRESULT InitNew(void);  
```  
  
## 返回值  
 返回 `S_OK`，如果成功或 `E_FAIL`，如果错误在初始化时发生。  
  
## 备注  
 才能使用脚本引擎，必须调用以下方法之一: `IPersist*::Load`、 `IPersist*::InitNew`或 `IActiveScriptParse::InitNew`。  此方法的语义与 `IPersistStreamInit::InitNew`相同，此方法调用脚本引擎初始化自身。  请注意无效的调用 `IPersist*::InitNew` 或 `IActiveScriptParse::InitNew` 和 `IPersist*::Load`，也不是它实际多次调用 `IPersist*::InitNew`、 `IActiveScriptParse::InitNew`或 `IPersist*::Load`。  
  
## 请参阅  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)