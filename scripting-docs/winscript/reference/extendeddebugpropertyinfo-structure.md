---
title: "ExtendedDebugPropertyInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ExtendedDebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee06b0ace93f068e0530a3aa62b8c28d11069f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo 结构
扩展`DebugPropertyInfo`与其他成员，以鉴定扩展的属性的结构。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>成员  
 `dwValidFields`  
 枚举的数据类型，用于指定哪些字段进行初始化。  
  
 `bstrName`  
 上下文中的属性名称。  
  
 `bstrType`  
 格式化字符串形式的属性类型。  
  
 `bstrValue`  
 格式化字符串形式的属性值。  
  
 `bstrFullName`  
 属性的完整名称。  
  
 `dwAttrib`  
 指定调试属性特性的标志的枚举。  
  
 `pDebugProp`  
 `IDebugProperty`对应于此对象`ExtendedDebugPropertyInfo`。  
  
 `nDISPID`  
 调度 id 中。  
  
 `nType`  
 扩展的属性类型。  
  
 `varValue`  
 如果可以满足变体扩展的属性的值。  
  
 `plbValue`  
 属性值的实际数据字节数。  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty`对应于此对象`ExtendedDebugPropertyInfo`。  
  
## <a name="see-also"></a>另请参阅  
 [DebugPropertyInfo 结构](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty 接口](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty 接口](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)