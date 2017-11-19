---
title: "什么 &#39; s Visual Studio 2017 SDK 中的新增功能 |Microsoft 文档"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0be477d54ffeab52c415890c7d95447fa3f55ffc
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>什么 &#39; s Visual Studio 2017 SDK 中的新增功能

Visual Studio SDK 的 Visual Studio 2017 具有以下新的和更新功能。

## <a name="vsix-v3-format"></a>VSIX v3 格式

若要支持新的轻量安装的 Visual Studio 2017，VSIX 扩展清单格式已更新为版本 3 (VSIX v3)。

新格式具有对支持：

* 显式声明要检测到，由 VSIXInstaller 安装系统必备组件。
* Ngen'ing 上扩展安装的程序集。
* 安装在常用扩展根的外部的资产。

若要了解有关这些更改，请参阅以下主题：

* [对自 2017 年的扩展性的更改](breaking-changes-2017.md)
* [VSIX v3 中的 Ngen 支持](ngen-support.md)
* [在扩展文件夹外进行安装](set-install-root.md)
* [Visual Studio 2017 扩展性的常见问题](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>迁移到 Visual Studio 2017 扩展性项目

若要了解如何更新到 Visual Studio 2017 的扩展性项目和其 VSIX 清单，请参阅[如何： 将扩展性项目迁移到 Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。

## <a name="custom-project-and-item-templates"></a>自定义项目和项模板

从 Visual Studio 2017 年 1 开始，扫描自定义项目和项模板将无法再执行。 相反，扩展必须提供模板清单文件描述这些模板的安装位置。 你可以使用 Visual Studio 2017 更新 VSIX 扩展。 如果在部署你使用 MSI 的扩展，你必须手动生成模板清单文件。 有关详细信息，请参阅[升级自定义项目和项模板为 Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 模板清单架构记录在[Visual Studio 模板清单架构参考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

## <a name="updated-extension-performance-guidelines"></a>更新的扩展性能准则

新增了一个[如何： 诊断扩展性能](how-to-diagnose-extension-performance.md)下的主题[管理 Vspackage](managing-vspackages.md)来演示如何检测和分析对 Visual Studio 扩展影响启动和解决方案加载时间。
