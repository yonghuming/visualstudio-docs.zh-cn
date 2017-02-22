---
title: "实现和注册端口提供程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]、 注册端口的供应商"
  - "注册的端口供应商"
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 实现和注册端口提供程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

端口提供程序的角色是跟踪，并提供端口，或托管进程。  在端口需要创建时，端口提供实例化使用端口提供程序 GUID 的共同创建 \(会议调试管理器 SDM \[\] 将使用端口提供用户选定或端口提供程序由项目系统指定的\)。  SDM 将调用 [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) 发现任何端口是否可以添加。  如果端口可以添加，新端口通过调用 [添加端口](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 并将描述端口的该 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) 请求。  `AddPort` 将返回 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 接口表示的新端口。  
  
## 讨论  
 端口由端口提供程序创建的，这与设备或调试服务器。  服务器可以通过[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) 方法枚举其端口提供程序，并且，端口提供程序可以通过 [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) 方法枚举其端口。  
  
 除了典型的 COM 注册，端口提供程序之外通过将其 CLSID 和名称必须与 Visual Studio 注册在特定注册表位置。  debugging SDK 帮助器函数调用 `SetMetric` 处理此差事:因此它一次调用以便注册每个项，例如:  
  
```cpp#  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricCLSID,  
          <CLSID of your port supplier>,  
          false,  
          NULL)  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricName,  
          <name of your port supplier>,  
          false,  
          NULL);  
```  
  
 端口提供注销通过调用 `RemoveMetric` \(另一个 debugging SDK 帮助器函数\) 因此注册的每个项，例如:  
  
```cpp#  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricCLSID,  
             NULL);  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricName,  
             NULL);  
```  
  
> [!NOTE]
>  [SDK 帮助器调试](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` 和 `RemoveMetric` 是静态函数定义在 dbgmetric.h 并编译成 ad2de.lib。  `metrictypePortSupplier`、 `metricCLSID`和`metricName` 帮助器在 dbgmetric.h 还定义。  
  
 端口提供程序可以通过方法 [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) 和 [GetPortSupplierId](../Topic/IDebugPortSupplier2::GetPortSupplierId.md)提供其名称和 GUID，分别。  
  
## 请参阅  
 [实现端口提供程序](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [SDK 帮助器调试](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [端口供应商](../../extensibility/debugger/port-suppliers.md)