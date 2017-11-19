---
title: "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e428f12b3d199603ac341a5e069fcc5ce5d36f93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
通知主机有关脚本运行时错误过程调试管理器时未找到实时脚本调试器。  
  
 若要在你的主机中实现调试器，你应处理[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)。 根据用户操作，主机可以附加调试器并返回，或者返回 OnScriptErrorDebug 中调试器的起始`pfEnterDebugger`参数。 你还应实现此接口可获取有关运行时错误通知，即使有过程调试管理器可以解释没有外部调试器。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pErrorDebug`  
 [in]发生的运行时错误。  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out]是否要调用[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)如果用户决定继续而不进行调试。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 你还应实现此接口可看到一条通知。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptSiteDebugEx 接口](../../winscript/reference/iactivescriptsitedebugex-interface.md)