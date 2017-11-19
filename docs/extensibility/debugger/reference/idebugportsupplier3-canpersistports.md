---
title: "IDebugPortSupplier3::CanPersistPorts |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords: IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 95e62f283d2ea0411162fb0406c712f0d17a1183
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
此方法可确定是否端口提供程序可以调用调试器之间 （通过其写入到磁盘） 中保留端口。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>参数  
 无。  
  
## <a name="return-value"></a>返回值  
 `S_OK`如果端口可以保持不变，或`S_FALSE`以指示不保留端口。  
  
## <a name="remarks"></a>备注  
 如果端口供应商可以保留端口，它应被销毁时这样操作，然后重新加载它们再一次实例化时。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)