---
title: "从 Visual Studio 将 Python 应用发布到 Azure 应用服务 | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85031f91-3a65-463b-a678-1e69f1b843e6
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
ms.openlocfilehash: 0163d1279b41ef8fecf9ca774cd3e67f0f47f1b1
ms.lasthandoff: 03/07/2017

---

# <a name="publishing-to-azure-app-service"></a>发布到 Azure 应用服务

通过以下步骤，可在 Visual Studio 中快速开始构建 Python 网站并将其发布到 Azure 应用服务：

- [创建 Azure 订阅](#create-an-azure-subscription)
- [创建和测试初始项目](#create-and-test-the-initial-project)
- [发布到 Azure 应用服务](#publish-to-azure-app-service)

可在 [Visual Studio Python 教程：构建网站](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6)（youtube.com、3m10s）中找到一个此过程的简短演练。 

> [!VIDEO https://www.youtube.com/embed/FJx5mutt1uk] 

## <a name="create-an-azure-subscription"></a>创建 Azure 订阅

发布到 Azure 需要 Azure 订阅，或可以使用临时站点。

对于订阅，以[免费的完整 Azure 帐户](https://azure.microsoft.com/en-us/free/)入手，其中包括丰厚的 Azure 服务信用额度。 此外，请考虑注册 [Visual Studio Dev Essentials](https://azure.microsoft.com/en-us/pricing/member-offers/vs-dev-essentials/)，每个月为你提供&25; 美元信用额度，为期一年。

没有 Azure 订阅的情况下，在 Azure 应用服务中创建临时站点：

1. 打开浏览器浏览 [try.azurewebsites.net](https://try.azurewebsites.net)。
1. 选择“Web 应用”应用类型，然后选择“下一步”。
1. 选择“空站点”作为模板，然后选择“创建”。
1. 使用所选社交登录名登录，不久后站点将在所显示的 URL 处准备就绪。
1. 选择“下载发布配置文件”并保存 `.publishsettings` 文件，稍后会使用该文件。

## <a name="create-and-test-the-initial-project"></a>创建和测试初始项目

1. 在 Visual Studio 中，选择“文件”>“新建”>“项目”，搜索“Bottle”，选择“Bottle Web 项目”，然后单击“确定”。    

1. 系统提示安装外部包时，选择“安装到虚拟环境”。 请注意，对话框底部的“显示所需包”控件将显示要安装的包：

  ![安装所需包](~/python/media/tutorials-common-external-packages.png)

1. 为虚拟环境选择首选基解释器（例如，**Python 2.7** 或 **Python 3.4**），单击“创建”：

  ![创建项目时添加虚拟环境](~/python/media/tutorials-common-add-virtual-environment.png)

1. 创建项目后，选择“调试”>“开始调试”或按 F5 进行本地测试。 默认情况下，应用程序使用内存中存储库，这并不需要任何配置。 停止 Web 服务器时，所有数据都将丢失。

1. 在应用程序四处单击，查看其操作。

1. 完成后停止调试器（“调试”>“停止调试”或 Shift-F5）。

## <a name="publish-to-azure-app-service"></a>发布到 Azure 应用服务

1. 在“解决方案资源管理器”中，右键单击项目，选择“发布”。 

1. 在“发布”对话框中，选择“Microsoft Azure 应用服务”：

  ![发布到 Azure 步骤 1](~/python/media/tutorials-common-publish-1.png)

1. 选择目标：

    - 如果具有 Azure 订阅，请选择“Microsoft Azure 应用服务”作为发布目标，然后在以下对话框中，选择一个现有应用服务或选择“新建”新建一个。
    - 如果从 try.azurewebsites.net 使用临时站点，请选择“导入”作为发布目标，然后浏览从该站点下载的 `.publishsettings` 文件，再选择“确定”。

1. 应用服务详细信息显示在下面的“发布”对话框的“连接”选项卡中。

  ![发布到 Azure 步骤 2](~/python/media/tutorials-common-publish-2.png)

1. 根据需要选择“下一步 >”，查看其他设置。 如果计划[在 Azure 上远程调试 Python 代码](debugging-azure-remote.md)，必须将“配置”设置为“调试”
1. 选择“发布”。 应用程序部署到 Azure 后，将在该站点上打开默认浏览器。 
