---
title: "IDebugProperty2::GetExtendedInfo |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetExtendedInfo
helpviewer_keywords: IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7456ebe1e28618270bd90f09186ec49814c62b66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
获取扩展的属性的信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>参数  
 `guidExtendedInfo`  
 [in]确定要检索的扩展信息的类型的 GUID。 有关详细信息，请参阅备注。  
  
 `pExtendedInfo`  
 [out]返回`VARIANT`（c + +） 或对象 (C#) 可以用于检索的扩展的属性信息。 例如，此参数可能会返回`IUnknown`为查询的接口[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)接口。 有关详细信息，请参阅备注。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则返回错误代码。 返回`S_GETEXTENDEDINFO_NO_EXTENDEDINFO`如果没有任何要检索的扩展的信息。  
  
## <a name="remarks"></a>备注  
 此方法存在目的是为了检索信息不会将自身添加到通过调用正在检索[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。  
  
 由 （的 GUID 值为指定 C# 因为名称不可用任何程序集中） 此方法通常识别以下 Guid。 供内部使用，可以创建其他的 Guid。  
  
|名称|GUID|描述|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|返回`IUnknown`到文档的接口。 通常情况下， [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)接口可以获取从此`IUnknown`接口。|  
|guidCodeContext|{e2fc65e-56ce-11 d 1-b528-00aax004a8797}|返回`IUnknown`到文档上下文的接口。 通常情况下， [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)接口可以获取从此`IUnknown`接口。|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|返回一个包含自定义查看器通常由表达式计算器实现的 CLSID 的字符串。|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|返回一个 32 位数字，表示所需的插槽数，如果此属性表示托管的代码的本地地址。|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|返回一个包含与属性对象相关联的变量的签名字符串。|  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)