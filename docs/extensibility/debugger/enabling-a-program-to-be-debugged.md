---
title: "启用要进行调试的程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 66daff038c7556a693964d5dabc4de054990d791
ms.lasthandoff: 02/22/2017

---
# <a name="enabling-a-program-to-be-debugged"></a>启用要进行调试的程序
您的调试引擎 (DE) 可以调试的程序之前，必须首先启动 DE 或将其附加到现有的程序。  
  
## <a name="in-this-section"></a>本节内容  
 [获取一个端口](../../extensibility/debugger/getting-a-port.md)  
 讨论如何启用要进行调试的程序的第一步中获得一个端口。  
  
 [注册程序](../../extensibility/debugger/registering-the-program.md)  
 介绍启用要进行调试的程序的下一步︰ 注册该端口。 注册后，可以调试程序通过将附加或实时 (JIT) 调试的过程。  
  
 [将附加到程序](../../extensibility/debugger/attaching-to-the-program.md)  
 介绍下一步︰ 将调试器附加到该程序。  
  
 [启动基于附加](../../extensibility/debugger/launch-based-attachment.md)  
 描述为一个程序，这是通过 SDM 启动时自动启动基于附件。  
  
 [发送所需的事件](../../extensibility/debugger/sending-the-required-events.md)  
 将指导你一步步创建调试引擎 (DE) 时所需的事件，并将其连接到的程序。  
  
## <a name="related-sections"></a>相关章节  
 [创建自定义调试引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 定义调试引擎 (DE)，并介绍通过 DE 接口和如何它们可能会导致不同的操作模式之间的转换到调试器中实现的服务。
