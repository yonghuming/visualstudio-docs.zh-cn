---
title: "IActiveScriptDebug::GetScriptletTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.GetScriptletTextAttributes
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::GetScriptletTextAttributes"
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::GetScriptletTextAttributes
返回任意scriptlet的文本属性。  
  
## 语法  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### 参数  
 `pstrCode`  
 \[in\] scriptlet文本。  不需要为null终止的该字符串。  
  
 `uNumCodeChars`  
 \[in\]中的字符数。scriptlet文本。  
  
 `pstrDelimiter`  
 \[in\]地址结束scriptlet分隔符。  当 `pstrCode` 从文本时流进行分析，宿主通常使用一个分隔符，例如两个引号\("\)，检测scriptlet的末尾。  此参数指定例如使用的主机，允许脚本引擎提供某些条件原始预处理的分隔符\(，一个单引号\[ \] “将两个单引号用作分隔符\)。  \(和\)，如果脚本引擎正确如何使用此信息取决于脚本引擎。  如果宿主不使用一个分隔符指示scriptlet，结束时将此参数设置为NULL。  
  
 `dwFlags`  
 \[in\]标志与scriptlet。  可以是这些值的组合：  
  
|常量|值|说明|  
|--------|-------|--------|  
|GETATTRTYPE\_DEPSCAN|0x0001|分别指示标识符和使用点运算符应确定与SOURCETEXT\_ATTR\_IDENTIFIER和SOURCETEXT\_ATTR\_MEMBERLOOKUP标志，。|  
|GETATTRFLAG\_THIS|0x0100|指示应确定当前对象的标识符与SOURCETEXT\_ATTR\_THIS标志。|  
|GETATTRFLAG\_HUMANTEXT|0x8000|指示应确定该字符串内容和注释文本与SOURCETEXT\_ATTR\_HUMANTEXT标志。|  
  
 `pattr`  
 \[in，out\]包含返回属性的缓冲区。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 实现 `IDebugDocumentText` 接口的一个智能宿主可以使用此方法将调用委托给 `IDebugDocumentText::GetText` 方法。  
  
 因为scriptlets比脚本往往表达式，并可以具有不同的语法块，则调用提供。  如果它们具有相同的语法，此方法的实现与 `GetScriptTextAttributes` 方法的实现是相同的。  
  
## 请参阅  
 [IActiveScriptDebug 接口](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [IDebugDocumentText 接口](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE\_TEXT\_ATTR 枚举](../../winscript/reference/source-text-attr-enumeration.md)