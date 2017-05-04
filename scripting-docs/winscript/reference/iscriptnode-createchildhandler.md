---
title: "IScriptNode::CreateChildHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.CreateChildHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildHandler"
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IScriptNode::CreateChildHandler
添加一scriptlet作为 `IScriptNode`的子实例。  
  
## 语法  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### 参数  
 `pszDefaultName`  
 \[in\]关联的默认名称的地址与scriptlet。  
  
 `prgpszNames`  
 \[in，size\_is \(`cpszNames`\)\]标识符的列表从完全限定名的宿主。  
  
 `cpszNames`  
 \[in\]标识符数。`prgpszNames` 参数的。  
  
 `pszEvent`  
 \[in\]标识事件名称的缓冲区地址与scriptlet。  
  
 `pszDelimiter`  
 \[in\]关闭脚本块分隔符的地址。  对分析，宿主通常使用一个分隔符\(例如两个单引号\)，检测末尾的脚本块。  
  
 该分隔符由生成引擎的脚本启用预处理。  例如，引擎可能具有两个单引号一个单引号用作分隔符。  引擎确定如何使用该分隔符。  
  
 设置为NULL，如果分隔符不用于标识末尾的脚本块。  
  
 `ptiSignature`  
 \[in\]函数对象的类型信息。  
  
 `iMethodSignature`  
 \[in\]功能的索引。`ITypeInfo``ptiSignature` 参数的。  
  
 `isn`  
 \[in\]\)的索引父级。  
  
 `dwCookie`  
 \[in\]用于将项与宿主对象的应用程序定义的值。  
  
 `ppse`  
 \[in\]接收指向该子实例的 `IScriptEntry` 接口变量的地址。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 scriptlet指定事件处理程序。  此方法将创建一个scriptlet，则由表示网页的 `IScriptNode` 对象调用。  如果它由其他接口，调用此方法不成功。  
  
## 请参阅  
 [IScriptNode 接口](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)