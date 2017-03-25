---
title: "Visual Studio 2017 扩展中的重大更改 |Microsoft 文档"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
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
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 2e6e4b3d9d1528d57fe181b3765e1ce3624bebad
ms.lasthandoff: 03/07/2017

---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Visual Studio 2017 扩展中的更改

使用 Visual Studio 2017，我们提供[更快、 更精简的 Visual Studio 安装体验](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer)时向用户提供更好的选择对工作负荷和安装的功能可减少用户在系统上，Visual Studio 的影响。 若要支持这些改进，我们对扩展性模型中，进行了更改，并对 Visual Studio 扩展性做出一些重大更改。 本文档将介绍这些更改，以及可以做什么来解决它们的技术详细信息。 请注意一些信息为时间点实现的详细信息，可能会更高版本发生更改。

## <a name="changes-affecting-vsix-format-and-installation"></a>更改影响 VSIX 格式和安装

我们引入 VSIX v3 （版本 3） 格式，以支持轻量安装体验。

为 VSIX 格式的更改包括︰

* 安装程序先决条件的声明。 为了兑现承诺的一种轻型，快速安装 Visual Studio 中，安装程序将立即向用户提供更多配置选项。 因此，若要确保安装的功能和扩展所需的组件，扩展将需要声明它们的依赖项。
  * Visual Studio 2017 安装程序将自动提供要获得并安装的过程中安装您的扩展的用户所必需的组件。
  * 在尝试安装的扩展，未生成使用新的 VSIX v3 格式，即使它们已标记为面向版本 15.0 其清单中时，还会警告用户。
* VSIX 格式的增强的功能。 在传递[低影响安装](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install)还支持通过并行安装的 Visual studio，我们不再将最多的配置数据保存到系统注册表且已移出 gac 中的 Visual Studio 特定程序集。 我们也大为增加 VSIX 格式和 VSIX 安装引擎的功能允许您使用它而不是 MSI 或 EXE 安装某些类型的安装程序扩展。

  新功能包括︰

  * 到指定的 Visual Studio 实例的注册。
  * 之外安装[extensions 文件夹](set-install-root.md)。
  * 检测到的处理器体系结构。
  * 依赖于语言分隔语言包。
  * 使用安装[NGEN 支持](ngen-support.md)。

## <a name="building-an-extension-for-visual-studio-2017"></a>为 Visual Studio 2017 构建扩展

设计器工具，用于创作新的 VSIX v3 清单格式现已推出 Visual Studio 2017 中。 请参阅随附的文档[如何︰ 将可扩展性项目迁移到 Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)有关使用设计器工具或对项目进行手动更新的详细信息和清单来开发 VSIX v3 扩展。

## <a name="change-visual-studio-user-data-path"></a>更改︰ Visual Studio 用户数据路径

以前，只能安装一个 Visual Studio 各主要版本可能存在每台计算机上。 若要支持通过并行安装 Visual Studio 2017，Visual Studio 的多个用户数据路径可能存在用户的计算机上。

应该更新在 Visual Studio 进程内运行代码以使用 Visual Studio 设置管理器。 在 Visual Studio 进程外部运行的代码可以查找特定的 Visual Studio 安装的用户路径[通过遵循的指导原则](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)。

## <a name="change-global-assembly-cache-gac"></a>更改︰ 全局程序集缓存 (GAC)

大多数 Visual Studio 核心程序集将不再安装到 gac。 因此，在 Visual Studio 进程中运行的代码仍然可以在运行时找到所需程序集进行以下更改。

* 仅安装到 GAC 的程序集︰
  * 这些程序集现在已经安装在 %VsFolder%\Common7\IDE\, %VsFolder%\Common7\IDE\PublicAssemblies 或 %vsfolder%\common7\ide\privateassemblies。 这些文件夹是 Visual Studio 进程的探测路径的一部分。
* 已安装并非探测路径放入 GAC 的程序集︰
  * 从安装程序删除了在 GAC 中的副本。
  * 添加.pkgdef 文件是为了指定程序集的基本代码的项。

    例如: 
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    在运行时，Visual Studio pkgdef 子系统将作为合并到 Visual Studio 进程的运行时配置文件 （位于 %vsappdatafolder%\devenv.exe.config) 这些条目[ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx)元素。 这是推荐的方法，以便让 Visual Studio 过程查找您的程序集，因为它可以避免通过探测路径搜索。

