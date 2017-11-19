---
title: "IDebugDocumentProvider 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 262794718e238068cfd9a8e3fae5161b9fe8cc54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentprovider-interface"></a>IDebugDocumentProvider 接口
提供了一种用于实例化上请求的文档。  
  
## <a name="remarks"></a>备注  
 用于实例化文档的这间接意味着：  
  
-   允许要在需要时加载的文档。  
  
-   允许要包含在调试器 IDE 的文档对象。  
  
-   允许多个用于访问相同的文档对象的方法。  
  
 这有效地从其提供程序分隔文档，并允许提供程序来执行其他运行时上下文信息。  
  
 除了从继承的方法`IDebugDocumentInfo`、`IDebugDocumentProvider`接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|使文档后，如果不存在要实例化。|