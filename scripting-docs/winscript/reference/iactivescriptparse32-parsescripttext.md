---
title: "IActiveScriptParse32::ParseScriptText |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f33e454c-69d8-4cab-9150-d1e7fd04786d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: af1e3b6723b402263359719695aa1f57432c76e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::ParseScriptText
分析给定的代码 scriptlet，添加到命名空间声明和评估作为适当的代码。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|`pstrCode`|[in]要评估的 scriptlet 文本的地址。 此字符串的解释依赖于脚本语言。|  
|`pstrItemName`|[in]将给出上下文 scriptlet 处于要进行求值的项名称的地址。 如果此参数为 NULL，是在脚本引擎的全局上下文中计算代码。|  
|`punkContext`|[in]上下文对象的地址。 此对象保留在调试环境中，此类上下文可能由调试器来表示活动的运行时上下文中使用。 如果此参数为 NULL，则引擎会使用`pstrItemName`能够识别该上下文。|  
|`pstrDelimiter`|[in]最终的 scriptlet 分隔符的地址。 当`pstrCode`分析从文本流中，主机通常使用分隔符，如两个单引号 （'），来检测的 scriptlet 尾。 此参数指定主机使用，从而提供某些条件的基元预处理的脚本引擎的分隔符 （例如，将作为分隔符用于两个单引号替换单引号 [']）。 完全如何 （和如果） 可以使用此信息的使用取决于脚本引擎脚本引擎进行。 将此参数设置为`NULL`如果主机未使用分隔符来标记的 scriptlet 的结尾。|  
|`dwSourceContextCookie`|[in]出于调试目的使用 cookie。|  
|`ulStartingLineNumber`|[in]指定的分析将开始的行的从零开始值。|  
|`dwFlags`|[in]与 scriptlet 关联的标志。 可以是这些值的组合：|  
  
|值|含义|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|如果计算的表达式和语句之间的差异非常重要，但语法不明确的脚本语言中，此标志指定 scriptlet 是被解释为表达式，而不是一个语句或语句的列表。 默认情况下，除非可以从 scriptlet 文本的语法确定正确的选择假定语句。|  
|SCRIPTTEXT_ISPERSISTENT|指示是否保存脚本引擎，应保存在此调用过程中添加的代码 (例如，通过调用`IPersist*::Save`)，或如果脚本引擎重置通过回初始化状态的转换。|  
|SCRIPTTEXT_ISVISIBLE|表示脚本文本应为可见 (因此，可调用按名称) 作为脚本的命名空间中的全局方法。|  
  
|||  
|-|-|  
|`pvarResult`|[out]接收的 scriptlet 处理结果的缓冲区地址或`NULL`如果调用方不期望任何结果 （即，不设置 SCRIPTTEXT_ISEXPRESSION 值）。|  
|`pexcepinfo`|[out]接收异常信息的结构的地址。 如果填充此结构`IActiveScriptParse::ParseScriptText`返回 DISP_E_EXCEPTION。|  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|在的 scriptlet 处理过程中出现异常。 `pexcepinfo`参数包含有关异常的信息。|  
|`E_INVALIDARG`|自变量无效。|  
|`E_POINTER`|指定了无效的指针。|  
|`E_NOTIMPL`|不支持此方法。 脚本引擎不支持运行时计算的表达式或语句。|  
|`E_UNEXPECTED`|不应调用 （例如，脚本引擎处于未初始化或已关闭状态，或设置 SCRIPTTEXT_ISEXPRESSION 标志和脚本引擎处于初始化状态）。|  
|`OLESCRIPT_E_SYNTAX`|Scriptlet 中出现未指定的语法错误。|  
  
## <a name="remarks"></a>备注  
 如果脚本引擎处于初始化状态时，没有代码实际上将计算在此调用; 过程相反，此类代码是排队和执行时到 （或通过） 转换脚本引擎已启动的状态。 处于初始化状态不允许执行，因为它是调用具有 SCRIPTTEXT_ISEXPRESSION 标志处于初始化状态时此方法中的错误。  
  
 Scriptlet 可以是表达式、 语句的列表，或允许的脚本语言的任何内容。 例如，此方法使用在评估中的 html\<脚本 > 标记，它使得多个语句来执行，因为正在构建 HTML 页，而不是只需将它们编译成的脚本状态。  
  
 传递给此方法的代码必须是有效的完整部分代码。 例如，在 VBScript 中是非法的调用与子进行一次此方法，然后第二次使用`End Sub`。 分析器必须不等待完成子例程，第二个调用，但因为子例程声明已启动但未完成，而是就必须生成分析错误。  
  
 有关脚本状态的详细信息，请参阅的脚本引擎状态部分[Windows 脚本引擎](../../winscript/windows-script-engines.md)。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)