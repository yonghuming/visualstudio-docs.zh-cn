---
title: "IActiveScript::GetScriptDispatch | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptDispatch
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptDispatch"
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptDispatch
检索方法和属性的 `IDispatch` 接口与当前运行的脚本。  
  
## 语法  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### 参数  
 `pstrItemName`  
 \[in\]包含项目的名称调用方需要将计划的对象缓冲区的地址。  如果此参数是 `NULL`，将调度对象包含作为其成员该脚本和属性定义的所有全局方法。  通过 `IDispatch` 接口和关联的 `ITypeInfo` 接口，宿主可以调用脚本方法或视图和修改脚本变量。  
  
 `ppdisp`  
 \[in\]接收指向该对象变量的地址与脚本的全局方法和属性。  如果脚本引擎不支持这些对象，`NULL` 返回。  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|参数无效。|  
|`E_POINTER`|无效指针指定了。|  
|`E_UNEXPECTED`|调用非预期\(例如，脚本引擎尚未加载还未初始化\)。|  
|`S_FALSE`|脚本引擎不支持计划对象；`ppdisp` 参数设置为NULL。|  
  
## 备注  
 由于方法和属性可通过调用 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) 接口添加，返回的 `IDispatch` 接口可以动态此方法支持新的方法和属性。  同样，那么，当方法和属性添加时，`IDispatch::GetTypeInfo` 方法应返回一个新的，唯一 `ITypeInfo` 接口。  但是，请注意，语言引擎不能更改 `IDispatch` 接口用与以前的所有 `ITypeInfo` 接口不兼容的方法返回的。  例如，这意味着不会重新使用Dispid。  
  
## 请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)