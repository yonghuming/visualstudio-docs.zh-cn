---
title: "IScriptNode:: CreateChildEntry |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode. CreateChildEntry
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fcc010efe8fcf30a8f467dd94befff54bc5fac5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
添加的子实例`IScriptEntry`。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>参数  
 `isn`  
 [in]父代中的子级的索引。  
  
 `dwCookie`  
 [in]应用程序定义的值，用于将子条目与该主机对象相关联。  
  
 `pszDelimiter`  
 [in]结束的脚本块分隔符的地址。 有关分析过程中，主机通常使用分隔符 （如两个单引号），来检测脚本块的末尾。  
  
 分隔符使创作引擎提供预处理的脚本。 例如，对于引擎可能与用作分隔符两个单引号替换单引号。 引擎确定如何使用分隔符。  
  
 如果分隔符将脚本块的末尾不标记，则设置为 NULL。  
  
 `ppse`  
 [out]接收指向的变量的地址`IScriptEntry`接口的子实例。  
  
 有关`IScriptNode`表示网页上的对象，此参数返回`IScriptEntry`指定的脚本块的实例。  
  
 有关`IScriptEntry`表示脚本块的对象，此参数返回`IScriptEntry`指定的函数对象的实例。  
  
 有关`IScriptEntry`对象，后者表示函数对象，此方法失败。  
  
 有关`IScriptScriptlet`对象，此方法失败。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 `IScriptNode`接口表示某个网页或其元素。 `IScriptEntry`接口 (派生自`IScriptNode`) 表示脚本块或函数对象。 `IScriptScriptlet`接口 (派生自`IScriptEntry`) 表示一个事件处理程序。  
  
## <a name="see-also"></a>另请参阅  
 [IScriptNode 接口](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)