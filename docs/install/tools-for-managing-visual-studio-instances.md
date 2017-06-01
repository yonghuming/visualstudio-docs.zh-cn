---
title: "用于检测和管理 Visual Studio 实例的工具 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
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
ms.openlocfilehash: a6c3aa65a2c0198c856f09f6f16f58bf16945d58
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>用于检测和管理 Visual Studio 实例的工具

## <a name="detecting-existing-visual-studio-instances"></a>检测现有 Visual Studio 实例
我们提供了几种工具来帮助你检测和管理在客户端计算机上安装的 Visual Studio 实例：

* [VSWhere](https://github.com/microsoft/vswhere)：有助于在已安装的 Visual Studio 实例中查找核心 Visual Studio 工具位置的 C++ 可执行文件。
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell)：使用安装程序配置 API 来标识已安装的 Visual Studio 实例的 PowerShell 脚本。
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples)：展示了如何使用安装程序配置 API 来查询现有安装的 C# 和 C++ 示例。

此外，[安装程序配置 API](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) 提供了接口，方便开发者生成自己的实用工具来询问 Visual Studio 实例。

>[!TIP]
>有关 Visual Studio 2017 安装的详细信息，请参阅 [Heath Stewart 的博文](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/)。


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>编辑 Visual Studio 实例的注册表
在 Visual Studio 2017 中，注册表设置存储在专用位置中，以便于可以在同一计算机上安装相同版本 Visual Studio 的多个并行实例。

由于这些条目并非存储在全局注册表中，因此需要遵循有关使用注册表编辑器更改注册表设置的特殊说明：

1. 如果有打开的 Visual Studio 2017 实例，请予以关闭。
2. 启动 `regedit.exe`。
3. 选择“`HKEY_LOCAL_MACHINE`”节点。
4. 在 Regedit 主菜单中，依次选择“文件 -> 加载配置单元...”，然后选择专用注册表文件（存储在“AppData\Local”文件夹中）。 例如：
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

> [!NOTE]
> `<config>` 对应于要浏览的 Visual Studio 实例。

系统会提示你输入配置单元名称，这将成为你的独立配置单元的名称。 执行此操作后，应该能够在所创建的独立配置单元下浏览注册表。

> [!IMPORTANT]
> 必须先卸载已创建的独立配置单元，然后才能再次启动 Visual Studio。 为此，请依次选择 Regedit 主菜单中的“文件 -> 卸载配置单元”。 （如果不这样做，文件会一直处于锁定状态，且 Visual Studio 无法启动。）

