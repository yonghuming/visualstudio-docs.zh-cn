---
title: "安全问题 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8061c419f81493e56a58df8fefbe4d3362d43e46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="security-issues"></a>安全性问题
若要调试使用 Visual Studio 的程序，所需的唯一权限是相同的开发人员需要运行程序。 这包括大多数情况下 （涉及其他服务，如 Internet 信息服务中，某些情况下可能需要更高级别的权限） 的远程调试。  
  
 在 Visual Studio 运行时，过程调试管理器 (PDM) 在本地计算机上跟踪调试进程。 远程，一个名为 msvsmon.exe 程序启动由开发人员能够处理远程调试，并使 PDM 可用。 （请注意该 msvsmon.exe 不是服务，必须手动启动，以启用该计算机上的远程调试）。如果未运行 Visual Studio （或 msvsmon.exe），针对调试不跟踪任何进程。  
  
 这意味着开发人员可以调试的程序他或她入门任何特殊权限。 开发人员甚至可以调试该其他人是否相同的安全组的成员由其他人启动的进程。 并且若要启用远程调试，有必要仅复制所需文件复制到远程计算机，并启动 msvsmon.exe (请参阅[远程调试](../../debugger/remote-debugging.md)有关详细信息)。  
  
## <a name="see-also"></a>另请参阅  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)   
 [过程调试管理器](../../extensibility/debugger/process-debug-manager.md)   
 [远程调试](../../debugger/remote-debugging.md)