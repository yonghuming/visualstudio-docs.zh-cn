---
title: "IDebugApplicationNode 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode 接口"
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugApplicationNode 接口
`IDebugApplicationNode` 接口通过提供在项树中的上下文扩展 `IDebugDocumentProvider` 接口的功能。  
  
 除了从 `IDebugDocumentProvider` 继承的方法之外，`IDebugApplicationNode` 接口还公开下面的方法。  
  
## 方法按Vtable顺序  
  
|方法|说明|  
|--------|--------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|此枚举应用程序节点的子节点。|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|返回此应用程序节点父节点。|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|将此应用程序节点的文档提供程序。|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|导致此应用程序释放所有引用并输入一个非活动状态。|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|将此应用程序节点到指定的项目树。|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|从项目中移除此应用程序节点。|