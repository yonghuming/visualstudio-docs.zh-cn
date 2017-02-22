---
title: "IDebugProperty2::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

扩展属性的信息。  
  
## 语法  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```c#  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### 参数  
 `guidExtendedInfo`  
 \[in\] 确定要检索的扩展的信息类型的 GUID。  请参见 " 备注 " 了解详细信息。  
  
 `pExtendedInfo`  
 \[out\] 返回可用于检索扩展属性信息的 `VARIANT` \(C\+\+\) 或对象 \(c\# 中\)。  例如，此参数可能返回可用于 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) 接口要查询的 `IUnknown` 接口。  请参见 " 备注 " 了解详细信息。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  ; 如果没有检索，的扩展的信息返回 `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` 。  
  
## 备注  
 此方法对于检索不适用于检索通过调用 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 方法的信息的目的存在。  
  
 下面的 GUID 此方法通常认可 \(GUID 值对于 C\# 指定，因为该名称不在任何程序集\)。  附加的 GUID 可以创建以供内部使用。  
  
|名称|GUID|说明|  
|--------|----------|--------|  
|guidDocument|{} 3f98de84\-fee9\-11d0\-b47f\-00a0244a1dd2|返回 `IUnknown` 接口到文档中。  通常， [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) 接口可以通过此 `IUnknown` 接口来获得。|  
|guidCodeContext|{} e2fc65e\-56ce\-11d1\-b528\-00aax004a8797|返回 `IUnknown` 接口添加到文档上下文。  通常， [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 接口可以通过此 `IUnknown` 接口来获得。|  
|guidCustomViewerSupported|{} d9c9da31\-ffbe\-4eeb\-9186\-23121e3c088c|返回一个自定义浏览器的 CLSID 的字符串，通常实现由表达式计算器。|  
|guidExtendedInfoSlot|{} 6df235ad\-82c6\-4292\-9c97\-7389770bc42f|，如果该属性表示托管代码本地地址，返回表示预期插槽号的 32 位数字。|  
|guidExtendedInfoSignature|{} b5fb6d46\-f805\-417f\-96a3\-8ba737073ffd|返回包含该变量的签名字符串与属性关联的对象。|  
  
## 请参阅  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)