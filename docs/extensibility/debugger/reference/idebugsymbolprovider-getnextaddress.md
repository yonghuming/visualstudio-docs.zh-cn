---
title: "IDebugSymbolProvider::GetNextAddress |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
caps.latest.revision: 8
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
ms.openlocfilehash: 61f05a9cdde32717d6151a15cf7f8d2176c7ed60
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
获取遵循中方法的给定的调试地址的调试地址。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetNextAddress(   
   IDebugAddress*  pAddress,  
   BOOL            fStatementOnly,  
   IDebugAddress** ppAddress  
);  
```  
  
```csharp  
int GetNextAddress(   
   IDebugAddress     pAddress,  
   bool              fStatementOnly,  
   out IDebugAddress ppAddress  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pAddress`  
 [in]提供调试地址。  
  
 `fStatementOnly`  
 [in]如果为 TRUE，限制到单个语句的调试地址。  
  
 `ppAddress`  
 [out]返回下一个调试地址。  
  
## <a name="return-value"></a>返回值  
 返回一个有效`HRESULT`，通常，则为 S_OK。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
