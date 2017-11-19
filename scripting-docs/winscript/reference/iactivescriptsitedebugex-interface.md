---
title: "IActiveScriptSiteDebugEx 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cf5849ff1fca282bace97774c6b7ac9e4510226
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx 接口
实现此接口和`IActiveScriptSiteDebug`接口如果你正在编写的主机，需要应用程序中看到一条通知的运行时错误，并选择性地附加的应用程序进行调试。 过程调试管理器提供了通过通知`IActiveScriptDebug`如果中实时脚本调试程序的计算机上找到。 如果没有时间就脚本调试器是发现，PDM 提供通过通知`IActiveScriptDebugEx`相反。  
  
 若要获取运行时错误的通知，你的主机必须处理[ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4)。 根据用户操作，你可以决定是否附加内部调试器并返回时，或者若要返回 OnScriptErrorDebug 中调试器的起始`pfEnterDebugger`参数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|通知主机有关脚本运行时错误过程调试管理器时未找到外部的实时调试器。|