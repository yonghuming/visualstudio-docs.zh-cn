---
title: "什么是 Visual Studio 2017 SDK 中的新增功能 |Microsoft 文档"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 3da360fc4df5516f5d976f807319c07b49d8c4e8
ms.contentlocale: zh-cn
ms.lasthandoff: 03/07/2017

---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>什么是 Visual Studio 2017 SDK 中的新增功能

Visual Studio SDK 的 Visual Studio 2017 具有以下新的和更新功能。

## <a name="vsix-v3-format"></a>VSIX v3 格式

若要支持新的轻量安装的 Visual Studio 2017，VSIX 扩展清单格式已更新为版本 3 (VSIX v3)。

新格式具有对支持︰

* 显式声明要检测到并由 VSIXInstaller 安装系统必备组件。
* 扩展安装中 Ngen'ing 的程序集。
* 安装常用的扩展根目录之外的资产。

若要了解有关这些更改，请参阅以下主题︰

* [对 2017年的可扩展性的更改](breaking-changes-2017.md)
* [VSIX v3 中的 Ngen 支持](ngen-support.md)
* [在扩展文件夹外进行安装](set-install-root.md)
* [Visual Studio 2017 可扩展性的常见问题](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>迁移到 Visual Studio 2017 扩展性项目

若要了解如何更新 Visual Studio 2017 扩展性项目以及各自的 VSIX 清单，请参阅[如何︰ 将可扩展性项目迁移到 Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。

## <a name="lightweight-solution-load-lsl"></a>轻量解决方案加载 (LSL)

轻量解决方案加载是 VS 2017 这将大大降低解决方案加载时，使您能够更快更高效工作中的新增功能。 启用 LSL 后，Visual Studio 不会完全加载项目直到您开始使用它们。

LSL 可能会影响 Visual Studio 扩展。 扩展其功能取决于要完全加载的项目可能不工作或未正确工作。 请参阅[轻型解决方案加载](lightweight-solution-load-extension-impact.md)若要了解是否可能会影响您的扩展，并获得更新您的扩展的指导。

## <a name="custom-project-and-item-templates"></a>自定义项目和项模板

从 Visual Studio 2017 开始，扫描自定义项目和项模板将不会再执行。 相反，该扩展插件必须提供模板的清单文件，用于描述这些模板的安装位置。 Visual Studio 2017 可用于更新您的 VSIX 扩展。 如果您部署使用 MSI 扩展插件，必须手动生成模板清单文件。 有关详细信息，请参阅[升级自定义项目和项模板的 Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 中介绍了模板清单架构[Visual Studio 模板清单架构参考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

## <a name="updated-extension-performance-guidelines"></a>更新的扩展性能准则

新增了一个[如何︰ 诊断扩展性能](how-to-diagnose-extension-performance.md)下的主题[管理 Vspackage](managing-vspackages.md)以演示如何检测和分析对 Visual Studio 扩展影响启动和解决方案加载时间。

