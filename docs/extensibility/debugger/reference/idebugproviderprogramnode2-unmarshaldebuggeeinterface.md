---
title: "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1801f2df2dfff7667e8a9991892b3218dc3bb71a
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
跨进程边界中获取指定的接口。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>参数  
 `riid`  
 [in]若要获取接口的 GUID。  
  
 `ppvObject`  
 [out]返回实现所需的接口的对象。 [C + +] 这可以直接为所需的接口类型强制转换。 [C#] 使用<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>方法以获取所需的接口。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 当在运行时的调试引擎使用此方法[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]进程空间和正在调试的程序在其自己的进程空间中运行。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
