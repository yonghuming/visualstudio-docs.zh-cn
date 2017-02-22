---
title: "IDebugPortSupplier2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2"
helpviewer_keywords: 
  - "IDebugPortSupplier2 接口"
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口会议的端口提供调试管理器 \(SDM\)。  
  
## 语法  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## 实现者说明  
 自定义端口提供程序实现此接口表示端口提供程序。  
  
## 调用方的说明  
 为 `CoCreateInstance` 的调用和端口提供程序的 `GUID` 返回此接口 \(这是典型方式获取此接口\)。  例如：  
  
```cpp#  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 为 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) 的调用返回此接口，表示 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]当前使用的端口提供程序。  
  
 [GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md) 返回此接口，表示创建的端口提供程序。  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) 表示 `IDebugPortSupplier` 接口列表 \( `IEnumDebugPortSuppliers` 接口从 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)获取，表示任何端口提供程序注册用 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]\)。  
  
 调试引擎与端口提供程序通常不进行交互。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugPortSupplier2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|获取端口提供程序名称。|  
|[GetPortSupplierId](../Topic/IDebugPortSupplier2::GetPortSupplierId.md)|获取端口提供程序标识符。|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|从端口提供程序获取端口。|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|枚举已存在的端口。|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|验证端口提供程序支持添加新端口。|  
|[添加端口](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|添加一个端口。|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|移除端口。|  
  
## 备注  
 端口提供程序可以按名称标识自身和 ID，添加和移除端口和枚举端口提供程序提供的任何端口。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)