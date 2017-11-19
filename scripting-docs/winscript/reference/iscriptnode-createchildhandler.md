---
title: "IScriptNode::CreateChildHandler |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.CreateChildHandler
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff2ba40d1570e23f0256bd34ca8aff0f8d77ce5c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
添加的子实例作为的 scriptlet `IScriptNode`。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `pszDefaultName`  
 [in]要将与 scriptlet 相关联的默认名称的地址。  
  
 `prgpszNames`  
 [在 size_is (`cpszNames`)] 从主机上的完全限定名称的标识符的列表。  
  
 `cpszNames`  
 [in]中的标识符的数量`prgpszNames`参数。  
  
 `pszEvent`  
 [in]标识与 scriptlet 关联的事件名称的缓冲区地址。  
  
 `pszDelimiter`  
 [in]结束的脚本块分隔符的地址。 有关分析过程中，主机通常使用分隔符 （如两个单引号），来检测脚本块的末尾。  
  
 分隔符使预处理创作引擎脚本。 例如，对于引擎可能与用作分隔符两个单引号替换单引号。 引擎确定如何使用分隔符。  
  
 如果无分隔符用于标识脚本块的末尾，则设置为 NULL。  
  
 `ptiSignature`  
 [in]函数对象的类型信息。  
  
 `iMethodSignature`  
 [in]中的函数的索引`ITypeInfo``ptiSignature`参数。  
  
 `isn`  
 [in]父代中的子级的索引。  
  
 `dwCookie`  
 [in]应用程序定义的一个值，用于将条目与该主机对象相关联。  
  
 `ppse`  
 [out]接收指向的变量的地址`IScriptEntry`接口的子实例。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 Scriptlet 指定事件处理程序。 此方法创建 scriptlet，如果它由`IScriptNode`表示 Web 页的对象。 如果它由其他接口进行调用，则此方法不会成功。  
  
## <a name="see-also"></a>另请参阅  
 [IScriptNode 接口](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)