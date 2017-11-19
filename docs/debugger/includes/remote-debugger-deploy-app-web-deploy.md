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
ms.openlocfilehash: 27cff46f5a68ef28f247aa159a2b8be5db56b0fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
如果你安装 Web 部署使用 Web 平台安装程序，你可以部署该应用程序直接从 Visual Studio。

1. 使用管理员权限启动 Visual Studio 并重新打开该项目。

    部署使用 Web 部署对应用程序需要管理员权限。

2. 在“解决方案资源管理器” 中，右键单击项目节点并选择“发布” 。

3. 有关**选择发布目标**，选择**IIS，FTP，等**单击**发布**。

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

4. IIS 设置中输入更正配置参数。

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    如果主机名不能解决当你尝试验证下一步中的步骤**服务器**文本框中，请尝试 IP 地址。 包括`http://`作为前缀的**服务器**字段。  请确保使用在端口 80**服务器**文本框中，并确保端口 80 是在防火墙中打开。

6. 单击**下一步**，选择**调试**配置，然后选择**删除目标位置的其他文件**下**文件发布**选项。

    > [!NOTE]
    > 如果你选择发布配置，则禁用调试在 web.config 文件中，在发布时。

5. 单击**Prev**，然后选择**验证**。 如果连接安装验证，你可以尝试发布。

6. 单击**发布**发布该应用程序。

    输出选项卡将显示是否发布已成功，以及你的浏览器然后打开应用程序。

    如果你收到一提的是 Web 部署错误，重新检查 Web 部署安装步骤，请确保正确的端口已打开 （Web 部署还需要端口 8172 要在服务器上打开）。

    如果应用程序已成功部署，但不能正常运行，可能有 IIS 配置，您的 ASP.NET 安装，或者你的 Web 站点配置的问题。 在 Windows Server 中，打开从 IIS 的网站的更具体的错误消息，然后重新检查之前的步骤。