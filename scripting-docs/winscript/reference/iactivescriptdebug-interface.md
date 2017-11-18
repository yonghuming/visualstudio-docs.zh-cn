---
title: "IActiveScriptDebug 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1e1d0c1cf51c63f1bb3fcd90ae72520da907e50
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebug-interface"></a>IActiveScriptDebug 接口
由脚本引擎实现，支持调试。 通常，实现的对象`IActiveScriptDebug`接口还实现`IActiveScript`接口。 如果出现这种情况，调用`IActiveScript::QueryInterface`方法来获取`IActiveScriptDebug`接口。  
  
 `IActiveScriptDebug`接口提供了有关方式：  
  
-   若要接管文档管理的智能主机。  
  
-   过程调试管理器，若要同步的多个脚本引擎调试。  
  
 除了从继承的方法`IUnknown`、`IActiveScriptDebug`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|返回脚本文本的任意块的文本属性。|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|返回任意 scriptlet 的文本属性。|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|委托给`IDebugDocumentContext::EnumCodeContexts`。|