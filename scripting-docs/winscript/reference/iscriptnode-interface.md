---
title: "IScriptNode 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptNode 接口"
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IScriptNode 接口
对象实现 `IScriptNode` 接口表示网页。  
  
 除了从 `IUnknown` 继承的方法之外，`IScriptNode` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|指示对象是否处于活动状态。|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|添加 `IScriptEntry`子实例。|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|添加一scriptlet作为 `IScriptNode`的子实例。|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|删除对象树。|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|返回位于节点的指定索引处的子级。|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|返回用于将scriptlet与宿主对象的应用程序定义的值。|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|返回一个对象的索引在父的子元素的列表。|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|返回当前节点脚本使用的脚本语言。|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|返回 `IScriptNode` 对象的子节点的数目。|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|返回一个对象的父级的 `IScriptNode` 对象。|  
  
## 请参阅  
 [活动脚本创作接口](../../winscript/reference/active-script-authoring-interfaces.md)