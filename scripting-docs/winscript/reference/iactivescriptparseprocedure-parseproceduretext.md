---
title: "IActiveScriptParseProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedure_ParseProcedureText"
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure::ParseProcedureText
分析特定代码程序并添加过程到命名空间。  
  
## 语法  
  
```  
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### 参数  
 `pstrCode`  
 \[in\]计算的程序文本的地址。  此字符串的解释取决于这种脚本语言。  
  
 `pstrFormalParams`  
 \[in\]形参名称地址对于程序。  必须分隔参数名后面加上脚本引擎的相应分隔符。  不应括在括号名称。  
  
 `pstrProcedureName`  
 \[in\]要分析的过程名地址。  
  
 `pstrItemName`  
 \[in\]提供上下文该程序将计算项目名称的地址。  如果此参数是 `NULL`，代码对脚本引擎的全局上下文进行计算。  
  
 `punkContext`  
 \[out\]上下文对象的地址。  此对象保留了用于调试环境，此上下文可能由调试器提供表示有效的运行时上下文。  如果此参数是 `NULL`，引擎使用 `pstrItemName` 标识上下文。  
  
 `pstrDelimiter`  
 \[in\]关闭程序分隔符的地址。  当 `pstrCode` 从文本时流进行分析，宿主通常使用一个分隔符，例如两个引号\("\)，检测过程的结尾。  此参数指定例如使用的主机，允许脚本引擎提供某些条件原始预处理的分隔符\(，一个单引号\[ \] “将两个单引号用作分隔符\)。  \(和\)，如果脚本引擎正确如何利用此信息取决于脚本引擎。  如果宿主不使用一个分隔符以指示该程序，结束时将此参数设置为 `NULL`。  
  
 `dwSourceContextCookie`  
 \[in\]使用了用于调试目的应用程序定义的值。  
  
 `ulStartingLineNumber`  
 \[in\]指定的从零开始的值哪行分析将启动。  
  
 `dwFlags`  
 \[in\]标志与该程序。  可以是这些值的组合：  
  
|值|含义|  
|-------|--------|  
|SCRIPTPROC\_ISEXPRESSION|指示在 `pstrCode` 的代码是表示该过程的返回值的表达式。  默认情况下，代码可以在程序包含表达式，语句脚本语言允许的列表或其他。|  
|SCRIPTPROC\_IMPLICIT\_THIS|指示 `this` 指针包括在该过程范围内。|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|指示 `this` 指针的父包括在该过程范围内。|  
  
 `ppdisp`  
 \[out\]指针的地址包含脚本的全局方法和属性的对象。  如果脚本引擎不支持这些对象，`NULL` 返回。  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|参数无效。|  
|`E_POINTER`|无效指针指定了。|  
|`E_NOTIMPL`|此方法不受支持。  脚本引擎不支持程序的运行时向命名空间。|  
|`E_UNEXPECTED`|调用非预期\(例如，脚本引擎在未初始化或已关闭状态\)。|  
|`OLESCRIPT_E_SYNTAX`|一个未指定的语法错误在过程生成的。|  
|`S_FALSE`|脚本引擎不支持计划对象；`ppdisp` 参数设置为 `NULL`。|  
  
## 备注  
 脚本代码不会计算在调用;相反，该程序被编译到其可以由该脚本调用后的脚本状态。  
  
## 请参阅  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)