---
title: "IActiveScriptAuthor::GetInfoFromContext |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetInfoFromContext
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27c13dbe51bb1150554275b5fbeacd00be2e445f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
返回类型的代码块中的信息和给定的字符的定位点位置。 IntelliSense、 全局列表和参数提示，本文提供有关成员的信息。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pszCode`  
 [in]用于生成信息结果代码块字符串的地址。  
  
 `cchCode`  
 [in]该代码块的长度。  
  
 `ichCurrentPosition`  
 [in]字符的位置相对于开始复制的块。  
  
 `dwListTypesRequested`  
 [in]请求列表类型。 可以是以下值的组合：  
  
|常量|值|描述|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|没有列表。|  
|SCRIPT_CMPL_MEMBERLIST|从 0x0001|成员列表。|  
|SCRIPT_CMPL_ENUMLIST|0x0002|枚举列表。|  
|SCRIPT_CMPL_PARAMLIST|0x0004|调用方法参数列表。|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|全局列表。|  
  
 SCRIPT_CMPL_GLOBALLIST 类型会被视为可以通过使用其他完成项的 OR 运算符组合的默认值完成项。 该脚本首先创作引擎尝试填充其他完成列表项的类型信息。 如果失败，则引擎填充 SCRIPT_CMPL_GLOBALLIST。  
  
 `pdwListTypesProvided`  
 [out]提供的列表的类型。  
  
 `pichListAnchorPosition`  
 [out]包含当前的位置的上下文的起始索引。 起始索引是相对于块的起始位置。  
  
 这填充仅当`dwListTypesRequested`包括 SCRIPT_CMPL_MEMBERLIST、 SCRIPT_CMPL_ENUMLIST 或 SCRIPT_CMPL_GLOBALLIST。 对于其他请求的列表类型，结果不可确定。  
  
 `pichFuncAnchorPosition`  
 [out]包含当前的位置的函数调用的开始索引。 起始索引是相对于块的起始位置。  
  
 仅当包含当前的位置的上下文是函数调用，以及时填充`dwListTypesRequested`包括 SCRIPT_CMPL_PARAMLIST。 否则，结果是不确定的。  
  
 `pmemid`  
 [out]中的类型定义的函数 MEMBERID `IProvideMultipleClassInfo``ppunk` out 参数。  
  
 这填充仅当`dwListTypesRequested`包括 SCRIPT_CMPL_PARAMLIST。  
  
 `piCurrentParameter`  
 [out]包含当前的位置参数的索引。 如果当前位置位于函数名称，则返回-1。  
  
 `piCurrentParameter`填充值时，才`dwListTypesRequested`包括 SCRIPT_CMPL_PARAMLIST。  
  
 `ppunk`  
 中的形式提供的类型信息`IProvideMultipleClassInfo`对象。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [IProvideMultipleClassInfo 接口](https://msdn.microsoft.com/library/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo.aspx)   
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)