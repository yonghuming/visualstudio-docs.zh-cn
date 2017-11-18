---
title: "配置 Windows 防火墙以允许远程调试 |Microsoft 文档"
ms.custom: 
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9432c65ec6a481b23655fb2a92915a4a4365ed5e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>配置 Windows 防火墙以便进行远程调试
本主题介绍如何配置防火墙以在运行以下操作系统的计算机上启用远程调试：  
  
-   Windows 10  
  
-   Windows 8/8.1  
  
-   Windows 7   
  
-   Windows Server 2012 R2  

-   Windows Server 2012
  
-   Windows Server 2008 R2 
  
 如果正在调试的网络不受防火墙保护，则此配置是不必要的。 否则，承载 Visual Studio 的计算机和要调试的远程计算机均需要对防火墙配置的更改。  
  
 “” If your network requires that communication be performed using , you must open additional ports on both the Visual Studio host computer and the remote computer.  
  
 “Web 服务器” 如果你正在调试远程 Web 服务器，则必须打开远程计算机上的其他端口。 （有关 IIS 中，端口 80 必须打开。）  
  
 请注意，这两台计算机不需要运行相同的操作系统。 例如，Visual Studio 计算机可以运行 Windows 10，而远程计算机可以运行 Windows Server 2012 R2。      
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>启用远程调试的远程计算机上的端口  
  
|||||  
|-|-|-|-|  
|**端口**|**传入/传出**|**协议**|**描述**|   
|4022|传入|TCP|有关 VS 自 2017 年。 端口号针对每个 Visual Studio 版本递增 2。 有关详细信息，请参阅[Visual Studio 远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)。|  
|4023|传入|TCP|有关 VS 自 2017 年。 端口号针对每个 Visual Studio 版本递增 2。 （仅用于远程调试从远程调试器的 64 位版本的 32 位进程。）有关详细信息，请参阅[Visual Studio 远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)。| 
|3702|传出|UDP|（可选）所需的远程调试器发现。|    
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>如何在 Windows 防火墙中配置端口  

在安装 Visual Studio 或远程调试器时，该软件将尝试打开相应的端口。 但是，在某些情况下 （例如，使用第三方防火墙），你可能需要手动打开一个端口。 如果你需要验证端口已打开，请参阅[故障排除](#troubleshooting)。 一些有关打开端口的说明可能会较旧版本的 Windows 上有所不同。

若要打开一个端口：
  
1. 打开**启动**菜单中，搜索**高级安全 Windows 防火墙**。

2. 然后选择**入站规则 > 新规则 > 端口**，然后单击**下一步**。 (对于传出规则选择**出站规则**相反。)

3. 选择**TCP**或**UDP**，取决于的端口号。

4. 下**特定本地端口**，输入端口号，单击**下一步**。

5. 单击**允许连接**，然后单击**下一步**。

6. 选择要为端口启用并单击的一个或多个网络类型**下一步**。

    你选择的类型必须包括远程计算机连接到的网络。
7. 添加名称 (例如， **msvsmon**， **IIS**，或**Web 部署**) 规则和单击**完成**。

    你应该看到你在入站规则或出站规则列表中的新规则。

## <a name="troubleshooting"></a>故障排除

如果你有使用远程调试器附加到你的应用程序的问题，你可能需要验证打开了正确的端口。

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-visual-studio-computer"></a>验证在 Visual Studio 计算机上的 Windows 防火墙中打开端口  
 有关配置 Windows 防火墙的说明在不同操作系统上略有不同。 在 Windows 8/8.1、 Windows 10 和 Windows Server 2012，word**应用**使用; 在 Windows 7 或 Windows Server 2008 中，word**程序**使用; 在以下步骤中，我们将使用 word**应用**。  
  
1.  打开 Windows 防火墙页。 （在“启动”  菜单搜索框中，键入“Windows 防火墙” 。）  
  
2.  单击“允许应用或功能通过 Windows 防火墙” 。  
  
3.  在“允许的应用和功能”  列表中，查找“Visual Studio 远程调试器发现” 。 如果已列出，请确保该选项被选中，并且同时选中一个或多个网络类型。  
  
4.  如果未列出“Visual Studio 远程调试器发现”  ，请单击“允许其他应用” 。 如果你仍未看到它在**添加应用程序**窗口中，单击**浏览**并导航到 **\<Visual Studio 安装目录 > \Common7\IDE\Remote 调试器**. 为应用程序 (x86, x64, Appx) 查找适当的文件夹，然后选择“msvsmon.exe” 。 然后单击 **“添加”**。  
  
5.  在**允许的应用和功能**列表中，选择**Visual Studio 远程调试器**。 检查你希望远程调试监视器与之进行通信的一个或多个网络类型（“域”、“家庭/工作”（专用）、“公用”）。 类型必须包括 Visual Studio 计算机连接到的网络。 

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-remote-computer"></a>验证在远程计算机上的 Windows 防火墙中打开端口  
 远程调试组件可在远程计算机上安装或从共享目录中运行。 在这两种情况下都必须配置远程计算机的防火墙。 远程调试组件位于：  
  
 **\<Visual Studio 安装目录 > \Common7\IDE\Remote 调试器**  
  
 有关配置 Windows 防火墙的说明在不同操作系统上略有不同。 在 Windows 8/8.1、 Windows 10 和 Windows Server 2012，word**应用**使用; 在 Windows 7 或 Windows Server 2008 中，word**程序**使用; 在以下步骤中，我们将使用 word**应用**。  
  
1.  打开 Windows 防火墙页。 （在“启动”  菜单搜索框中，键入“Windows 防火墙” 。）  
  
2.  单击“允许应用或功能通过 Windows 防火墙” 。  
  
3.  在**允许的应用和功能**列表中，查找**Visual Studio 远程调试器**。 如果已列出，请确保该选项被选中，并且同时选中一个或多个网络类型。  
  
4.  如果**Visual Studio 远程调试器**是未列出，请单击**允许另一个应用**。 如果你仍未看到它在**添加应用程序窗口**，单击**浏览**并导航到 **\<Visual Studio 安装目录 > \Common7\IDE\Remote 调试器**. 为应用程序 (x86, x64, Appx) 查找适当的文件夹，然后选择“msvsmon.exe” 。 然后单击 **“添加”**。  
  
5.  在**允许的应用**列表中，选择**Visual Studio 远程调试器**。 检查你希望远程调试监视器与之进行通信的一个或多个网络类型（“域”、“家庭/工作”（专用）、“公用”）。 类型必须包括 Visual Studio 计算机连接到的网络。 

### <a name="managed-or-native-compatibility-mode-open-additional-ports-on-the-remote-computer"></a>（托管或本机兼容性模式）打开远程计算机上的其他端口

如果你正在使用调试程序兼容性模式 (**工具 > 选项 > 调试**)，将需要打开其他端口。 兼容性模式下，调试器的旧版本和不同的端口是必需的。

> [!NOTE]
> 旧版本是调试器的 Visual Studio 2010 调试器。
  
|||||  
|-|-|-|-|  
|**端口**|**传入/传出**|**协议**|**说明**|  
|135, 139, 445|传出|TCP|必需。|  
|137, 138|传出|UDP|必需。|  
|500, 4500|传出|UDP|如果你的域策略需要通过 IPSec 进行网络通信，则需要。|  
|80|传出|TCP|Web 服务器调试所必需。|
  
## <a name="see-also"></a>另请参阅  
 [远程调试](../debugger/remote-debugging.md)