---
title: "IApplicationDebuggerUI 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbaa04f6790ffc4d80447a6745ca82cc8dba6802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerui-interface"></a>IApplicationDebuggerUI 接口
由调试器集成的开发环境 (IDE) 实现 (除了`IApplicationDebugger`) 以提供更好地控制调试器的用户界面 (UI) 的外部组件。  
  
 除了从继承的方法`IUnknown`、`IApplicationDebuggerUI`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|将包含到调试器中的顶部的指定的调试文档窗口带用户界面。|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|将包含到调试器用户界面中的顶部的给定的文档上下文的窗口，并将窗口滚动到上下文。|