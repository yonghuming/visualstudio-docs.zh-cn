---
title: "Visual Studio 团队资源管理器 2017 工作负载和组件 ID | Microsoft Docs"
description: "使用 Visual Studio 工作负载和组件 ID 为技术全面的测试人员提供集成的测试工具"
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
ms.assetid: c6ef9a3b-d13d-49b4-9faa-51fa06b21e1f
ms.openlocfilehash: d4590db9e33d955f7e0c1b77845cf3819bc0d68e
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="visual-studio-team-explorer-2017-component-directory"></a>Visual Studio 团队资源管理器 2017 组件目录

本页中的表中列出了可用于通过命令行安装 Visual Studio 的 ID。 请注意，我们将在发布 Visual Studio 更新时添加其他组件。

另请注意以下有关本页的注意事项：

* 每个工作负载均有其自己的部分，后跟工作负载 ID 和适用于工作负载的组件表格。
* 默认情况下，安装工作负载时将安装**必需**组件。 如果愿意，还可以安装**推荐**和**可选**组件。
* 我们还添加了一个部分，此部分列出了不属于任何工作负载的其他组件。

有关如何使用这些 ID 的详细信息，请参阅[使用命令行参数安装 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) 页。 另外，有关其他产品的工作负载和组件 ID 的列表，请参阅 [Visual Studio 2017 工作负载和组件 ID](workload-and-component-ids.md) 页。

## <a name="visual-studio-core-editor-included-with-visual-studio-team-explorer-2017"></a>Visual Studio 核心编辑器（随附于 Visual Studio 团队资源管理器 2017）

**ID：**Microsoft.VisualStudio.Workload.CoreEditor

**说明：**Visual Studio 核心 shell 体验，包括语法感知代码编辑、源代码管理和工作项管理。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 版本 | 依赖项类型
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio 核心编辑器 | 15.0.26606.0 | 必需

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
