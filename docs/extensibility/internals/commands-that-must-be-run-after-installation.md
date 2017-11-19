---
title: "必须在安装后运行的命令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4fef2c76364c1ca1398aef3b94226e7a9a365cf1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="commands-that-must-be-run-after-installation"></a>必须在安装后运行的命令
如果通过.msi 文件部署你的扩展，则必须运行`devenv /setup`中对 Visual Studio 来发现你的扩展的顺序对安装的一部分。  
  
> [!NOTE]
>  本主题中的信息适用于查找 DevEnv 随 Visual Studio 2008 及更早版本。 有关如何发现 DevEnv 与更高版本的 Visual Studio 的信息，请参阅[检测系统要求](../../extensibility/internals/detecting-system-requirements.md)。  
  
## <a name="finding-devenvexe"></a>查找 devenv.exe  
 你可以找到每个版本从注册表的 devenv.exe 值[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]编写安装程序，使用 RegLocator 表和 AppSearch 表将注册表值作为属性存储。 有关详细信息，请参阅[检测系统要求](../../extensibility/internals/detecting-system-requirements.md)。  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>要查找来自不同版本的 Visual Studio 的 devenv.exe 的 RegLocator 表行  
  
|Signature_|根|键|名称|类型|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch 的相应 RegLocator 表行的表行  
  
|属性|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 例如，Visual Studio 安装程序将写的注册表值**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath**作为**C:\VS2008\Common7\IDE\devenv.exe**，安装程序必须运行的可执行文件的完整路径。  
  
 **请注意**RegLocator 类型列是 2，因为不需要签名表中指定的其他版本信息。  
  
## <a name="running-devenvexe"></a>运行 devenv.exe  
 在安装程序中运行的标准操作 AppSearch 后, AppSearch 表中的每个属性具有相应版本的 Visual Studio 的 devenv.exe 文件所指向的值。 如果任何指定的注册表值都不存在-由于未安装该版本的 Visual Studio-指定的属性设置为 null。  
  
 通过自定义操作运行可执行文件属性所指向的 Windows Installer 支持类型 50。 自定义操作应包括在脚本执行选项、 msidbCustomActionTypeInScript (1024) 和 msidbCustomActionTypeCommit (512)，以确保已成功将其集成到之前安装 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 有关详细信息，请参阅 CustomAction 表和自定义操作脚本中执行的选项。  
  
 类型 50 的自定义操作指定的源列和目标列中的命令行自变量的值作为包含可执行文件的属性。  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>要运行 devenv.exe 的 CustomAction 表行  
  
|操作|类型|源|目标|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|  
  
 到要在安装过程的执行计划它们的 InstallExecuteSequence 表，必须编写自定义操作。 使用条件列中每一行中的相应属性以防止从正在运行，如果该自定义操作的版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在系统上未安装。  
  
> [!NOTE]
>  `Null`属性计算结果为`False`时在条件中使用。  
  
 为每个自定义操作的序列列的值取决于你的 Windows Installer 包中的其他序列值。 序列值应是这样，运行方式的 devenv.exe 自定义操作尽可能接近立即在了 InstallFinalize 标准操作之前。  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallExecuteSequence 表以计划 devenv.exe 自定义操作  
  
|操作|条件|序列|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>另请参阅  
 [使用 Windows Installer 安装 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)