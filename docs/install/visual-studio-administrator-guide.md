---
title: "Visual Studio 管理员指南 | Microsoft Docs"
ms.custom: 
ms.date: 04/03/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
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
translationtype: Human Translation
ms.sourcegitcommit: af9699b63fdfb81a274affb78856817520c38b05
ms.openlocfilehash: fb7a87b720ad29252c602d9be5b958d8417ab93e
ms.lasthandoff: 04/03/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>适用于 Visual Studio 2017 的 Visual Studio 管理员指南

 只要每台目标计算机都满足[最低安装要求](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)，就可以在网络上部署 Visual Studio。

 无论是通过 System Center 等软件还是通过批处理文件进行部署，通常都需要完成以下步骤：

1. [将 Visual Studio 产品布局](create-an-offline-installation-of-visual-studio.md)缓存到网络位置。

2. [选择要安装的工作负载和组件](workload-and-component-ids.md)。

3. 使用选定项和其他命令行参数[生成安装脚本](use-command-line-parameters-to-install-visual-studio.md)来控制安装。

4. （可选）[应用批量许可证产品密钥](automatically-apply-product-keys-when-deploying-visual-studio.md)作为安装脚本的一部分，这样用户便无需单独激活软件。

5. 使用选定的部署技术，在目标开发者工作站上执行前述步骤中生成的脚本。

6. 定期运行第 1 步中的命令来添加更新后的组件，使用 Visual Studio 最新更新刷新网络位置。

> [!IMPORTANT]
>  请注意，从网络共享进行安装会“记住”它们的源位置。 这意味着客户端计算机的修复可能需要返回最初从中安装客户端的网络共享。 请仔细选择网络位置，使其符合在组织中运行的 Visual Studio 2017 客户端的预期生存期。

## <a name="tools"></a>工具

 我们提供了几种工具来帮助你检测和管理在客户端计算机上安装的 Visual Studio 实例：

* [VSWhere](https://github.com/microsoft/vswhere)：有助于在已安装的 Visual Studio 实例中查找核心 Visual Studio 工具位置的 C++ 可执行文件。
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell)：使用安装程序配置 API 来标识已安装的 Visual Studio 实例的 PowerShell 脚本。
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples)：展示了如何使用安装程序配置 API 来查询现有安装的 C# 和 C++ 示例。

此外，[安装程序配置 API](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) 提供了接口，方便开发者生成自己的实用工具来询问 Visual Studio 实例。

>[!TIP]
>有关 Visual Studio 2017 安装的详细信息，请参阅 [Heath Stewart 的博文](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/)。


## <a name="see-also"></a>请参阅
* [安装 Visual Studio 2017](install-visual-studio.md)
* [创建 Visual Studio 2017 的脱机安装程序](create-an-offline-installation-of-visual-studio.md)
* [使用命令行参数安装 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [报告 Visual Studio 2017 的问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

