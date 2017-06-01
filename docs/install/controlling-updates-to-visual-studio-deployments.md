---
title: "控制对 Visual Studio 部署的更新 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
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
ms.openlocfilehash: 2e68d084c88c398d1576f53a79a156c111651895
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>控制对基于网络的 Visual Studio 部署的更新

企业管理员通常会创建布局，并将其托管在网络文件共享上，以供部署给最终用户。

## <a name="controlling-where-visual-studio-looks-for-updates"></a>控制 Visual Studio 在何处查找更新
默认情况下，即使安装是从网络共享进行部署，Visual Studio 也仍会继续联机查找更新。 如果有更新，用户将能够进行安装；在脱机布局中找不到的任何更新内容都将从 Web 下载。

如果要直接控制 Visual Studio 在何处查找更新，以及用户要更新到的版本，可以按照以下步骤操作，修改 Visual Studio 在何处查找更新：

 1. 创建脱机布局：
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. 将脱机布局复制到托管文件共享上：
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. 修改布局中的 response.json 文件，将 `channelUri` 值更改为指向管理员控制的 channelManifest.json 的副本。 <b>注意：</b>请务必在此值中转义反斜杠，如下所示：
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 4. 现在，最终用户可以从此共享运行安装程序来安装 Visual Studio。
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```
 5. 如果确定用户是时候更新到更高版本的 Visual Studio，企业管理员可以使用下面的命令，[将布局位置更新](update-a-network-installation-of-visual-studio.md)为纳入更新后的文件：
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 6. 确保在更新后的布局中 response.json 文件仍包含自定义设置，特别是 channelUri 修改：
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 7. 通过此布局安装的现有 Visual Studio 将在 `\\server\share\VS2017\ChannelManifest.json` 中查找更新。 如果此 channelManifest.json 比用户已安装的版本更高，Visual Studio 会通知用户有更新可供安装。
 8. 安装 Visual Studio 的新用户将直接通过此布局自动安装更新后的 Visual Studio 版本。

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>在 Visual Studio IDE 中控制通知
如上所述，Visual Studio 检查其安装位置（例如，网络共享或 Internet），以确定是否有任何更新。 若有更新，Visual Studio 默认会在窗口右上角显示通知标志 ![更新通知标志](media/notification-flag.png) 来通知用户

如果不希望最终用户收到更新通知（例如，通过中央软件分发机制提供更新），可以禁用这些通知。

由于 Visual Studio 2017 [将注册表项存储在专用注册表中](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)，因此无法照常直接编辑注册表。 不过，Visual Studio 提供可用于更改 Visual Studio 设置的命令 `vsregedit.exe`。 可以使用下面的命令禁用通知：

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2 dword 0
```

替换上述命令中的目录，与要编辑的已安装实例匹配。 

> [!TIP]
> 使用 [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) 可以在客户端工作站上查找 Visual Studio 的特定实例。 

## <a name="see-also"></a>请参阅
* [安装 Visual Studio](install-visual-studio.md)
* [Visual Studio 管理员指南](visual-studio-administrator-guide.md)
* [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [用于管理 Visual Studio 实例的工具](tools-for-managing-visual-studio-instances.md)

