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
ms.openlocfilehash: a55b2a12c9a45c5a3952e3e6f4e1627bec8ba520
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
1. 在**解决方案资源管理器**，右键单击项目节点并选择**发布**(对于 Web 窗体，**发布 Web 应用**)。

2. 在**发布**对话框中，选择**文件夹**，单击**浏览**，并创建一个新文件夹中， **C:\Publish**。

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    对于 Web 窗体应用中，选择**自定义**在发布对话框中，输入配置文件名称，然后选择**确定**。

3. 单击“发布” 。

    Visual Studio 将项目发布到的文件夹。 进度将显示在输出窗口中。

4. 在**发布**对话框中，单击**设置**链接，，然后选择**设置**选项卡。

5. 将配置设置为**调试**，选择**删除所有现有的文件发布前**，然后单击**保存**。

    > [!NOTE]
    > 如果你使用的发布版本，则禁用调试在 web.config 文件中，在发布时。

6. 单击“发布” 。

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    应用程序发布**调试**到本地文件夹的项目配置。

5. 从 Visual Studio 计算机的 ASP.NET 项目目录复制到对 ASP.NET 应用程序配置的本地目录 (在此示例中， **C:\Publish**) Windows Server 计算机上。 在本教程中，我们假设你要手动复制，但你可以使用 PowerShell、 Xcopy 或 Robocopy 等其他工具。

    > [!CAUTION]
    >  如果你需要更改代码或重新生成，你必须重新发布并重复此步骤。 复制到远程计算机的可执行文件必须与你的本地源和符号完全匹配。

6. 在 Windows 服务器上，验证可以正确运行该应用，通过在浏览器中打开应用程序。

    如果应用程序无法正常运行，安装在你的服务器和您的 Visual Studio 计算机上的 ASP.NET 版本之间可能有不匹配，或你可能遇到的问题与您的 IIS 或网站配置。 重新检查之前的步骤。