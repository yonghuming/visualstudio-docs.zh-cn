---
title: "IActiveScriptSiteDebug::GetDocumentContextFromPosition |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteDebug::GetDocumentContextFromPosition
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25ce03a124f246443afd0f5a8540a93e7d474f9a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebuggetdocumentcontextfromposition"></a>IActiveScriptSiteDebug::GetDocumentContextFromPosition
语言引擎用于委派`IDebugCodeContext::GetSourceContext`。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwSourceContext`  
 [in]源内容提供给`ParseScriptText`或`AddScriptlet`。  
  
 `uCharacterOffset`  
 [in]字符相对于的脚本块或 scriptlet 开始偏移量。  
  
 `uNumChars`  
 [in]在此上下文中的字符数。  
  
 `ppsc`  
 [out]对应于此字符位置范围文档上下文。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 语言引擎使用此方法委托`IDebugCodeContext::GetSourceContext`。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptSiteDebug 接口](../../winscript/reference/iactivescriptsitedebug-interface.md)