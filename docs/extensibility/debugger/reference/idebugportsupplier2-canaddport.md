---
title: "IDebugPortSupplier2::CanAddPort |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier2::CanAddPort
helpviewer_keywords: IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6f19d220f8638b84e194ab1604816ed767d10c41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
验证端口供应商可以添加新端口。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>返回值  
 如果可以添加端口，则返回`S_OK`; 否则为返回`S_FALSE`以指示无端口可以添加到此端口供应商。  
  
## <a name="remarks"></a>备注  
 调用此方法之前调用[添加](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)由于后一种方法将创建该端口，以及添加它，这可能会耗时的操作的方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [添加](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)