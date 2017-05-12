---
title: "IActiveScriptParse::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_AddScriptlet"
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::AddScriptlet
添加一个代码scriptlet到脚本。  此方法用于该脚本持久状态交错与宿主文档的环境，并且宿主还原该脚本负责，而不是通过 `IPersist*` 接口。  示例主体是脚本如允许在HTML嵌入的代码scriptlets文档附加到内部事件的语言的HTML \(，ONCLICK\= " button1.text\='Exit”\)。  
  
## 语法  
  
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
  
#### 参数  
 `pstrDefaultName`  
 \[in\]关联的默认名称的地址与scriptlet。  如果scriptlet不包含名为信息\(在上面的示例ONCLICK中\)，则此名称将用于标识scriptlet。  如果此参数是 `NULL`，脚本引擎生成一个名称，如有必要，。  
  
 `pstrCode`  
 \[in\]添加的scriptlet文本的地址。  此字符串的解释取决于这种脚本语言。  
  
 `pstrItemName`  
 \[in\]包含项目名称缓冲区的地址与此scriptlet。  此参数，以及 `pstrSubItemName`外，标识scriptlet是一个事件处理程序的对象。  
  
 `pstrSubItemName`  
 \[in\]一个项目 `subobject` 的名称此scriptlet关联缓冲区的地址;在名为项类型信息必须找到此名称。  如果scriptlet将与命名项目而非 `subitem`，此参数为NULL。  此参数，以及 `pstrItemName`外，标识scriptlet是一个事件处理程序的特定对象。  
  
 `pstrEventName`  
 \[in\]包含事件的名称scriptlet是一个事件处理程序缓冲区的地址。  
  
 `pstrDelimiter`  
 \[in\]地址结束scriptlet分隔符。  当 `pstrCode` 参数从文本时流进行分析，宿主通常使用一个分隔符，例如两个引号\("\)，检测scriptlet的末尾。  此参数指定例如使用的主机，允许脚本引擎提供某些条件原始预处理的分隔符\(，一个单引号\[ \] “将两个单引号用作分隔符\)。  \(和\)，如果脚本引擎正确如何利用此信息取决于脚本引擎。  如果宿主不使用一个分隔符指示scriptlet，结束时将此参数设置为NULL。  
  
 `dwSourceContextCookie`  
 \[in\]使用了用于调试目的应用程序定义的值。  
  
 `ulStartingLineNumber`  
 \[in\]指定的从零开始的值哪行分析将启动。  
  
 `dwFlags`  
 \[in\]标志与scriptlet。  可为下列值的组合：  
  
|返回值|含义|  
|---------|--------|  
|SCRIPTTEXT\_ISVISIBLE|指示脚本文本应当可见\(，因此，可调用的名称\)作为在脚本的命名空间的全局方法。|  
|SCRIPTTEXT\_ISPERSISTENT|指示在添加的代码调用应保存，如果脚本引擎保存\(例如，通过对 `IPersist*::Save`的调用\)，或者，如果脚本引擎通过转换被重置为初始化状态。  有关此状态的更多信息，请参见脚本引擎状态。|  
  
 `pbstrName` ,  
 \[in\]用于的实际名称标识scriptlet。  这是按优先顺序:在scriptlet文本显式指定的名称，在 `pstrDefaultName`提供的默认名称或脚本引擎聚合的唯一名称。  
  
 `pexcepinfo` ,  
 \[in\]包含异常信息的结构的地址。  如果DISP\_E\_EXCEPTION返回，应填充此结构。  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|异常在分析发生scriptlet。  `pexcepinfo` 参数包含有关异常的信息。|  
|`E_INVALIDARG`|参数无效。|  
|`E_NOTIMPL`|此方法不支持;脚本引擎不支持将事件接收的scriptlets。|  
|`E_POINTER`|无效指针指定了。|  
|`E_UNEXPECTED`|调用非预期\(例如，脚本引擎尚未加载还未初始化\)和非失败。|  
|`OLESCRIPT_E_INVALIDNAME`|所提供的默认名称无效的使用此脚本语言。|  
|`OLESCRIPT_E_SYNTAX`|一个未指定的语法错误。scriptlet错误。|  
  
## 请参阅  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)