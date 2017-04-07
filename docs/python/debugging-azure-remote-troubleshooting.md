---
title: "使用针对 Visual Studio 的 Python 工具对 Azure 远程调试进行故障排除 | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b723b343-dffb-457e-9af7-ee48c1451e30
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: fcf44a3967c0bd391808c9f6b3a23f39aeff05fd
ms.lasthandoff: 03/07/2017

---

# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>用于 Python 和 Azure 的远程调试故障排除程序

Visual Studio 将由于下列任意原因而无法附加到 [Azure 应用服务进行远程调试](debugging-azure-remote.md)：

| 原因 | 解决方法 |
| --- | --- |
| 未安装 Visual Studio 2013 Update 4 或更高版本。 | 从 [visualstudio.com](https://www.visualstudio.com/downloads/) 安装合适的版本。 | 
| 部署到应用服务的项目与 Visual Studio 中打开的不匹配。 | 将正确的项目加载到 Visual Studio。 |
| 项目未使用调试配置进行部署。 | 右键单击解决方案资源管理器中的项目并选择“发布”，重新部署应用程序。 在“设置”选项卡中，确保“调试”是所选的配置。 |
| 应用服务未在运行。 | 从 Visual Studio 中的服务器资源管理器或 Azure 门户启动它。 |
| 应用服务未针对 Web 套接字进行配置。 | 转到“Azure 门户”[](https://portal.azure.com)，导航到应用服务，打开“设置”>“应用程序设置”边栏选项卡，将“常规设置”>“Web 套接字”切换为“打开”，然后选择“保存”。 （请注意，此边栏选项卡上显示的“调试”选项*不*适用于 Python 调试。） |
| 已修改 `web.debug.config` 以禁用调试代理。 | 删除文件并将项目重新发布到应用服务，在此期间，针对 Visual Studio 的 Python 工具将重新创建该文件。 |

另请参阅：

- [针对 Python 的 Azure 远程调试](debugging-azure-remote.md)

