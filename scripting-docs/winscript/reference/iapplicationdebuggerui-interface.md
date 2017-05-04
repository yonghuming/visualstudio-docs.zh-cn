---
title: "IApplicationDebuggerUI 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IApplicationDebuggerUI 接口"
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI 接口
实现由调试器集成开发环境\(IDE\) \(除了 `IApplicationDebugger`\)为外部组件到调试器的用户界面\(UI\)的多个控件。  
  
 除了从 `IUnknown` 继承的方法之外，`IApplicationDebuggerUI` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|将包含窗口指定调试在调试器用户界面的顶级文档。|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|将包含窗口提供在调试器用户界面和滚动的顶级文档上下文窗口到上下文。|