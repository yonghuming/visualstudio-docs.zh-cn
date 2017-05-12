---
title: "IScriptEntry::SetSignature | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetSignature
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetSignature"
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::SetSignature
设置 `IScriptEntry` 函数对象的类型信息。  
  
## 语法  
  
```  
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### 参数  
 `pti`  
 \[in\]类型信息。  
  
 `iMethod`  
 \[out\]在 `ITypeInfo` 对象的方法索引。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 使用 `IScriptEntry::SetSignature` 或 [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)，将类型信息。  类型信息可能会根据内部函数表示的项也会发生。  
  
## 请参阅  
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)