---
title: "IActiveScript::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_AddTypeLib"
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddTypeLib
添加一个类型库到脚本的命名空间。  这类似于C\/C\+\+的 `#include` 指令。  它允许将一组预定义的项\(如类定义、 `typedefs`和要添加的命名常量添加到该运行时环境可用于该脚本。  
  
## 语法  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### 参数  
 `guidTypeLib`  
 \[in\]类型添加库的CLSID。  
  
 `dwMaj`  
 \[in\]主要版本号。  
  
 `dwMin`  
 \[out\]一次版本号。  
  
 `dwFlags`  
 \[in\] 可选标志。  可以是以下操作：  
  
|值|含义|  
|-------|--------|  
|SCRIPTTYPELIB\_ISCONTROL|类型库描述宿主使用的ActiveX控件。|  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|参数无效。|  
|`E_UNEXPECTED`|调用非预期\(例如，脚本引擎尚未加载还未初始化\)。|  
|`TYPE_E_CANTLOADLIBRARY`|一个指定类型库未能加载。|  
  
## 请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)