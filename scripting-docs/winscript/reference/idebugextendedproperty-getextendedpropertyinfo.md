---
title: "IDebugExtendedProperty::GetExtendedPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExtendedProperty.GetExtendedPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugExtendedProperty::GetExtendedPropertyInfo"
ms.assetid: 56edf538-5082-4653-82b6-e6640d6f61ba
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExtendedProperty::GetExtendedPropertyInfo
获取一个扩展属性的扩展的信息，比更简单的 `IDebugProperty`是更多信息。  
  
## 语法  
  
```  
HRESULT GetExtendedPropertyInfo(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   ExtendedDebugPropertyInfo*  pExtendedPropertyInfo  
);  
```  
  
#### 参数  
 `dwFieldSpec`  
 \[in\]指定定位在 `ExtendedDebugPropertyInfo` 框架将填写字段的EX\_DBGPROP\_INFO\_FLAGS常数。  
  
 `nRadix`  
 \[in\]用于解释任何数字信息基数。  
  
 `pExtendedPropertyInfo`  
 \[in\]返回描述属性的 `ExtendedDebugPropertyInfo` 结构。  
  
## 返回值  
 返回有效的 `HRESULT`，通常 `S_OK`。  
  
## 请参阅  
 [IDebugExtendedProperty 接口](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX\_DBGPROP\_INFO\_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo 结构](../../winscript/reference/extendeddebugpropertyinfo-structure.md)