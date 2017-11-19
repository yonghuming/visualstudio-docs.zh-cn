---
title: "端口供应商 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41c797d2c04c630d5aee7ff5ca2c0d5fc084026a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="port-suppliers"></a>端口供应商
在调试器体系结构，方面**端口供应商**:  
  
-   包含由服务器并提供有关对该服务器的请求的端口。  
  
-   可以添加和删除包含的服务器的端口。  
  
-   可以枚举具有提供给服务器的所有端口。  
  
-   由[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)接口，通过注册表注册 Visual Studio。 此接口可以通过调用获取[GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供一个默认端口供应商和默认端口。 如果需要实现一个自定义端口，自定义端口供应商还需要可实现以提供这些自定义端口。  
  
## <a name="see-also"></a>另请参阅  
 [服务器](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [端口](../../extensibility/debugger/ports.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)