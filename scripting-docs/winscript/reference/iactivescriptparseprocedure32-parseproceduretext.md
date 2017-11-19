---
title: "IActiveScriptParseProcedure32::ParseProcedureText |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2f36160ab9dca3ccc99aed1068b7e94fe1b7675d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
分析给定的代码过程并添加到命名空间的过程。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `pstrCode`  
 [in]要评估的过程文本的地址。 此字符串的解释依赖于脚本语言。  
  
 `pstrFormalParams`  
 [in]该过程的形式参数名称的地址。 参数名称必须与脚本引擎适当的分隔符分隔。 名称应不能括在括号中。  
  
 `pstrProcedureName`  
 [in]要分析的过程名称的地址。  
  
 `pstrItemName`  
 [in]将给出上下文是用要计算该过程的项名称的地址。 如果此参数为`NULL`，在脚本引擎的全局上下文中计算代码。  
  
 `punkContext`  
 [in]上下文对象的地址。 此对象保留在调试环境中，此类上下文可能由调试器来表示活动的运行时上下文中使用。 如果此参数为`NULL`，则引擎会使用`pstrItemName`能够识别该上下文。  
  
 `pstrDelimiter`  
 [in]最终的过程分隔符的地址。 当`pstrCode`分析从文本流中，主机通常使用分隔符，如两个单引号 （'），来检测过程末尾。 此参数指定主机使用，从而提供某些条件的基元预处理的脚本引擎的分隔符 （例如，将作为分隔符用于两个单引号替换单引号 [']）。 完全如何 （和如果） 可以使用此信息的使用取决于脚本引擎脚本引擎进行。 将此参数设置为`NULL`如果主机未使用分隔符来标记该过程的结尾。  
  
 `dwSourceContextCookie`  
 [in]出于调试目的使用的应用程序定义的值。  
  
 `ulStartingLineNumber`  
 [in]指定的分析将开始的行的从零开始值。  
  
 `dwFlags`  
 [in]与该过程关联的标志。 可以是这些值的组合：  
  
|值|含义|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|指示中的代码`pstrCode`是表示该过程的返回值的表达式。 默认情况下，代码可以包含表达式、 语句的列表，或任何其他允许的脚本语言在过程中。|  
|SCRIPTPROC_IMPLICIT_THIS|指示`this`过程的作用域内包括指针。|  
|SCRIPTPROC_IMPLICIT_PARENTS|指示的父级`this`指针都包括在该过程的作用域。|  
  
 `ppdisp`  
 [out]包含脚本的全局方法和属性的对象的指针的地址。 如果脚本引擎不支持此类对象，`NULL`返回。  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|自变量无效。|  
|`E_POINTER`|指定了无效的指针。|  
|`E_NOTIMPL`|不支持此方法。 脚本引擎不支持运行时添加到命名空间的过程。|  
|`E_UNEXPECTED`|不应调用 （例如，脚本引擎处于未初始化或已关闭状态）。|  
|`OLESCRIPT_E_SYNTAX`|在过程中出现未指定的语法错误。|  
|`S_FALSE`|脚本引擎不支持调度的对象;`ppdisp`参数设置为`NULL`。|  
  
## <a name="remarks"></a>备注  
 此调用; 不计算任何脚本代码则相反，该过程会编译成，则可以调用脚本更高版本的脚本状态。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)