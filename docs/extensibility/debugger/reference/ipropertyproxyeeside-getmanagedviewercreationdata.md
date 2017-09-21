---
title: "IPropertyProxyEESide::GetManagedViewerCreationData |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: 12
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
ms.openlocfilehash: 221d26b43f57c5519747ef04e9ccc17fc9fad10e
ms.lasthandoff: 02/22/2017

---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
为了实例化该查看器检索有关此属性类型的查看器的信息。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```c#  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### <a name="parameters"></a>参数  
 `assemName`  
 [out]返回该对象的程序集的名称。  
  
 `assemBytes`  
 [out]返回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)对象，其中包含此对象 （如果不可用的任何字节，这是一个 null 值） 的程序集字节。  
  
 `assemPdb`  
 [out]返回`IEEDataStorage`对象，其中包含该符号将存储该对象的信息 （没有符号存储区是否可用，这是一个 null 值）。  
  
 `className`  
 [out]返回包含此对象的类名。  
  
 `alr`  
 [out]返回一个介于[ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)枚举，指示该程序集的位置。  
  
 `replacementOk`  
 [out]返回非零值 (`TRUE`) 可以更改此对象的值; 如果为零 (`FALSE`) 如果对象是只读的。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 类型的可视化工具使用此方法来实例化托管的查看器。  
  
## <a name="see-also"></a>另请参阅  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
