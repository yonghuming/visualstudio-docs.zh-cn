---
title: "IScriptNode 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 788be3fe9cb5ba529e3d1ca653d4f0f5c35b5932
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnode-interface"></a>IScriptNode 接口
实现的对象`IScriptNode`接口表示网页。  
  
 除了从继承的方法`IUnknown`、`IScriptNode`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|指示对象是否仍处于活动状态。|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|添加的子实例`IScriptEntry`。|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|添加的子实例作为的 scriptlet `IScriptNode`。|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|删除对象树。|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|返回位于指定索引的节点中的子级。|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|返回一个用于将 scriptlet 与该主机对象相关联的应用程序定义值。|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|在父级的子列表中返回的对象的索引。|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|返回由当前的脚本节点的脚本语言。|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|返回的子节点的数目`IScriptNode`对象。|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|返回`IScriptNode`是对象的父级的对象。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本创作接口](../../winscript/reference/active-script-authoring-interfaces.md)