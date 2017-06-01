---
title: "Visual Studio 管理员指南 | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
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
ms.translationtype: Human Translation
ms.sourcegitcommit: b5b496e0de0a12c9f52c944ef9e768c82d9be783
ms.openlocfilehash: c88a932beac964117ac2fd6ffe171bf4256ac706
ms.contentlocale: zh-cn
ms.lasthandoff: 05/08/2017

---
# <a name="visual-studio-2017-administrator-guide"></a>Visual Studio 2017 管理员指南

在企业环境中，系统管理员通常会从网络共享或使用系统管理软件向最终用户部署安装。 为了支持企业部署，我们精心设计了 Visual Studio 安装程序引擎，以便系统管理员可以创建网络安装位置、预配置安装默认值、在安装过程中部署产品密钥以及管理成功推出的产品更新。 本管理员指南通过各种情境，提供有关在常见网络环境中进行企业部署的指导。

## <a name="steps-for-deploying-visual-studio-2017-in-an-enterprise-environment"></a>如何在企业环境中部署 Visual Studio 2017

只要每台目标计算机满足[最低安装要求](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)，就可以将 Visual Studio 2017 部署到客户端工作站。 无论是通过 System Center 等软件还是通过批处理文件进行部署，通常都需要完成以下步骤：

1. 在网络位置上[创建包含 Visual Studio 产品文件的网络共享](create-a-network-installation-of-visual-studio.md)；

2. [选择要安装的工作负载和组件](workload-and-component-ids.md)；

3. [创建包含默认安装选项的响应文件](automated-installation-with-response-file.md)。 或者，使用命令行参数[生成安装脚本](use-command-line-parameters-to-install-visual-studio.md)来控制安装；

4. （可选）[应用批量许可证产品密钥](automatically-apply-product-keys-when-deploying-visual-studio.md)作为安装脚本的一部分，这样用户便无需单独激活软件；

5. 将网络布局更新为[控制何时向最终用户提供产品更新](controlling-updates-to-visual-studio-deployments.md)；

6. （可选）将注册表项设置为[控制在客户端工作站上缓存什么内容](set-defaults-for-enterprise-deployments.md)；

7. 使用所选部署技术，在目标开发者工作站上执行前述步骤中生成的脚本；

8. 定期运行第 1 步中的命令来添加更新后的组件，使用 Visual Studio [最新更新刷新网络位置](update-a-network-installation-of-visual-studio.md)。

> [!IMPORTANT]
> 请注意，从网络共享进行安装会“记住”它们的源位置。 这意味着客户端计算机的修复可能需要返回最初从中安装客户端的网络共享。 请仔细选择网络位置，使其符合在组织中运行的 Visual Studio 2017 客户端的预期生存期。

## <a name="tools"></a>工具
我们提供了几种工具来帮助你[检测和管理在客户端计算机上安装的 Visual Studio 实例](tools-for-managing-visual-studio-instances.md)。

> [!TIP]
> 除了管理员指南中的文档外，[Heath Stewart 的博客](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/)也是不错的 Visual Studio 2017 安装程序参考信息源。

## <a name="see-also"></a>请参阅
* [安装 Visual Studio 2017](install-visual-studio.md)
* [在脱机环境中安装 Visual Studio](install-visual-studio-in-offline-environment.md)
* [使用命令行参数安装 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [命令行参数示例](command-line-parameter-examples.md)
* [报告 Visual Studio 2017 的问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

