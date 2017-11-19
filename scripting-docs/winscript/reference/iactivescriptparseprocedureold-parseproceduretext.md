---
title: "IActiveScriptParseProcedureOld::ParseProcedureText |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptParseProcedureOld.ParseProcedureText
apilocation: jscript.dll
helpviewer_keywords: IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab546deb390535fa8ff71e116a0ad42d33cc104
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
分析给定的代码过程并将匿名过程添加到命名空间。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstrCode`  
 [in]要评估的过程文本。 此字符串的解释依赖于脚本语言。  
  
 `pstrFormalParams`  
 [in]该过程的正式参数名称。 参数名称必须与脚本引擎适当的分隔符分隔。 名称应不能括在括号中。  
  
 `pstrItemName`  
 [in]将给出上下文是用要计算过程命名项的名称。 如果此参数为`NULL`，在脚本引擎的全局上下文中计算代码。  
  
 `punkContext`  
 [in]上下文对象中。 此对象保留在调试环境中，此类上下文可能由调试器来表示活动的运行时上下文中使用。 如果此参数为`NULL`，则引擎会使用`pstrItemName`能够识别该上下文。  
  
 `pstrDelimiter`  
 [in]最终的过程分隔符中。 当`pstrCode`分析从文本流中，主机通常使用分隔符，如两个单引号 （'），来检测过程末尾。 此参数指定主机使用，从而提供某些条件的脚本引擎的分隔符 （例如，将替换为用于作为分隔符两个单引号单引号 [']） 的基元预处理。 完全如何 （和如果） 此信息取决于脚本引擎的脚本引擎使用。 将此参数设置为`NULL`如果主机未使用分隔符来标记该过程的结尾。  
  
 `dwSourceContextCookie`  
 [in]出于调试目的使用的应用程序定义的值。  
  
 `ulStartingLineNumber`  
 [in]指定哪些行处的分析将开始的从零开始值。  
  
 `dwFlags`  
 [in]与该过程关联的标志。 可以是这些值的组合。  
  
|常量|值|含义|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|指示中的代码`pstrCode`是表示该过程的返回值的表达式。|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|指示`this`过程的作用域内包括指针。|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|指示的父级`this`指针都包括在该过程的作用域。|  
  
 `ppdisp`  
 [out]返回的调度包装其中的默认方法是通过此方法分析的过程。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_INVALIDARG`|自变量无效。|  
|`E_POINTER`|指定了无效的指针。|  
|`E_NOTIMPL`|不支持此方法。 脚本引擎不支持运行时添加到命名空间的过程。|  
|`E_UNEXPECTED`|不应调用 （例如，脚本引擎处于未初始化或已关闭状态）。|  
|`OLESCRIPT_E_SYNTAX`|在过程中出现未指定的语法错误。|  
|`S_FALSE`|脚本引擎不支持调度的对象;`ppdisp`参数设置为`NULL`。|  
  
## <a name="remarks"></a>备注  
 此调用; 不计算任何脚本代码则相反，该过程编译成方法上`ppdisp`其中它可以由调用脚本更高版本。  
  
 此接口已弃用鉴于`IActiveScriptParseProcedure`接口。 `IActiveScriptParseProcedure::ParseProcedureText`方法类似于此方法，但它允许过程名称以指定。 在所有情况下，`IActiveScriptParseProcedure::ParseProcedureText`应使用。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptParseProcedureOld 接口](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)