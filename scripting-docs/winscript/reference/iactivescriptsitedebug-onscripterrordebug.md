---
title: "IActiveScriptSiteDebug::OnScriptErrorDebug |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a669d435d84295b22af4298936babf8439eaefa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
允许智能主机，以便确定如何处理运行时错误。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pErrorDebug`  
 [in]发生的运行时错误  
  
 `pfEnterDebugger`  
 [out]标志，该值指示是否将错误传递到调试器执行 JIT 调试。  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out]标志，该值指示是否调用`IActiveScriptSite::OnScriptError`当用户决定继续而不进行调试。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括，但不限于以下表中的值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 智能宿主可以使用此方法来确定如何处理运行时错误。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptSiteDebug 接口](../../winscript/reference/iactivescriptsitedebug-interface.md)