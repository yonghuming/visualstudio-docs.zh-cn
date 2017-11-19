---
title: "IDebugDocumentHelper::DefineScriptBlock |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.DefineScriptBlock
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b6ec86dacc2e3a8f3d9e28a6db744b778ff01eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
指示帮助器特定范围的字符，是由给定的脚本引擎处理的脚本块。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ulCharOffset`  
 [in]脚本块的起始位置。  
  
 `cChars`  
 [in]脚本块中的字符数。  
  
 `pas`  
 [in]此脚本块与脚本引擎。  
  
 `fScriptlet`  
 [in]该标志指示脚本块是否 scriptlet。  
  
 `pdwSourceContext`  
 [out]脚本块的源上下文。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 当其文档包含嵌入式的脚本块，智能主机可以使用此方法。 语言引擎可以使用此方法时其代码包含对其他语言的嵌入式的脚本。  
  
 脚本引擎负责所有语法颜色设置和代码上下文查找，脚本块中。  
  
 `DefineScriptBlock`添加文本后，应调用方法 (例如，使用`IDebugDocumentHelper::AddDBCSText`方法)，但在该脚本之前已分析块 (例如，使用`IActiveScriptParse ::ParseScriptText`方法)。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentHelper 接口](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)