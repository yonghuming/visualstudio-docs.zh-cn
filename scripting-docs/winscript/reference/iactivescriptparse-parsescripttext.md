---
title: "IActiveScriptParse::ParseScriptText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_ParseScriptText"
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptParse::ParseScriptText
分析给定的代码 scriptlet，添加声明到命名空间并根据需要计算代码。  
  
## 语法  
  
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
  
#### 参数  
  
|||  
|-|-|  
|`pstrCode`|\[in\] 要计算的 scriptlet 文本的地址。  此字符串的解释取决于脚本语言。|  
|`pstrItemName`|\[in\] 提供将计算 scriptlet 的上下文的项目名称的地址。  如果此参数为 NULL，则代码将在脚本引擎的全局上下文中进行评估。|  
|`punkContext`|\[in\] 上下文对象的地址。  此对象保留给调试环境使用，在这种环境中可由调试器提供上下文以表示有效的运行时上下文。  如果此参数为 NULL，引擎将使用 `pstrItemName` 来标识上下文。|  
|`pstrDelimiter`|\[in\] 结束 scriptlet 分隔符的地址。  当从文本流分析得到 `pstrCode` 时，主机通常使用分隔符，例如两个单字节引号 \("\)，检测 scriptlet 的末尾部分。  此参数可以指定主机使用的分隔符，允许脚本引擎提供有条件的原始预处理（例如，使用用作分隔符的双引号替换单引号\['\]）。  脚本引擎是否会且如何使用此信息取决于脚本引擎。  如果主机不使用分隔符指示脚本小程序的结束，则将此参数设置为 `NULL`。|  
|`dwSourceContextCookie`|\[in\] 用于调试目的 Cookie。z|  
|`ulStartingLineNumber`|\[in\] 指定分析开始的行的从零开始的值。|  
|`dwFlags`|\[in\] 与 scriptlet 相关联的标志。  可以是这些值的组合：|  
  
|值|含义|  
|-------|--------|  
|SCRIPTTEXT\_ISEXPRESSION|如果一个计算表达式和语句之间的差异很重要，但在脚本语言中的语法模糊，此标志将指定理解为表达式而不是语句或语句列表的 scriptlet。  默认情况下，除非可以从 scriptlet 文本语法中确定正确的选择，否则要假定语句。|  
|SCRIPTTEXT\_ISPERSISTENT|如果脚本引擎保存（例如，通过对 `IPersist*::Save` 的调用），或者如果脚本引擎通过转换为初始化状态的方法重置，指示该调用中添加的代码应保存。|  
|SCRIPTTEXT\_ISVISIBLE|指示脚本文本应当显示为脚本名称空间的全局方法（因此，可根据名称调用）。|  
  
|||  
|-|-|  
|`pvarResult`|\[out\] 接收 scriptlet 处理过程的结果，或者，当调用方希望无结果（即不设置 SCRIPTTEXT\_ISEXPRESSION 值）时，接收 `NULL` 结果的缓冲区的地址。|  
|`pexcepinfo`|\[out\] 接收异常信息的结构的地址。  如果 `IActiveScriptParse::ParseScriptText` 返回 DISP\_E\_EXCEPTION，将填充此结构。|  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|在处理 scriptlet 时发生的异常。  `pexcepinfo` 参数包含异常的相关信息。|  
|`E_INVALIDARG`|参数无效。|  
|`E_POINTER`|指定了无效的指针。|  
|`E_NOTIMPL`|此方法不受支持。  脚本引擎不支持表达式或语句的运行时计算。|  
|`E_UNEXPECTED`|这是意外调用（例如，脚本引擎为未初始化或已关闭状态，或已设置 SCRIPTTEXT\_ISEXPRESSION 标志，同时脚本引擎为初始化状态\)。|  
|`OLESCRIPT_E_SYNTAX`|Scriptlet 中出现了一个未指定的语法错误。|  
  
## 备注  
 如果脚本引擎处于初始化状态，在此调用的实际过程中将不对任何代码进行评估；当然，当脚本引擎转换到（或通过）已启用状态时，将排列并执行此代码。  因为在初始化状态中不允许执行，所以在处于初始化状态时调用这个带有 SCRIPTTEXT\_ISEXPRESSION 标志的方法是错误的。  
  
 scriptlet 可以是表达式、一列语句，或脚本语言允许的任何形式。  例如，此方法用于 HTML \<SCRIPT\> 标记的计算，允许在构造 HTML 页时执行语句，而不是仅将其编译成脚本状态。  
  
 传递给此方法的代码必须是有效的完整部分代码。  例如，在 VBScript 中，第一次用子函数 \(x\)、第二次用 `End Sub` 调用该方法是非法的。  不可以第二次调用分析器完成子例程，因为已经启动了子例程声明但还没有完成，所以肯定会生成分析错误。  
  
 有关脚本状态的详细信息，请参阅 [Windows 脚本引擎](../../winscript/windows-script-engines.md) 的脚本引擎状态章节。  
  
## 请参阅  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)