---
title: "由 IDE 实现的回调函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fbc71942a87685a4011b13d1054c4855a5e18012
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="callback-functions-implemented-by-the-ide"></a>由 IDE 实现的回调函数
若要与集成为尽可能并提供一种统一的最终用户体验，无缝集成的开发环境 (IDE) 的源代码管理插件可以使用由 IDE 实现的回调函数。 该插件可调用这些函数在适当的时间，在源代码管理操作将信息传递到 IDE;IDE 然后可以显示此信息作为其本机用户界面中的嵌入元素。 用户在这种情况下，如果该插件，则采用其自己的 UI 比具有更少碎片的体验。  
  
 必需的标头文件是 scc.h。 默认位置是 \Program Files\VSIP 8.0\EnvSDK\common\inc\\。 它也是在 \Program Files\VSIP 8.0\MSSCCI 有源控件插件示例的 VSIP 文件夹\\。  
  
## <a name="in-this-section"></a>本节内容  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 描述由回调函数[SccOpenProject](../extensibility/sccopenproject-function.md)来从源代码管理插件通过 IDE 显示消息。  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 描述由回调函数[SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE 不具有完全访问权限的信息的仅供源代码管理插件，如版本控制下的文件的完整列表。  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 描述由回调函数[SccQueryChanges](../extensibility/sccquerychanges-function.md)操作。  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 描述由回调函数[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)操作。  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 描述通过调用设置的回调函数[SccSetOption](../extensibility/sccsetoption-function.md)启用源代码管理插件进行通信的名称更改回 IDE。  
  
## <a name="related-sections"></a>相关章节  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 打开一个项目。  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 检查以了解其当前状态的文件的列表。 此外，使用`pfnPopulate`函数以在文件不匹配的条件时通知调用方`nCommand`。  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 检查中一个项目或项目受源代码管理目录和文件的列表。 找到每个目录和文件名称传递给回调函数。  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 检查已对文件的列表的名称更改。 每个文件名传递给回调函数以及其更改状态。  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 设置各种选项。 每个选项开头`SCC_OPT_xxx`并具有其自己定义的一组值。  
  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)  
 描述源控件插件 SDK 的参考部分的内容。