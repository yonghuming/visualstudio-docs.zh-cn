---
title: "IDebugApplication110::SynchronousCallInMainThread |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplication110::SynchronousCallInMainThread
ms.assetid: 57475ae5-1520-45ef-800d-ccfc6235a5d1
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef52ebfe8bfccecc0eea2383787a5b2698a5ce5f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication110synchronouscallinmainthread"></a>IDebugApplication110::SynchronousCallInMainThread
主线程上进行同步调用。  
  
> [!IMPORTANT]
>  [IDebugApplication110 接口](../../winscript/reference/idebugapplication110-interface.md)是实现由 PDM v11.0 和更高版本。 在 activdbg100.h 中发现。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>参数  
 `pptc`  
 [IDebugThreadCall 接口](../../winscript/reference/idebugthreadcall-interface.md)对象调用。  
  
 `dwParam1`  
 调用的第一个参数。  
  
 `dwParam1`  
 调用的第一个参数。  
  
 `dwParam2`  
 调用第二个参数。  
  
 `dwParam3`  
 调用的第三个参数。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugApplication110 接口](../../winscript/reference/idebugapplication110-interface.md)