### <a name="reacting-to-this-breaking-change"></a>响应此重大更改

* 如果在 Visual Studio 进程内运行，您的扩展︰
  * 您的代码将能够找到 Visual Studio 核心程序集。
  * 请考虑使用.pkgdef 文件来指定您的程序集，如有必要的路径。
* 如果您的扩展 Visual Studio 进程外部运行︰
  * 寻找 %VsFolder%\Common7\IDE 下的 Visual Studio 核心程序集，请考虑\,%VsFolder%\Common7\IDE\PublicAssemblies 或 %VsFolder%\Common7\IDE\PrivateAssemblies 使用配置文件或程序集冲突解决程序。

## <a name="change-reduce-registry-impact"></a>更改︰ 降低注册表产生的影响

### <a name="global-com-registration"></a>全局 COM 注册

* 以前，Visual Studio 安装到 HKEY_CLASSES_ROOT 和 HKEY_LOCAL_MACHINE 配置单元，以支持本机 COM 注册多个注册表项。 若要消除这种影响，Visual Studio 现在将使用[的 COM 组件免注册激活](https://msdn.microsoft.com/en-us/library/ms973913.aspx)。
* 因此，大多数 TLB / OLB / 默认情况下，由 Visual Studio 将不再安装在 %programfiles (x86) %\Common Files\Microsoft Shared\MSEnv 下的 DLL 文件。 %Vsfolder%下，这些文件现在与 Visual Studio 宿主进程使用的相应免注册 COM 清单一起安装。
* 结果是，依赖于 Visual Studio COM 接口的全局 COM 注册的外部代码将无法再找到这些注册。 在 Visual Studio 进程内运行代码不会看到差异。

### <a name="visual-studio-registry"></a>Visual Studio 注册表

* 以前，Visual Studio 安装到系统的 HKEY_LOCAL_MACHINE 和 HKEY_CURRENT_USER 配置单元下的 Visual Studio 特定密钥许多注册表项︰
  * HKLM\Software\Microsoft\VisualStudio\\**版本**︰ 通过 MSI 安装程序和每台计算机扩展创建的注册表项。
  * HKCU\Software\Microsoft\VisualStudio\\**版本**: Visual Studio 来存储特定于用户的设置创建注册表项。
  * HKCU\Software\Microsoft\VisualStudio\\**版本**_Config︰ 从.pkgdef 文件合并的扩展插件的一份 Visual Studio HKLM 项以上，加上的注册表项。
* 为了减少对注册表的影响，Visual Studio 现在使用[RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx)函数将注册表项存储在 %vsappdatafolder%\privateregistry.bin 下专用二进制文件中。 只有极少数的 Visual Studio 特定密钥保留在系统注册表中。
* 在 Visual Studio 进程内运行的现有代码不会受到影响。 Visual Studio 将重定向到专用注册表 HKCU Visual Studio 特定项下的所有注册表操作。 读取和写入注册表的其他位置将继续使用系统注册表。
* 外部代码将需要加载并从 Visual Studio 注册表项此文件中读取。

### <a name="reacting-to-this-breaking-change"></a>响应此重大更改

* 外部代码应将转换为对 COM 组件以及使用免注册激活。
* 外部组件可以找到 Visual Studio 位置[通过遵循的指导原则](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)。
* 我们建议使用的外部组件[外部设置管理器](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx)而不是直接向 Visual Studio 的注册表项的读/写。
* 检查是否使用您的扩展的组件可能会实现用于注册的另一种技术。 例如，可能无法利用新的调试器扩展[msvsmon JSON 文件 COM 注册](migrate-debugger-COM-registration.md)。

## <a name="change-lightweight-solution-load"></a>更改︰ 种轻量型解决方案，负载

轻量解决方案加载 (LSL) 减少通过在用户与他们开始工作之前未完全加载项目解决方案加载时间。 这可能会影响假定一个项目被完全加载的扩展。 请参阅[轻型解决方案加载](lightweight-solution-load-extension-impact.md)若要了解是否可能会影响您的扩展，并获得更新您的扩展的指导。

