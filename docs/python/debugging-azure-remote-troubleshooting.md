---
title: "Visual Studio 中适用于 Python 的 Azure 远程调试故障排除 | Microsoft Docs"
ms.custom: 
ms.date: 7/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b723b343-dffb-457e-9af7-ee48c1451e30
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: de9d74c3a0a8a3f3b66d621884f9c17fe787f856
ms.contentlocale: zh-cn
ms.lasthandoff: 07/18/2017

---

# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>用于 Python 和 Azure 的远程调试故障排除程序

由于下列任意原因，Visual Studio 将而无法附加到 [Azure App Service 进行远程调试](debugging-azure-remote.md)：

| 原因 | 解决方法 |
| --- | --- |
| 未安装 Visual Studio 2013 Update 4 或更高版本。 | 从 [visualstudio.com](https://www.visualstudio.com/downloads/) 安装合适的版本。 | 
| 部署到应用服务的项目与 Visual Studio 中打开的不匹配。 | 将正确的项目加载到 Visual Studio。 |
| 项目未使用调试配置进行部署。 | 右键单击解决方案资源管理器中的项目并选择“发布”，重新部署应用程序。 在“设置”选项卡中，确保“调试”是所选的配置。 |
| 应用服务未在运行。 | 从 Visual Studio 中的服务器资源管理器或 Azure 门户启动它。 |
| 应用服务未针对 Web 套接字进行配置。 | 转到 [“Azure 门户”](https://portal.azure.com)，导航到应用服务，打开“设置”>“应用程序设置”边栏选项卡，将“常规设置”>“Web 套接字”切换为“打开”，然后选择“保存”。 （请注意，此边栏选项卡上显示的“调试”选项*不*适用于 Python 调试。） |
| 已修改 `web.debug.config` 以禁用调试代理。 | 删除文件并将项目重新发布到应用服务，在此期间，Visual Studio 将重新创建该文件。 |

另请参阅：

- [针对 Python 的 Azure 远程调试](debugging-azure-remote.md)

