---
title: "禁用或移动包缓存 | Microsoft Docs"
description: "禁用、启用或移动部署 Visual Studio 时使用的包缓存。"
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: heaths
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
ms.openlocfilehash: e07f1c04d9695e092db7aa29e641ce9bd36250f9
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="disable-or-move-the-package-cache"></a>禁用或移动包缓存

如果需要在未连接 Internet 的情况下修复 Visual Studio 或其他相关产品，可以使用包缓存提供的已安装的包源。 不过，在安装一些驱动器或系统后，可能不希望保留所有这些包。
由于安装程序会在需要时下载它们，因此如果希望节省或恢复磁盘空间，可以禁用或移动包缓存。

## <a name="disable-the-package-cache"></a>禁用包缓存

使用新安装程序安装、修改或修复 Visual Studio 或其他产品之前，可以使用 `--nocache` 开关来启动安装程序。

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

对任意产品执行任何操作都会删除相应产品的任何现有包，并避免在安装后保存任何包。 如果修改或修复 Visual Studio 且必须使用包，那么它们会自动进行下载，并在安装后进行删除。

若要重新启用缓存，请改为传递 `--cache`。 由于只会缓存必需的包，因此，如果需要还原所有包，应在断开网络连接之前修复 Visual Studio。

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

还可以在安装、修改或修复 Visual Studio 之前设置 `KeepDownloadedPayloads` [注册表策略](set-defaults-for-enterprise-deployments.md)来禁用缓存。

## <a name="move-the-package-cache"></a>移动包缓存

常见的系统配置是将 Windows 安装在硬盘较大（或更大）且可满足开发需求（如源代码、程序二进制文件等）的 SSD 上。 如果要脱机工作，可以改为移动包缓存。

目前，只有在安装、修改或修复 Visual Studio 之前设置了 `CachePath` [注册表策略](set-defaults-for-enterprise-deployments.md)后，才能执行此操作。

## <a name="see-also"></a>请参阅

 * [安装 Visual Studio](install-visual-studio.md)
 * [为企业部署设置默认值](set-defaults-for-enterprise-deployments.md)
 * [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [报告 Visual Studio 的问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

