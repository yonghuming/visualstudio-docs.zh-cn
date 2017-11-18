---
title: "IActiveScriptAuthor::GetEventHandler |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetEventHandler
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b09f900162b6dba82696c946b53ab131691530c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
返回具有指定的属性的 scriptlet。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pdisp`  
 [in]`IDispatch`对象对应于`NamedItem`scriptlet 所附加到。  
  
 `pszItem`  
 [in]在主机中的完全限定的 scriptlet 名称的顶级标识符的缓冲区地址。  
  
 `pszSubItem`  
 [in]在主机中的完全限定的 scriptlet 名称的第二级别标识符的缓冲区地址。 如果名称包含仅一个级别，则设置为 NULL。  
  
 `pszEvent`  
 [in]包含事件名称的缓冲区的地址。 Scriptlet 是此事件的事件处理程序。  
  
 `ppse`  
 [out]接收指向的变量的地址`IScriptEntry`的 scriptlet 具有指定的属性的接口。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)