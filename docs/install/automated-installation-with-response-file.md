---
title: "通过响应文件自动执行 Visual Studio 安装 | Microsoft Docs"
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
ms.assetid: 448C738E-121F-4B64-8CA8-3BC997817A14
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
ms.openlocfilehash: 2c709b5aa90ff4f5f70f0411c7f4f1870d1725d4
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="how-to-define-settings-in-a-response-file"></a>如何在响应文件中定义设置
部署 Visual Studio 的管理员可以使用 `--in` 参数指定响应文件，例如：

```
vs_enterprise.exe --in customInstall.json
```

响应文件是 [JSON](http://json-schema.org/) 文件，其内容镜像反转命令行自变量。  一般来说，如果命令行参数未使用任何自变量（例如，`--quiet`、`--passive` 等），响应文件中的值应为 true/false。  如果使用自变量（例如，`--installPath <dir>`），响应文件中的值应为字符串。  如果使用自变量并能在命令行中多次出现（例如，`--add <id>`），响应文件中的值应为一组字符串。

在命令行中指定的参数会重写响应文件中的设置，参数使用多个输入（例如，`--add`）的情况除外，因为命令行中提供的输入会与响应文件的设置合并。

# <a name="setting-a-default-configuration-for-visual-studio"></a>设置 Visual Studio 默认配置

如果使用 `--layout` 创建了网络布局缓存，则会在布局中创建初始 `response.json` 文件。

创建布局的管理员可以修改布局中的 `response.json` 文件，以控制用户通过此布局安装 Visual Studio 时看到的默认设置。  例如，如果管理员希望默认安装选定的特定工作负载和组件，可以配置 `response.json` 文件来添加这些设置。

如果 Visual Studio 安装程序是从布局文件夹运行，则会_自动_使用相应布局文件夹中的响应文件。  无需使用 `--in` 选项。

可以更新在脱机布局文件夹中创建的 `response.json` 文件，以定义用户通过此布局进行安装时看到的默认设置。 **不过，请务必保留在创建此布局时定义的现有属性。**

布局中的基本 `response.json` 文件如下所示，不同之处在于使用的是你要安装的产品和信道的值：

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

## <a name="example-layout-response-file-content"></a>布局响应文件内容示例
此示例将安装包含六个常见工作负载和组件且 UI 语言为英语和法语的 Visual Studio Enterprise。 可以将此示例用作模板，只需将工作负载和组件更改为你要安装的内容即可。

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

