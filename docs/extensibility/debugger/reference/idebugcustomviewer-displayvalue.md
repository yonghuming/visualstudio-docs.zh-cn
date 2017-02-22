---
title: "IDebugCustomViewer::DisplayValue | Microsoft Docs"
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
  - "IDebugCustomViewer::DisplayValue"
helpviewer_keywords: 
  - "IDebugCustomViewer::DisplayValue"
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法调用显示为指定值。  
  
## 语法  
  
```cpp#  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```c#  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### 参数  
 `hwnd`  
 \[in\] 父窗口  
  
 `dwID`  
 \[in\] 支持多个类型的自定义浏览器的 ID。  
  
 `pHostServices`  
 \[in\] 已保留。  始终设置为 null。  
  
 `pDebugProperty`  
 \[in\] 可用于检索将显示的值的接口。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  
  
## 备注  
 该显示为 “模式”此方法将创建必要的窗口，其中显示值，等待输入，然后关闭窗口，都在返回到调用方之前。  这意味着该方法必须处理显示属性值的所有方面，从创建输出的 " 窗口中，将等待的用户输入，对销毁窗口。  
  
 —，如果值可以表示为字符串，若要支持更改在特定 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 对象的值，可以使用 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) 方法。  否则，创建自定义接口独占实现方法在同一对象的表达式计算器此 `DisplayValue` 实现 `IDebugProperty3` 接口是必需的。  此自定义接口将提供更改的任意大小或复杂的数据方法。  
  
## 请参阅  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)