---
title: "IActiveScriptAuthor::GetLanguageFlags |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetLanguageFlags
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6137f1cd77d2f305a9ff9d51ac49c214e4c4237b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
返回语言信息。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pgrfasa`  
 [out]包含语言信息的标志。 可以是以下值的组合：  
  
|常量|值|描述|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|从 0x0001|语言由创作而不是应用程序引擎的脚本首选脚本事件处理程序创建。|  
|fasaSupportInternalHandler|0x0002|语言支持创作引擎脚本所创建的脚本事件处理程序。|  
|fasaCaseSensitive|0x0004|脚本语言是区分大小写。|  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 如果创作引擎脚本管理事件处理程序，应调用你的应用程序`CreateChildHandler`从`IScriptEntry`对象。 这将创建`IScriptScriptlet`对应于事件处理程序的对象。 该引擎还将事件处理程序添加到脚本条目。 事件处理程序是一个空的函数，其中包含指定的签名信息。  
  
 如果你的应用程序管理事件处理程序，则应调用`CreateChildHandler`从`IScriptNode`表示事件处理程序 scriptlet 的对象。 这将创建`IScriptScriptlet`与事件处理程序 scriptlet 相关联的对象。 应用程序还必须将空函数为事件添加到新的处理程序或现有`IScriptEntry`对象。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)