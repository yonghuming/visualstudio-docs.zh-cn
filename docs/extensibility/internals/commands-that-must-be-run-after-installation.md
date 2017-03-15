---
title: "必须在安装后运行的命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安装后命令"
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# 必须在安装后运行的命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

如果通过.msi 文件部署您的扩展，则必须运行 `devenv /setup` 作为您的安装顺序对 Visual Studio 来发现您的扩展的一部分。  
  
> [!NOTE]
>  本主题中的信息适用于查找 DevEnv 使用 Visual Studio 2008 和更早版本。 有关如何发现 DevEnv Visual Studio 的较新版本的信息，请参阅 [检测系统要求](../../extensibility/internals/detecting-system-requirements.md)。  
  
## 查找 devenv.exe  
 您可以找到每个版本从注册表的 devenv.exe 值 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 编写安装程序，使用 RegLocator 表和 AppSearch 表作为属性存储的注册表值。 有关更多信息，请参见[检测系统要求](../../extensibility/internals/detecting-system-requirements.md)。  
  
### 要找到来自不同版本的 Visual Studio 的 devenv.exe 的 RegLocator 表行  
  
|Signature\_|根|键|名称|类型|  
|-----------------|-------|-------|--------|--------|  
|RL\_DevenvExe\_2002|2|SOFTWARE\\Microsoft\\VisualStudio\\7.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2003|2|SOFTWARE\\Microsoft\\VisualStudio\\7.1\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2005|2|SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2008|2|SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS|EnvironmentPath|2|  
  
### AppSearch 表行的相应 RegLocator 表行  
  
|属性|Signature\_|  
|--------|-----------------|  
|DEVENV\_EXE\_2002|RL\_DevenvExe\_2002|  
|DEVENV\_EXE\_2003|RL\_DevenvExe\_2003|  
|DEVENV\_EXE\_2005|RL\_DevenvExe\_2005|  
|DEVENV\_EXE\_2008|RL\_DevenvExe\_2008|  
  
 例如，Visual Studio 安装程序将写的注册表值 **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS\\EnvironmentPath** 作为 **C:\\VS2008\\Common7\\IDE\\devenv.exe**, ，必须运行安装程序的可执行文件的完整路径。  
  
 **注意** RegLocator 类型列是 2，因为不需要指定签名表中的附加版本信息。  
  
## 运行 devenv.exe  
 之后在安装程序中运行的标准操作 AppSearch，AppSearch 表中的每个属性具有相应版本的 Visual Studio 的 devenv.exe 文件所指向的值。 如果任何指定的注册表值不存在 — 因为未安装该版本的 Visual Studio\-指定的属性设置为 null。  
  
 Windows 安装程序支持通过自定义操作运行属性所指向的可执行文件键入 50。 自定义操作应包括在脚本执行选项、 msidbCustomActionTypeInScript \(1024\) 和 msidbCustomActionTypeCommit \(512\)，以确保已成功将其集成到之前安装 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 有关详细信息，请参阅 CustomAction 表和自定义操作脚本中执行选项。  
  
 类型 50 的自定义操作指定作为源列和目标列中的命令行参数的值包含可执行文件的属性。  
  
### 要运行 devenv.exe 的 CustomAction 表行  
  
|操作|类型|源|目标|  
|--------|--------|-------|--------|  
|CA\_RunDevenv2002|1586|DEVENV\_EXE\_2002|\/setup|  
|CA\_RunDevenv2003|1586|DEVENV\_EXE\_2003|\/setup|  
|CA\_RunDevenv2005|1586|DEVENV\_EXE\_2005|\/setup|  
|CA\_RunDevenv2008|1586|DEVENV\_EXE\_2008|\/setup|  
  
 插入 InstallExecuteSequence 表来计划的安装过程的执行，必须编写自定义操作。 条件列的每一行中的对应属性用于防止自定义操作正在运行，如果该版本的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 系统上未安装。  
  
> [!NOTE]
>  `Null` 属性的计算结果为 `False` 时在条件中使用。  
  
 为每个自定义操作的序列列的值取决于您的 Windows 安装程序包中的其他序列值。 序列值应该是这样，devenv.exe 自定义操作以运行得尽可能靠近之前的情况下了 InstallFinalize 标准操作。  
  
### InstallExecuteSequence 表才能计划 devenv.exe 自定义操作  
  
|操作|条件|序列|  
|--------|--------|--------|  
|CA\_RunDevenv2002|DEVENV\_EXE\_2002|6602|  
|CA\_RunDevenv2003|DEVENV\_EXE\_2003|6603|  
|CA\_RunDevenv2005|DEVENV\_EXE\_2005|6605|  
|CA\_RunDevenv2008|DEVENV\_EXE\_2008|6608|  
  
## 请参阅  
 [使用 Windows Installer 安装 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)