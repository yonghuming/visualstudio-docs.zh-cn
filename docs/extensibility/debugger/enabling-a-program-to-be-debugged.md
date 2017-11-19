---
title: "启用要调试程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f1c38c110e9499936a24c33432180adf18209bf7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="enabling-a-program-to-be-debugged"></a>启用要调试程序
你的调试引擎 (DE) 可以调试的程序之前，你必须首先启动 DE 或将其附加到的现有程序。  
  
## <a name="in-this-section"></a>本节内容  
 [获取端口](../../extensibility/debugger/getting-a-port.md)  
 讨论如何为启用要调试程序的第一步获取端口。  
  
 [注册程序](../../extensibility/debugger/registering-the-program.md)  
 说明启用要调试程序的下一步： 注册端口。 注册后，可以调试程序通过附加或实时 (JIT) 调试的过程。  
  
 [附加到程序](../../extensibility/debugger/attaching-to-the-program.md)  
 介绍下一步： 将调试器附加到程序。  
  
 [启动基于附加](../../extensibility/debugger/launch-based-attachment.md)  
 描述为一个程序，这是 SDM 通过启动时自动启动基于附件。  
  
 [发送必需事件](../../extensibility/debugger/sending-the-required-events.md)  
 将指导你逐步创建调试引擎 (DE) 时所需的事件，并将其连接到的程序。  
  
## <a name="related-sections"></a>相关章节  
 [创建自定义调试引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 定义调试引擎 (DE)，并介绍通过 DE 接口和如何它们可能会导致不同的运行模式之间的转换调试器实现的服务。