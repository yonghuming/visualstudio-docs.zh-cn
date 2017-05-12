---
title: "IDebugDocumentHost::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetScriptTextAttributes"
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetScriptTextAttributes
返回块的文本属性文档文本。  
  
## 语法  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### 参数  
 `pstrCode`  
 \[in\]该脚本块文本。  不需要为null终止的该字符串。  
  
 `uNumCodeChars`  
 \[in\]中的字符数在脚本块文本。  
  
 `pstrDelimiter`  
 \[in\]关闭脚本块分隔符的地址。  当 `pstrCode` 从文本时流进行分析，宿主通常使用一个分隔符，例如两个引号\("\)，检测末尾的脚本块。  此参数指定例如使用的主机，允许脚本引擎提供某些条件原始预处理的分隔符\(，一个单引号\[ \] “将两个单引号用作分隔符\)。  \(和\)，如果脚本引擎正确如何使用此信息取决于脚本引擎。  如果宿主不使用一个分隔符指示末尾的脚本块，将此参数设置为NULL。  
  
 `dwFlags`  
 \[in\]标志与该脚本块。  可以是这些值的组合：  
  
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
|`E_NOTIMPL`|宿主仅使用默认特性。|  
  
## 备注  
 此方法返回任意的文本特性块文档文本。  在使用情况下，返回 `E_NOTIMPL`宿主可接受默认特性。  
  
## 请参阅  
 [IDebugDocumentHost 接口](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE\_TEXT\_ATTR 枚举](../../winscript/reference/source-text-attr-enumeration.md)