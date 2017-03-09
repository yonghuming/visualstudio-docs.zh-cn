---
title: "“为远程调试配置防火墙”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.firewallconfiguration"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "“为远程调试配置防火墙”对话框"
  - "远程调试，配置防火墙"
  - "防火墙，为远程调试配置"
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “为远程调试配置防火墙”对话框
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当 Windows 防火墙阻止调试器在网络上接收信息时，会出现此对话框。 若要继续进行远程调试，您必须在防火墙上打开一个口以使调试器能够接收信息。  
  
> [!CAUTION]
>  如果在防火墙上打开一个口，可能会使计算机暴露在防火墙应该阻止的安全威胁之下。 在 Visual Studio 2015 中，打开一个口进行远程调试将取消阻止端口 4020 和 4021。 在其他版本的 Visual Studio 中，将使用其他端口号。 有关详细信息，请参阅[远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)。 此外，它还允许调试器打开其他端口。 有关详细信息，请参阅[配置 Windows 防火墙以便进行远程调试](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。  
  
## UIElement 列表  
 **取消远程调试**  
 取消远程调试尝试。 计算机的安全设置保持不变。  
  
 **取消禁止从本地网络\(子网\)中的计算机进行远程调试的限制**  
 启用本地子网中的计算机的远程调试。 这可能会将安全漏洞暴露给本地子网上的计算机，但是防火墙将继续阻止来自子网外的信息。  
  
 **取消禁止从任何计算机进行远程调试的限制**  
 启用网络上任何位置的计算机的远程调试。 此设置是最不安全的。  
  
## 请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [在设备上安装远程工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [调试用户界面参考](../debugger/debugging-user-interface-reference.md)