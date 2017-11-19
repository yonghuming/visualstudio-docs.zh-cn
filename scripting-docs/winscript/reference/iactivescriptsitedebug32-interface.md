---
title: "IActiveScriptSiteDebug32 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: a752851aa6afd903747dc58fed79d2bc5b27e3e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 接口
智能主机实现`IActiveScriptSiteDebug32`接口进行文档管理和参与调试。 `IActiveScriptSite`对象通常提供的实现`IActiveScriptSiteDebug32`接口。 如果此操作后，调用`IActiveScriptSite::QueryInterface`方法来获取`IActiveScriptSiteDebug32`接口。  
  
 除了从继承的方法`IUnknown`、`IActiveScriptSiteDebug32`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|返回与此脚本站点关联的调试应用程序对象。|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|语言引擎用于委派`IDebugCodeContext::GetSourceContext`。|