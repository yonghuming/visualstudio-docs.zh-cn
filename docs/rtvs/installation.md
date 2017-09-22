---
title: "安装针对 Visual Studio 的 R 工具 | Microsoft Docs"
ms.custom: 
ms.date: 6/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.devlang: r
ms.topic: article
ms.assetid: 3ff60292-1b88-4ee9-b2b2-edd957f1a519
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 8e35c82a5f8583a609e9fccbacb0b27d9c3eac8f
ms.contentlocale: zh-cn
ms.lasthandoff: 07/12/2017

---

# <a name="how-to-install-r-tools-for-visual-studio"></a>如何安装针对 Visual Studio 的 R 工具

在本主题中：

- [支持的 Visual Studio 版本](#supported-versions-of-visual-studio)
- [在 Visual Studio 2017 中安装 RTVS](#installing-rtvs-in-visual-studio-2017)
- [在 Visual Studio 2015 中安装 RTVS](#installing-rtvs-in-visual-studio-2015)
- [脱机安装](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> 安装 R 工具后，可能想要配置 Visual Studio，获得经过优化的数据科学家布局，如[选项](options.md#data-scientist-layout)主题所述。

## <a name="supported-versions-of-visual-studio"></a>支持的 Visual Studio 版本

[Visual Studio 2017](https://www.visualstudio.com/downloads/) 和 [Visual Studio 2015 Update 3（或更高版本）](http://go.microsoft.com/fwlink/?LinkId=691129)的社区版（免费）、专业版和企业版上均支持针对 Visual Studio 的 R 工具 (RTVS)。 

如果只有 Visual Studio Test Professional 和 SQL Server Management Studio 等产品随附的 Visual Studio Shell，则不会安装 RTVS。 Visual Studio Shell 缺少 RTVS 的必需组件。


## <a name="installing-rtvs-in-visual-studio-2017"></a>在 Visual Studio 2017 中安装 RTVS

1. 运行 Visual Studio 安装程序。 （如果尚未安装 Visual Studio，请参阅[下载](https://www.visualstudio.com/downloads/)。）在 Windows 7 上，请确保安装程序已更新，显示 Visual Studio 版本 15.2（内部版本 26430.12）或更高版本。

2. 选择“数据科学和分析应用程序”工作负载：

    ![VS 2017 中的数据科学和分析应用程序工作负载](media/installation-data-science-workload.png)

3. 在同一工作负载名称下的右侧设置任何其他选项。 此工作负载默认包含 F# 和 Python 支持。 对于 R，最低要求是“R 语言支持”、“R 开发运行时支持”以及“Microsoft R Client”。

RTVS 的安装位置为：`%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`，其中 `<version>` 通常是 `2017`，而 `<edition>` 通常是 `Community`、`Professional` 或 `Enterprise`。

## <a name="installing-rtvs-in-visual-studio-2015"></a>在 Visual Studio 2015 中安装 RTVS

安装 Visual Studio 2015 后，需要单独安装 R 解释器和 R 工具。

### <a name="install-an-r-interpreter"></a>安装 R 解释器

RTVS 需要从以下一个或多个来源安装 64 位的 R 3.2.1 或更高版本：

* [Microsoft R Open](https://mran.microsoft.com/download/)
* [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started)
* [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open 和 CRAN R 均允许多个并行版本。 但是，Microsoft R Client 只支持一个版本，并始终使用安装的最新版本。

### <a name="install-the-r-tools"></a>安装 R 工具

从 [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current) 下载当前 RTVS。 如果尚未安装，RTVS 会检查是否有适合的 Visual Studio 版本，并帮助安装 R 解释器。

RTVS 的安装位置为：`%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Visual Studio 和 RTVS 的脱机安装

脱机安装适用于未连接到 Internet 的计算机：

1. 按照说明创建当前版本 Visual Studio 的脱机安装程序： 

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. 从 [https://aka.ms/rtvs-current-zip](https://aka.ms/rtvs-current-zip) 和 [https://aka.ms/rtvs-remote-zip](https://aka.ms/rtvs-remote-zip) 下载脱机 RTVS 安装程序。 

1. 从脱机安装程序安装 Visual Studio 和 RTVS。

## <a name="see-also"></a>另请参阅

- [R 入门](getting-started-with-r.md)
- [R 工具示例项目](getting-started-samples.md)
- [获取帮助](getting-started-help.md)
- [选项设置](options.md)

