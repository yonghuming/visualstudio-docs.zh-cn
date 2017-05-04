---
title: "IActiveScriptAuthor::GetScriptletTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetScriptletTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetScriptletTextAttributes"
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptAuthor::GetScriptletTextAttributes
返回scriptlet的文本属性。  
  
## 语法  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### 参数  
 `pszCode`  
 \[in，size\_is \(`cch`\)\]scriptlet文本。  不必为null终止的该字符串。  
  
 `cch`  
 \[in\]用于 `pszCode` 和 `pattr` 参数的大小。  
  
 `pszDelimiter`  
 \[in\]地址结束scriptlet分隔符。  当 `pszCode` 从文本时流进行分析，宿主通常使用一个分隔符\(例如两个单引号\)，检测scriptlet的末尾。  如果分隔符不用于标识scriptlet，结束时将此参数设置为NULL。  
  
 `dwFlags`  
 \[in\]与scriptlet的文本属性的标志。  可为下列值的组合。  
  
|常量|值|说明|  
|--------|-------|--------|  
|GETATTRTYPE\_DEPSCAN|0x0001|确定具有SOURCETEXT\_ATTR\_IDENTIFIER属性的标识符，并确定具有SOURCETEXT\_ATTR\_MEMBERLOOKUP属性的使用点运算符。|  
|GETATTRFLAG\_THIS|0x0100|确定具有SOURCETEXT\_ATTR\_THIS属性的当前对象。|  
|GETATTRFLAG\_HUMANTEXT|0x8000|标识字符串内容和注释具有SOURCETEXT\_ATTR\_HUMANTEXT属性的文本。|  
  
 `pattr`  
 \[in，size\_is \(`cch`\)\]scriptlet代码的颜色信息。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE\_TEXT\_ATTR 枚举](../../winscript/reference/source-text-attr-enumeration.md)