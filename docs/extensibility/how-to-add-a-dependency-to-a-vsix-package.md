---
title: "如何： 将依赖项添加到 VSIX 包 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f6f1e4739922a2d73999b36c0dc66e6069a6d6b
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/29/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>如何： 将依赖项添加到 VSIX 包

你可以将用于安装尚不存在于目标计算机上的任何依赖关系的 VSIX 包部署设置。 若要实现此目的，包括对 source.extension.vsixmanifest 文件中的 VSIX 依赖关系。

## <a name="to-add-a-dependency"></a>添加依赖关系

1. 打开 source.extension.vsixmanifest 文件中的**设计**视图。 转到**依赖关系**选项卡，单击**新建**。

2. 若要添加已安装的扩展： 在**添加新依赖关系**对话框中，选择**安装扩展**，然后针对**名称**，选择列表中的扩展。

3. 若要添加另一个未安装的 VSIX:: 在**添加新依赖关系**对话框中，选择**文件系统上的文件**，然后使用**浏览**按钮以选择 VSIX。

## <a name="require-a-specific-visual-studio-release"></a>需要特定的 Visual Studio 版本

如果你的扩展需要特定版本的 Visual Studio 2017，例如，它依赖于在 15.3 中发布的功能，你可以在你的 VSIX 中指定的生成号**InstallationTarget**。 例如，版本 15.3 有"15.0.26730.3"内部版本号。 你可以看到的版本生成数字映射[此处](../install/visual-studio-build-numbers-and-release-dates.md)。 请注意，使用发行版号"15.3"将无法正常运行。

如果你的扩展需要 15.3 或更高版本，你将声明**InstallationTarget 版本**作为 [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller 将检测 Visual Studio 的早期版本，并通知用户需要更高版本的更新。


## <a name="see-also"></a>另请参阅

 [VSIX 扩展架构 1.0 引用](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)[剖析 VSIX 包](../extensibility/anatomy-of-a-vsix-package.md)[准备 Windows Installer 部署扩展](../extensibility/preparing-extensions-for-windows-installer-deployment.md)