---
title: "IActiveScriptParse::AddScriptlet |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptParse.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptParse_AddScriptlet
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e854ac71dc36263d805160f9336e049856076ce5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
将代码 scriptlet 添加到该脚本。 此方法使用在且环境中使用主机文档混合在一起的持久状态的脚本主机负责还原脚本，而不是通过`IPersist*`接口。 主示例包括允许的代码嵌入在 HTML 文档中要附加到内部函数的事件的 scriptlet 的 HTML 脚本语言 (例如，ONCLICK="button1.text='Exit")。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstrDefaultName`  
 [in]默认名称，以将与 scriptlet 相关联的地址。 如果 scriptlet 不包含命名信息 （如上面的 ONCLICK 示例），此名称将用于标识 scriptlet。 如果此参数为`NULL`，脚本引擎生成的唯一名称，如有必要。  
  
 `pstrCode`  
 [in]要添加的 scriptlet 文本的地址。 此字符串的解释依赖于脚本语言。  
  
 `pstrItemName`  
 [in]包含与此 scriptlet 关联的项名称的缓冲区地址。 此参数，除`pstrSubItemName`，标识 scriptlet 为事件处理程序的对象。  
  
 `pstrSubItemName`  
 [in]包含的名称的缓冲区地址`subobject`与其此 scriptlet 相关联; 必须在命名的项的类型信息中找到此名称的命名项。 此参数为 NULL，而不是命名项与相关联的 scriptlet 是否`subitem`。 此参数，除`pstrItemName`，标识 scriptlet 为事件处理程序的特定对象。  
  
 `pstrEventName`  
 [in]包含为其 scriptlet 是一个事件处理程序事件的名称的缓冲区地址。  
  
 `pstrDelimiter`  
 [in]最终的 scriptlet 分隔符的地址。 当`pstrCode`参数分析从文本流中，主机通常使用分隔符，如两个单引号 （'），来检测的 scriptlet 尾。 此参数指定主机使用，从而提供某些条件的基元预处理的脚本引擎的分隔符 （例如，将作为分隔符用于两个单引号替换单引号 [']）。 完全如何 （和如果） 可以使用此信息的使用取决于脚本引擎脚本引擎进行。 如果主机未使用分隔符来标记的 scriptlet 的结尾，此参数设置为 NULL。  
  
 `dwSourceContextCookie`  
 [in]出于调试目的使用的应用程序定义的值。  
  
 `ulStartingLineNumber`  
 [in]指定的分析将开始的行的从零开始值。  
  
 `dwFlags`  
 [in]与 scriptlet 关联的标志。 可以是以下值的组合：  
  
|返回值|含义|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|表示脚本文本应为可见 (因此，可调用按名称) 作为脚本的命名空间中的全局方法。|  
|SCRIPTTEXT_ISPERSISTENT|指示是否保存脚本引擎，应保存在此调用过程中添加的代码 (例如，通过调用`IPersist*::Save`)，或如果脚本引擎重置通过回初始化状态的转换。 有关此状态的详细信息，请参阅脚本引擎状态。|  
  
 `pbstrName` ,  
 [out]用于标识 scriptlet 的实际名称。 这是要优先顺序： scriptlet 文本中显式指定一个名称，在提供的默认名称`pstrDefaultName`，或通过脚本引擎合成的唯一名称。  
  
 `pexcepinfo` ,  
 [out]一个包含异常信息结构的地址。 如果返回 DISP_E_EXCEPTION，应该填写此结构。  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|在分析的 scriptlet 出现异常。 `pexcepinfo`参数包含有关异常的信息。|  
|`E_INVALIDARG`|自变量无效。|  
|`E_NOTIMPL`|不支持此方法;脚本引擎不支持添加事件接收 scriptlet。|  
|`E_POINTER`|指定了无效的指针。|  
|`E_UNEXPECTED`|不应调用 （例如，脚本引擎具有尚未加载或初始化），因此失败。|  
|`OLESCRIPT_E_INVALIDNAME`|此脚本的语言中，提供的默认名称无效。|  
|`OLESCRIPT_E_SYNTAX`|Scriptlet 中出现未指定的语法错误。|  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)