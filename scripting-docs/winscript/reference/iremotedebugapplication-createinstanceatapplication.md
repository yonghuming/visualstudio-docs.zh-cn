---
title: "IRemoteDebugApplication::CreateInstanceAtApplication |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplication.CreateInstanceAtApplication
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2185987f6b635dae4d537231fca3327d0aed003
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
允许应用程序进程中创建对象，通过代码，它是-进程外应用程序。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>参数  
 `rclsid`  
 [in]类标识符 (CLSID) 的要创建的对象。  
  
 `pUnkOuter`  
 [in]如果`NULL`，并未作为聚合的一部分创建的对象。 否则为`pUnkOuter`是指向聚合对象的指针`IUnknown`接口 (控制`IUnknown`)。  
  
 `dwClsContext`  
 [in]运行可执行代码的上下文。 值，将从枚举`CLSCTX`。  
  
 `riid`  
 [in]使用与对象进行通信的接口标识符。  
  
 `ppvObject`  
 [out]接收请求中的接口指针的指针变量的地址`riid`。 在成功返回时，*`ppvObject`包含请求的接口指针。 在失败\*`ppvObject`包含`NULL`。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法委托给`CoCreateInstance`。  
  
## <a name="see-also"></a>另请参阅  
 [IRemoteDebugApplication 接口](../../winscript/reference/iremotedebugapplication-interface.md)