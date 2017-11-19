---
title: "IActiveScriptSiteDebug 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b36054deeceb0528fb7ea399cc41d8edbbb47e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug-interface"></a>IActiveScriptSiteDebug 接口
智能主机实现`IActiveScriptSiteDebug`接口进行文档管理和参与调试。 `IActiveScriptSite`对象通常提供的实现`IActiveScriptSiteDebug`接口。 如果此操作后，调用`IActiveScriptSite::QueryInterface`方法来获取`IActiveScriptSiteDebug`接口。  
  
 除了从继承的方法`IUnknown`、`IActiveScriptSiteDebug`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|语言引擎用于委派`IDebugCodeContext::GetSourceContext`。|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|返回与此脚本站点关联的调试应用程序对象。|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|获取应在脚本下添加文档的应用程序节点。|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|允许智能主机，以便确定如何处理运行时错误。|