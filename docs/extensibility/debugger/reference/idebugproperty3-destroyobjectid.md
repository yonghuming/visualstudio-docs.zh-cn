---
title: "IDebugProperty3::DestroyObjectID |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3::DestroyObjectID
helpviewer_keywords: IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ceae63b77f0797e0781318cfa362e735d995eb3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
销毁，该值指示调用方不再关注以标识此属性唯一地从所有其他属性与此属性关联的唯一 ID。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 如果调试引擎不需要支持的属性的唯一 Id （因为它已跟踪它们唯一内部），则它可以只返回`E_NOTIMPL`为此方法。  
  
 唯一的 Id 创建通过调用[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)当调用方想要确保此属性唯一地标识所有其他属性中的方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)