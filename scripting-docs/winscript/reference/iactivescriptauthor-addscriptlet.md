---
title: "IActiveScriptAuthor::AddScriptlet |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b21f906a73a313bf775683ba63738adb25af0007
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
为根级别的子项添加代码 scriptlet`IScriptNode`对象。 在主机，scriptlet 的完全限定的名被允许具有只有两个级别。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pszDefaultName`  
 [in]要将与 scriptlet 相关联的默认名称的地址。  
  
 `pszCode`  
 [in]Scriptlet 文本的地址。  
  
 `pszItemName`  
 [in]在主机中的完全限定的 scriptlet 名称的顶级标识符的缓冲区地址。  
  
 `pszSubItemName`  
 [in]在主机中的完全限定的 scriptlet 名称的第二级别标识符的缓冲区地址。 如果名称包含仅一个级别，则设置为 NULL。  
  
 `pszEventName`  
 [in]包含为其 scriptlet 是一个事件处理程序的事件名称的缓冲区的地址。  
  
 `pszDelimiter`  
 [in]结束的脚本块分隔符的地址。 当`pszCode`分析从文本流中，主机通常使用分隔符 （如两个单引号），来检测脚本块的末尾。 如果分隔符将脚本块的末尾不标记，请将此参数设置为 NULL。  
  
 `dwCookie`  
 [in]应用程序定义的一个值，用于将 scriptlet 与主机对象相关联。  
  
 `dwFlags`  
 [in]未使用。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)