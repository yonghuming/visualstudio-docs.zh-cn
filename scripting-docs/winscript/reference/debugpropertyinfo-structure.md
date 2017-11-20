---
title: "DebugPropertyInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9baade1a742a06c952906c05c574e752806bc9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo 结构
描述一个对象具有名称、 类型和值的层次结构性质。 它用于描述的调试属性的本地变量、 参数、 监视变量和表达式，并注册。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>成员  
 dwValidFields  
 枚举的数据类型，用于指定哪些字段进行初始化。  
  
 bstrName  
 上下文中的属性名称。  
  
 bstrType  
 属性类型，作为格式字符串。  
  
 bstrValue  
 格式化字符串形式的属性值。  
  
 bstrFullName  
 属性的完整名称。  
  
 dwAttrib  
 指定调试属性特性的标志的枚举。  
  
 pDebugProp  
 `IDebugProperty`所描述的信息在此`DebugPropertyInfo`结构。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProperty 接口](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)