---
title: "安全问题 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 12
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
ms.sourcegitcommit: 98a4c85118fc836e1f8922a24700036c9d4837cb
ms.openlocfilehash: fcc65d94f8348674110db6cc0a87e0e3020a4683
ms.lasthandoff: 02/22/2017

---
# <a name="security-issues"></a>安全性问题
若要调试使用 Visual Studio 的某个程序，所需的唯一权限是相同的开发人员需要运行该程序。 这包括大多数情况下 （涉及其他服务，如 Internet 信息服务，某些情况下可能需要更高级别的权限） 的远程调试。  
  
 在 Visual Studio 运行时，进程调试管理器 (PDM) 将跟踪在本地计算机上的调试进程。 远程开发人员处理远程调试，并使 PDM 可用由启动一个名为 msvsmon.exe 程序。 （请注意该 msvsmon.exe 不是服务，必须手动启动，以启用该计算机上的远程调试）。当 Visual Studio （或 msvsmon.exe） 未运行时，没有进程被跟踪进行调试。  
  
 这意味着开发人员可以调试的程序他或她开始使用任何特殊权限。 开发人员甚至可以调试相同的安全组的成员的其他人是否被其他人启动的进程。 若要启用远程调试，因此需要就只复制所需的文件复制到远程计算机并且启动 msvsmon.exe (请参阅[远程调试](../../debugger/remote-debugging.md)的更多详细信息)。  
  
## <a name="see-also"></a>另请参阅  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)   
 [进程调试管理器](../../extensibility/debugger/process-debug-manager.md)   
 [远程调试](../../debugger/remote-debugging.md)
