---
title: "ICanHandleException::CanHandleException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ICanHandleException.CanHandleException
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ICanHandleException::CanHandleException"
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ICanHandleException::CanHandleException
确定脚本引擎的调用方是否可以处理指定的异常。  
  
## 语法  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### 参数  
 `pExcepInfo`  
 \[out\]一个指向包含报告的信息的 `EXCEPINFO` 结构的指针是否未找到匹配的异常处理程序。  
  
 `pvar`  
 \[in\]一个值都具有关联的异常，例如 `throw` 语句引发的值。  此参数可以为 `NULL`。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|调用方可以处理异常|  
|`E_FAIL`|调用方不能处理异常。|  
  
## 备注  
 如果对 `IDispatchEx::InvokeEx`的调用或一个类似的方法，导致异常，脚本引擎检查支持 `ICanHandleException` 接口的脚本的调用方链的调用方它意味着它可以处理异常。  如果调用方无法处理异常，脚本引擎将暂停。  
  
## 请参阅  
 [ICanHandleException 接口](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)