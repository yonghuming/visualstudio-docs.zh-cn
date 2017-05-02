---
title: "IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthorProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthorProcedure::ParseProcedureText"
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthorProcedure::ParseProcedureText
分析代码的程序中添加代码，程序的文本到生成引擎的脚本，并创建对应于代码的程序 `IScriptEntry` 对象。  
  
## 语法  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### 参数  
 `pszCode`  
 \[in\]分析的脚本文本。  
  
 `pszFormalParams`  
 \[in\]形参名称的地址对于程序。  必须由生成引擎的脚本的相应分隔符分隔参数名称。  在圆括号不应将名称。  
  
 `pszProcedureName`  
 \[in\]要分析的过程名的地址。  
  
 `pszItemName`  
 \[in\]包含项目名称的缓冲区地址与 `IScriptEntry` 对象。  
  
 `pszDelimiter`  
 \[in\]关闭脚本块分隔符的地址。  当 `pszCode` 从文本时流进行分析，宿主通常使用一个分隔符\(例如两个单引号\)，检测末尾的脚本块。  ;如果没有标记结束的分隔符的脚本块，将此参数设置为NULL。  
  
 `dwCookie`  
 \[in\]与新 `IScriptEntry` 对象的应用程序定义的值。  
  
 `dwFlags`  
 \[in\] 未使用。  
  
 `pdispFor`  
 \[in\] 未使用。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 当前 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 引擎不执行此方法。  
  
## 请参阅  
 [IActiveScriptAuthorProcedure 接口](../../winscript/reference/iactivescriptauthorprocedure-interface.md)