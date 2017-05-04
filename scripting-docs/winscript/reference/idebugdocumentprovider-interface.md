---
title: "IDebugDocumentProvider 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentProvider 接口"
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentProvider 接口
用于实例化文档提供方法在需要时。  
  
## 备注  
 这种间接方式表示用于实例化文档：  
  
-   在需要时，允许文档加载。  
  
-   允许文档对象在调试器IDE中。  
  
-   支持多种方法访问同一文档对象。  
  
 这将从其提供程序有效分离文档并允许提供程序具有不同的运行时，上下文信息。  
  
 除了从 `IDebugDocumentInfo` 继承的方法之外，`IDebugDocumentProvider` 接口还公开下面的方法。  
  
|方法|说明|  
|--------|--------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|如果它已不存在，使文档实例化。|