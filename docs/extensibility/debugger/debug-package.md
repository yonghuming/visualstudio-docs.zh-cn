---
title: "调试包 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eccd258476f82871732ef7b16f0282d2f945b9ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debug-package"></a>调试包
调试包在 Visual Studio shell 中运行，并处理所有 UI。 它使用 Visual Studio 调试接口，并与会话调试管理器 (SDM) 进行通信。  
  
 通过 SDM 发送的中断事件切换从运行模式调试器中断模式，并将焦点更改到程序发生中断的位置。 调试包发送给它的事件的信息从跟踪的堆栈帧和线程。  
  
 调试包不包含语言或运行时环境依赖关系。 不需要实现或修改调试包。  
  
 由 vsdebug.dll 实现调试包。  
  
## <a name="see-also"></a>另请参阅  
 [会话调试管理器](../../extensibility/debugger/session-debug-manager.md)   
 [堆栈帧](../../extensibility/debugger/stack-frames.md)   
 [线程](../../extensibility/debugger/threads.md)   
 [调试器组件](../../extensibility/debugger/debugger-components.md)