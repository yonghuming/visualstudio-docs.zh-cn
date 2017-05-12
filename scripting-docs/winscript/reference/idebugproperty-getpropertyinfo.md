---
title: "IDebugProperty::GetPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetPropertyInfo"
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetPropertyInfo
获取描述一个方法或索引属性 `IDebugProperty` 的值。  
  
## 语法  
  
```  
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGS dwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### 参数  
 `dwFields`  
 \[in\]指定定位在 `DebugPropertyInfo` 框架将填写字段的 `DBGPROP_INFO_FLAGS` 常数。  
  
 `nRadix`  
 \[in\]用于设置任何数值信息基数。  
  
 `pPropertyInfo`  
 \[in\]返回描述属性的 `DebugPropertyInfo` 结构。  
  
## 返回值  
 返回有效的 `HRESULT`，通常 `S_OK`。  
  
## 请参阅  
 [IDebugProperty 接口](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [DebugPropertyInfo 结构](../../winscript/reference/debugpropertyinfo-structure.md)