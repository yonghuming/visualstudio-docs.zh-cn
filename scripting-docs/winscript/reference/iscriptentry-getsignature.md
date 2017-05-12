---
title: "IScriptEntry::GetSignature | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetSignature
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetSignature"
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetSignature
返回 `IScriptEntry` 函数对象的类型信息。  
  
## 语法  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### 参数  
 `ppti`  
 \[out\]中键入信息与此 `IScriptEntry` 函数对象。  
  
 `piMethod`  
 \[out\]在 `ITypeInfo` 对象的方法索引。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 使用 [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) 或 [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)，将类型信息。  类型信息可能会根据内部函数表示的项也会发生。  
  
## 请参阅  
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)