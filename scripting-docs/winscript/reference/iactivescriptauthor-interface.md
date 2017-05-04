---
title: "IActiveScriptAuthor 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptAuthor 接口"
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor 接口
生成服务，包括信息的IntelliSense和排序规则的Represents。  
  
 除了从 `IUnknown` 继承的方法之外，`IActiveScriptAuthor` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|添加一个根级项目的名称改为生成引擎的命名空间的脚本。  一个 *根级项目* 是可以包含属性和方法，即，也可以包含事件源的对象。|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|添加一个代码scriptlet作为根级别 `IScriptNode` 对象的子对象。  在宿主，scriptlet的完全限定名只能有两个级别。|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|添加一个类型库到脚本的命名空间。|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|返回设置请求的完成上下文的完成字符。|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|返回具有指定的属性的scriptlet。|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|返回类型信息和特定字符的定位点位置在代码块。  对于成员IntelliSense提供信息，全局列表和参数提示。|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|返回语言信息。|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|返回作者的脚本 `IScriptNode` 树的根。|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|返回scriptlet的文本属性。|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|返回脚本的文本特性块。|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|返回一个值特定字符是否应由应用程序执行语句结束。|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|分析脚本文本，添加文本到生成引擎来编写的脚本，并创建对应于该脚本块的 `IScriptEntry` 对象。|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|从生成引擎的脚本的命名空间取消 `NamedItem` 对象。|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|从生成引擎命名空间的脚本移除类型库。|  
  
## 请参阅  
 [活动脚本创作接口](../../winscript/reference/active-script-authoring-interfaces.md)