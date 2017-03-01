---
title: "IDebugCoreServer2::GetMachineUtilities_V7 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 17
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8cec5befece6b3415a903ed84d8d31cbe3988ee8
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
此方法获取服务器的计算机的实用程序。  
  
> [!NOTE]
>  此方法已过时︰ 请不要使用 ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]始终返回`E_NOTIMPL`如果调用此方法)。 它将保留历史原因造成的。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```c#  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppUtil`  
 [out]返回`IDebugMDMUtil2_V7`表示该计算机的实用程序信息的接口。  
  
## <a name="return-value"></a>返回值  
 始终返回`E_NOTIMPL`，指示未实现方法。  
  
## <a name="remarks"></a>备注  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]始终返回`E_NOTIMPL`如果调用此方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
