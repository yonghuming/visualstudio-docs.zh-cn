---
title: "更新基于网络的 Visual Studio 安装 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 05/05/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 75c65d75ab751058ac435d62f253ead149ccfe42
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="update-a-network-based-installation-of-visual-studio"></a>更新基于网络的 Visual Studio 安装

可以使用最新的产品更新来更新 Visual Studio 的网络安装布局，以便它可用作 Visual Studio 最新更新的安装点，同时还可用于维护已部署到客户端工作站的安装。

## <a name="how-to-update-a-network-layout"></a>如何更新网络布局
若要将网络安装共享刷新为包含最新更新，请运行初始创建布局时运行的同一 `--layout` 命令，以增量下载更新后的包。

如果在首次创建网络布局时选择的是部分布局，请务必使用首次创建网络安装布局时使用的相同命令行参数（即相同的工作负载和语言）。 如果选择其他选项，那么第二个 `--layout` 命令不会更新第二次未指定的包。

如果在文件共享上托管布局，建议更新布局的私有副本（例如，`c:\vs2017offline`），并在下载所有更新后的内容后将其复制到文件共享（例如，`\\server\products\VS2017`）。  如果不这样做，那么任何在布局更新时运行安装程序的用户更有可能无法通过布局获取所有内容，因为布局并未完全更新。

## <a name="how-to-deploy-an-update-to-client-machines"></a>如何将更新部署到客户端计算机
更新可以由企业管理员进行部署，也可以由客户端计算机启动，具体视网络环境的配置方式而定。 

- 用户可以更新通过脱机安装文件夹安装的 Visual Studio 实例：
  - 运行 Visual Studio 安装程序。
  - 然后，单击“更新”。

- 管理员可以单独使用下面两个命令，更新 Visual Studio 的客户端部署，而无需与任何用户进行交互：
  - 首先，更新 Visual Studio 安装程序： <br>```vs_enterprise.exe --quiet --update```
  - 然后，更新 Visual Studio 应用程序本身： <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> 使用 [vswhere.exe 命令](tools-for-managing-visual-studio-instances.md)可标识客户端计算机上 Visual Studio 现有实例的安装路径。

> [!TIP]
> 若要详细了解如何控制何时向用户显示更新通知，请参阅[控制对基于网络的 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)。


## <a name="see-also"></a>请参阅
* [安装 Visual Studio](install-visual-studio.md)
* [Visual Studio 管理员指南](visual-studio-administrator-guide.md)
* [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [用于检测和管理 Visual Studio 实例的工具](tools-for-managing-visual-studio-instances.md)
* [控制对基于网络的 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)

