---
title: "ICanHandleException::CanHandleException |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ICanHandleException.CanHandleException
apilocation: scrobj.dll
helpviewer_keywords: ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15612330f160f694202bb2158f970e0633fe53bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
确定脚本引擎的调用方可以处理指定的异常。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pExcepInfo`  
 [in]指向`EXCEPINFO`结构，它包含发现没有异常处理程序的情况下报告的信息。  
  
 `pvar`  
 [in]与异常，如由引发值关联的值`throw`语句。 此参数可以为 `NULL`。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|调用方能够处理该异常|  
|`E_FAIL`|调用方无法处理的异常。|  
  
## <a name="remarks"></a>备注  
 如果调用`IDispatchEx::InvokeEx`，或类似方法，将引发异常，支持的脚本的调用方链中的调用方的脚本引擎检查`ICanHandleException`接口，并指示它能够处理该异常。 如果没有调用方可以处理异常，就会停止脚本引擎。  
  
## <a name="see-also"></a>另请参阅  
 [ICanHandleException 接口](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)