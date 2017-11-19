---
title: "IDebugCustomViewer::DisplayValue |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomViewer::DisplayValue
helpviewer_keywords: IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 701c5e33273dc6d00156e554e1abaa9a003568eb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
调用此方法以显示指定的值。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```csharp  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### <a name="parameters"></a>参数  
 `hwnd`  
 [in]父窗口  
  
 `dwID`  
 [in]支持多个类型的自定义查看器的 ID。  
  
 `pHostServices`  
 [in]保留。 始终设置为 null。  
  
 `pDebugProperty`  
 [in]可以用于检索要显示的值的接口。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则返回错误代码。  
  
## <a name="remarks"></a>备注  
 此方法将创建必要的窗口，显示的值、 等待输入，然后关闭该窗口，所有在返回给调用方之前，显示为"模式"。 这意味着该方法必须处理的显示属性的值，从创建到等待用户输入，到销毁窗口输出的窗口的所有方面。  
  
 若要支持上更改的值给定[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)对象时，可以使用[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)方法-如果值可以表示为一个字符串。 否则，它是创建自定义接口所需-专用于实现该表达式计算器`DisplayValue`方法-实现对同一对象`IDebugProperty3`接口。 此自定义接口将提供用于更改任意大小或复杂的数据。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)