---
title: "IActiveScriptAuthor::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddTypeLib"
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptAuthor::AddTypeLib
添加一个类型库到脚本的命名空间。  
  
## 语法  
  
```  
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### 参数  
 `rguidTypeLib`  
 \[in\] CLSID \(选件类标识符\)类型要添加的库。  
  
 `dwMajor`  
 \[in\]主版本号。  
  
 `dwMinor`  
 \[out\]一次版本号。  
  
 `dwFlags`  
 \[in\] 未使用。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法调用 `LoadTypeLib` 加载该类型库。  在成功，此方法调用 `IActiveScriptAuthor::AddNamedItem` 添加类型信息。  
  
## 请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](http://msdn.microsoft.com/zh-cn/155b48e5-5438-409e-9342-630a6a500f60)