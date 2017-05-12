---
title: "IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetInfoFromContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetInfoFromContext"
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::GetInfoFromContext
返回类型信息和特定字符的定位点位置在代码块。  对于成员IntelliSense提供信息，全局列表和参数提示。  
  
## 语法  
  
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
  
#### 参数  
 `pszCode`  
 \[in\]代码中的地址块用于的字符串生成信息结果。  
  
 `cchCode`  
 \[in\]代码的长度块。  
  
 `ichCurrentPosition`  
 \[in\]相对块的开头的字符位置。  
  
 `dwListTypesRequested`  
 \[in\]请求的类型列表。  可为下列值的组合：  
  
|常量|值|说明|  
|--------|-------|--------|  
|SCRIPT\_CMPL\_NOLIST|0x0000|没有列表。|  
|SCRIPT\_CMPL\_MEMBERLIST|0x0001|成员列表。|  
|SCRIPT\_CMPL\_ENUMLIST|0x0002|枚举列表。|  
|SCRIPT\_CMPL\_PARAMLIST|0x0004|调用方法的参数列表。|  
|SCRIPT\_CMPL\_GLOBALLIST|0x0008|全局列表。|  
  
 SCRIPT\_CMPL\_GLOBALLIST类型视为可以合并通过使用或运算符与其他完成项目的默认完成项。  生成引擎的脚本先尝试填充其他完成的类型信息列表项。  如果该操作失败，该引擎还SCRIPT\_CMPL\_GLOBALLIST填充。  
  
 `pdwListTypesProvided`  
 \[in\]类型的列表提供。  
  
 `pichListAnchorPosition`  
 \[in\]包含当前位置上下文的起始索引。  起始索引是相对于块的开头。  
  
 仅当 `dwListTypesRequested` 包括SCRIPT\_CMPL\_MEMBERLIST、SCRIPT\_CMPL\_ENUMLIST或SCRIPT\_CMPL\_GLOBALLIST时，将填充。  对于请求的其他列表类型，则结果是未定义的。  
  
 `pichFuncAnchorPosition`  
 \[in\]包含当前位置的起始索引函数调用。  起始索引是相对于块的开头。  
  
 这填充，仅在包含当前位置时的上下文是函数调用，则，所以，当 `dwListTypesRequested` 包括SCRIPT\_CMPL\_PARAMLIST时。  否则，结果是未定义的。  
  
 `pmemid`  
 \[in\]功能的MEMBERID定义，由 `IProvideMultipleClassInfo``ppunk` 参数的类型。  
  
 仅当 `dwListTypesRequested` 包括SCRIPT\_CMPL\_PARAMLIST时，将填充。  
  
 `piCurrentParameter`  
 \[in\]包含当前位置参数的索引。  如果当前位置在函数名，则返回\-1。  
  
 仅当 `dwListTypesRequested` 包括SCRIPT\_CMPL\_PARAMLIST时，`piCurrentParameter` 值填充。  
  
 `ppunk`  
 类型信息，并且 `IProvideMultipleClassInfo` 对象的形式，提供。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideMultipleClassInfo>   
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)