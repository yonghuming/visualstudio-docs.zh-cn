---
title: "IScriptNode:: CreateChildEntry | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode. CreateChildEntry
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildEntry"
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# IScriptNode:: CreateChildEntry
添加 `IScriptEntry`子实例。  
  
## 语法  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### 参数  
 `isn`  
 \[in\]\)的索引父级。  
  
 `dwCookie`  
 \[in\]用于的应用程序定义的值关联子项与宿主对象。  
  
 `pszDelimiter`  
 \[in\]关闭脚本块分隔符的地址。  对分析，宿主通常使用一个分隔符\(例如两个单引号\)，检测末尾的脚本块。  
  
 该分隔符启用生成引擎的脚本提供预处理。  例如，引擎可能具有两个单引号一个单引号用作分隔符。  引擎确定如何使用该分隔符。  
  
 设置为NULL，如果分隔符不指示末尾的脚本块。  
  
 `ppse`  
 \[in\]接收指向该子实例的 `IScriptEntry` 接口变量的地址。  
  
 对一个表示网页的 `IScriptNode` 对象，此参数返回指定脚本块的 `IScriptEntry` 实例。  
  
 对于表示脚本的 `IScriptEntry` 对象块，此参数返回指定函数对象的 `IScriptEntry` 实例。  
  
 为表示函数对象的 `IScriptEntry` 对象，此方法失败。  
  
 为 `IScriptScriptlet` 对象，此方法失败。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 `IScriptNode` 接口表示网页或其组件。  从 `IScriptNode`派生\)的 `IScriptEntry` 接口\(表示任何脚本块或函数对象。  从 `IScriptEntry`派生\)的 `IScriptScriptlet` 接口\(表示事件处理程序。  
  
## 请参阅  
 [IScriptNode 接口](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)