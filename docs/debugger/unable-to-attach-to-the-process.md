---
title: "无法附加到进程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.unable2attach
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ec2c181edc69ac2e693de96fcf72fe9116f758b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="unable-to-attach-to-the-process"></a>无法附加到进程
无法附加到进程。 在连接到此计算机期间服务器上的调试器组件接收了被拒绝的访问。  
  
 导致此错误的常见方案有两个：  
  
 **方案 1:**计算机 A 运行 Windows XP。 计算机 B 正在运行 Windows Server 2003。 计算机 B 上的注册表包含以下 DWORD 值：  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 用户 1 在计算机 B 上启动“终端服务器”会话（会话 1）并从该会话中启动托管应用程序。  
  
 是两台计算机上的管理员，2，用户登录到计算机 a。在这里，他或她尝试附加到在机 B.上会话 1 中运行的应用程序  
  
 **方案 2:**一个用户登录到两个计算机 A 和 B，位于同一工作组中，两台计算机上使用相同的密码。 调试器正在计算机 A 上运行并且尝试附加到在计算机 b。 计算机 A 上运行的托管应用程序有**网络访问： 本地帐户的共享和安全模型**设置为**来宾**。  
  
### <a name="to-solve-scenario-1"></a>解决方案 1  
  
-   在同一用户帐户名和密码下运行调试器和托管应用程序。  
  
### <a name="to-solve-scenario-2"></a>若要解决方案 2  
  
1.  从**启动**菜单上，选择**控制面板**。  
  
2.  在 Control Panel 中，双击**管理工具**。  
  
3.  在管理工具窗口中，双击**本地安全策略**。  
  
4.  在本地安全策略窗口中，选择**本地策略**。  
  
5.  在**策略**列中，双击**网络访问： 本地帐户的共享和安全模型**。  
  
6.  在**网络访问： 本地帐户的共享和安全模型**对话框框中，将本地安全设置更改为**经典**，然后单击**确定**。  
  
    > [!CAUTION]
    >    将安全模型更改为“传统型”可能会导致对共享文件和 DCOM 组件的意外访问。 如果进行此更改，则远程用户可以使用您的本地用户帐户（而不是“来宾”）进行身份验证。 如果某个远程用户与您的用户名和密码匹配，则该用户将能够访问您已对外共享的任何文件夹或 DCOM 对象。如果您使用此安全模型，请确保计算机上的所有用户帐户都具有强密码，或者为正在调试或已经调试过的计算机设置独立的网络孤岛以防止未经授权的访问。  
  
7.  关闭所有窗口。  
  
## <a name="see-also"></a>另请参阅  
 [调试器设置和准备](../debugger/debugger-settings-and-preparation.md)