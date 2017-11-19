---
translation.priority.ht:
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
ms.openlocfilehash: 103cefa8573c8f44efff0b53b0c09a5ec26706e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
这些步骤演示了基本配置的 IIS。 有关详细信息或要安装到 Windows 桌面计算机，请参阅[发布到 IIS](https://docs.microsoft.com/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)或[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

对于 Windows Server 操作系统，使用**添加角色和功能**向导通过**管理**链接或**仪表板**中链接**服务器管理器**. 在“服务器角色”步骤中，选中“Web 服务器(IIS)”框。

![在选择服务器角色步骤中选择了“Web 服务器 IIS”角色。](../media/remotedbg-server-roles-ws2012.png)

在“角色服务”步骤中，选择所需 IIS 角色服务，或接受提供的默认角色服务。

继续完成安装的 web 服务器角色和服务的确认步骤。 安装 Web 服务器 (IIS) 角色后无需重启服务器/IIS。