---
title: "配置防火墙以允许进行远程调试对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5912ebef0cd541bc6a7854a4de321019b1ef8ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>“为远程调试配置防火墙”对话框
当 Windows 防火墙阻止调试器在网络上接收信息时，会出现此对话框。 若要继续进行远程调试，您必须在防火墙上打开一个口以使调试器能够接收信息。  
  
> [!CAUTION]
>  如果在防火墙上打开一个口，可能会使计算机暴露在防火墙应该阻止的安全威胁之下。 在 Visual Studio 2015 中，打开一个口进行远程调试将取消阻止端口 4020 和 4021。 在其他版本的 Visual Studio 中，将使用其他端口号。 有关详细信息，请参阅[远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)。 此外，它还允许调试器打开其他端口。 有关详细信息，请参阅[配置 Windows 防火墙以进行远程调试](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **取消远程调试**  
 取消远程调试尝试。 计算机的安全设置保持不变。  
  
 **取消阻止从本地网络 （子网） 上的计算机进行远程调试**  
 启用本地子网中的计算机的远程调试。 这可能会将安全漏洞暴露给本地子网上的计算机，但是防火墙将继续阻止来自子网外的信息。  
  
 **取消阻止从任何计算机的远程调试**  
 启用网络上任何位置的计算机的远程调试。 此设置是最不安全的。  
  
## <a name="see-also"></a>另请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [远程调试](../debugger/remote-debugging.md)  
 [调试用户界面参考](../debugger/debugging-user-interface-reference.md)