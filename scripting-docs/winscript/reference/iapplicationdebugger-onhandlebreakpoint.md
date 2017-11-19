---
title: "IApplicationDebugger::onHandleBreakPoint |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebugger.onHandleBreakPoint
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebugger::onHandleBreakPoint
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3be067d3b8c3e3268ac2caf1614b70efff6f665
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
处理断点事件。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>参数  
 `prpt`  
 [in]断点发生的位置中的线程。  
  
 `br`  
 [in]断点的原因。  
  
 `pError`  
 [in]运行时错误信息时提供的值`br`是会发生 BREAKREASON_ERROR。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 命中断点时调用此方法和`IDebugApplication::HandleBreakPoint`调用。  
  
 应用程序将仍挂起，直到调试器 IDE 调用`IRemoteDebugApplication::ResumeFromBreakPoint`。  
  
## <a name="see-also"></a>另请参阅  
 [IApplicationDebugger 接口](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [BREAKREASON 枚举](../../winscript/reference/breakreason-enumeration.md)