---
title: "IDebugDocumentHelper::DefineScriptBlock | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.DefineScriptBlock
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::DefineScriptBlock"
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::DefineScriptBlock
指示到帮助器字符的特定范围由特定脚本引擎处理的脚本块。  
  
## 语法  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### 参数  
 `ulCharOffset`  
 \[in\]该脚本的位置块。  
  
 `cChars`  
 \[in\]中的字符数在脚本块。  
  
 `pas`  
 \[in\]此脚本的脚本引擎块。  
  
 `fScriptlet`  
 \[in\]中标记指示该脚本块是scriptlet。  
  
 `pdwSourceContext`  
 \[in\]该脚本的源上下文块。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 该文档包含嵌入式脚本块时，一个智能宿主可以使用此方法。  其代码包含其他语言时，嵌入式脚本语言引擎可以使用此方法。  
  
 脚本引擎对所有语法着色负责中，代码在该脚本的上下文找到块。  
  
 应调用 `DefineScriptBlock` 方法，在文本添加之后\(例如，使用 `IDebugDocumentHelper::AddDBCSText` 方法\)，但，在脚本块之前分析\(例如，使用 `IActiveScriptParse ::ParseScriptText` 方法\)。  
  
## 请参阅  
 [IDebugDocumentHelper 接口](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)