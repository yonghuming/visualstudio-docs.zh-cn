---
title: "IActiveScriptAuthor 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37abb356ab24d64a05a1f1209809d63e2f55e228
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor 接口
表示创作服务，包括 IntelliSense 和排序规则的信息。  
  
 除了从继承的方法`IUnknown`、`IActiveScriptAuthor`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|将根级别项的名称添加到引擎的命名空间创作的脚本。 A*根级别项*是可以包含属性和方法，并且，还可以包含事件源的对象。|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|为根级别的子项添加代码 scriptlet`IScriptNode`对象。 在宿主，scriptlet 的完全限定的名称可以具有只有两个级别。|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|将类型库添加到脚本的命名空间。|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|返回的请求的完成上下文的完成字符集。|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|返回具有指定的属性的 scriptlet。|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|返回类型的代码块中的信息和给定的字符的定位点位置。 IntelliSense、 全局列表和参数提示，本文提供有关成员的信息。|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|返回语言信息。|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|返回`IScriptNode`作者脚本树的根。|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|返回 scriptlet 的文本属性。|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|返回一个脚本块的文本属性。|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|返回一个值，该值指示给定的字符是否应由应用程序提交语句结束。|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|分析脚本文本，将文本添加到创作的脚本创作引擎，并创建`IScriptEntry`对应于脚本块的对象。|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|删除`NamedItem`从脚本创作引擎的命名空间的对象。|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|从创作引擎命名空间的脚本中删除类型库。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本创作接口](../../winscript/reference/active-script-authoring-interfaces.md)