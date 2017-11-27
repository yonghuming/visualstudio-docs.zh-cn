---
title: "Visual Studio Test Agent 2017 工作负载和组件 ID | Microsoft Docs"
description: "使用 Visual Studio 工作负载和组件 ID 远程运行自动测试和负载测试"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 10/09/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-ide-install
ms.assetid: 55aea29b-1066-4e5a-aa99-fc87d4efb6d5
ms.openlocfilehash: 517a6aa9b14848aee0d84c0d3c675efda8c275d7
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="visual-studio-test-agent-2017-component-directory"></a>Visual Studio Test Agent 2017 组件目录

本页中的表中列出了可用于通过命令行安装 Visual Studio 的 ID。 请注意，我们将在发布 Visual Studio 更新时添加其他组件。

另请注意以下有关本页的注意事项：

* 每个工作负载均有其自己的部分，后跟工作负载 ID 和适用于工作负载的组件表格。
* 默认情况下，安装工作负载时将安装**必需**组件。 如果愿意，还可以安装**推荐**和**可选**组件。
* 我们还添加了一个部分，此部分列出了不属于任何工作负载的其他组件。

有关如何使用这些 ID 的详细信息，请参阅[使用命令行参数安装 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) 页。 另外，有关其他产品的工作负载和组件 ID 的列表，请参阅 [Visual Studio 2017 工作负载和组件 ID](workload-and-component-ids.md) 页。

## <a name="test-agent"></a>测试代理

**ID：**Microsoft.VisualStudio.Workload.TestAgent

**说明：**支持远程运行自动测试和负载测试

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 版本 | 依赖项类型
--- | --- | --- | ---
Microsoft.VisualStudio.ComponentGroup.TestTools.TestAgent | 测试代理核心功能 | 15.0.26606.0 | 必需

## <a name="unaffiliated-components"></a>独立组件

这些组件不随附于任何工作负载，但可选择作为单个组件。

组件 ID | 名称 | 版本
--- | --- | ---
无 | 不可用 | 无

## <a name="get-support"></a>获取支持
有时也会遇到问题。 如果 Visual Studio 安装失败，请参阅 [Visual Studio 2017 安装和升级失败疑难解答](troubleshooting-installation-issues.md)页面，查看疑难解答提示。 也可以通过 Visual Studio IDE 中的[报告问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具向我们报告产品问题，或在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上与我们分享建议。 可以在 [Visual Studio 开发者社区](https://developercommunity.visualstudio.com/)中跟踪产品问题，并在其中提问和找到答案。 此外，还可以通过 [Gitter 社区的 Visual Studio 对话](https://gitter.im/Microsoft/VisualStudio)（需要 [GitHub](https://github.com/) 帐户）与我们和其他 Visual Studio 开发者进行交流。

## <a name="see-also"></a>请参阅

* [Visual Studio 工作负荷和组件 ID](workload-and-component-ids.md)
* [Visual Studio 管理员指南](visual-studio-administrator-guide.md)
* [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [命令行参数示例](command-line-parameter-examples.md)
* [创建 Visual Studio 的脱机安装](create-an-offline-installation-of-visual-studio.md)
