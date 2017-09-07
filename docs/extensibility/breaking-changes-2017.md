---
title: "Visual Studio 2017 扩展性中的重大更改 |Microsoft 文档"
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
ms.translationtype: MT
ms.sourcegitcommit: 17defdd0b96ec1c3273fc6b845af844b031a4a17
ms.openlocfilehash: ac7a99673eb4dc23dd53a46c3c93fd735325c255
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Visual Studio 2017 扩展性中的更改

使用 Visual Studio 2017，我们提供[更快、 轻量的 Visual Studio 安装体验](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer)时向用户提供更好的选择对工作负荷和功能可减少用户在系统上，Visual Studio 的影响安装。 若要支持这些改进，我们已更改扩展性模型，并对 Visual Studio 扩展性做出一些重大更改。 本文档将介绍这些更改，并且可以做什么解决它们的技术详细信息。 请注意，某些信息是时间点实现的详细信息，可能在以后对其进行更改。

## <a name="changes-affecting-vsix-format-and-installation"></a>更改影响 VSIX 格式和安装

我们也将引入 VSIX v3 （版本 3） 格式，以支持轻型安装体验。

为 VSIX 格式的更改包括：

* 安装程序先决条件的声明。 以履行其承诺的一种轻型，快速安装 Visual Studio，安装程序将现在向用户提供更多配置选项。 因此，若要确保已安装的功能和扩展所需的组件，扩展将需要声明它们的依赖项。
  * Visual Studio 2017 安装程序将自动提供的用于获取和安装作为安装扩展的一部分的用户必要的组件。
  * 尝试安装的扩展，未生成使用新的 VSIX v3 格式，即使它们已在其清单中，作为面向版本 15.0 标记时，还会警告用户。
* 有关 VSIX 格式的增强的功能。 在传递[影响较小的安装](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install)还支持通过并行安装的 Visual studio，我们不再将最多的配置数据保存到系统注册表，并已移出 gac 中的 Visual Studio 特定程序集。 我们还增加 VSIX 格式和 VSIX 安装引擎的功能让你能够使用它而不是 MSI 或 EXE 安装你的某些类型的安装的扩展。

  新功能包括：

  * 到指定的 Visual Studio 实例注册。
  * 之外安装[extensions 文件夹](set-install-root.md)。
  * 检测的处理器体系结构。
  * 对语言分隔语言包的依赖项。
  * 使用安装[NGEN 支持](ngen-support.md)。

## <a name="building-an-extension-for-visual-studio-2017"></a>为 Visual Studio 2017 生成扩展

设计器工具，用于创作新的 VSIX v3 清单格式现已在 Visual Studio 2017。 请参阅随附的文档[如何： 将扩展性项目迁移到 Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)有关使用设计器工具或对项目进行手动更新的详细信息和清单以开发 VSIX v3 扩展。

## <a name="change-visual-studio-user-data-path"></a>更改： Visual Studio 用户数据路径

以前，只有一个安装的每个主要版本的 Visual Studio 无法存在每台计算机上。 若要支持的 Visual Studio 2017 通过并行安装，Visual Studio 的多个用户数据路径可能用户的计算机上存在。

应更新在 Visual Studio 进程内运行的代码，以便使用 Visual Studio 设置管理器。 在 Visual Studio 进程外部运行的代码可以查找特定的 Visual Studio 安装的用户路径[按照此处的指南](locating-visual-studio.md)。

## <a name="change-global-assembly-cache-gac"></a>更改： 全局程序集缓存 (GAC)

大多数 Visual Studio 核心程序集不会再安装到 GAC。 以便在 Visual Studio 进程中运行的代码可以仍在运行时查找所需程序集进行以下更改。

> [!NOTE]
> [INSTALLDIR] 下面指的是 Visual Studio 的安装根目录。 VSIXInstaller.exe 将自动填充，但若要编写自定义部署代码，请阅读[查找 Visual Studio](locating-visual-studio.md)。

* 仅安装到 GAC 的程序集：
  * 这些程序集现在已经安装在 [INSTALLDIR] \Common7\IDE\, [INSTALLDIR] \Common7\IDE\PublicAssemblies 或 [INSTALLDIR] \Common7\IDE\PrivateAssemblies。 这些文件夹是 Visual Studio 进程的探测路径的一部分。
* 已安装到非探测路径和 GAC 的程序集：
  * 从安装程序已删除 GAC 中的副本。
  * 添加了一个.pkgdef 文件来指定程序集的基本代码的项。

    例如: 
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    在运行时，Visual Studio pkgdef 子系统将作为合并到 Visual Studio 进程的运行时配置文件 （在下 [VSAPPDATA]\devenv.exe.config) 这些条目[ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx)元素。 这是建议的方法，以便 Visual Studio 进程查找程序集，因为它避免通过探测路径搜索。

### <a name="reacting-to-this-breaking-change"></a>对此项重大更改的作出反应

* 如果在 Visual Studio 进程内运行的你的扩展：
  * 你的代码将无法找到 Visual Studio 核心程序集。
  * 请考虑使用一个.pkgdef 文件来指定你的程序集，如有必要的路径。
* 如果你的扩展 Visual Studio 进程外部运行：
  * 请考虑查找 Visual Studio 核心程序集 [INSTALLDIR] \Common7\IDE 下\,[INSTALLDIR] \Common7\IDE\PublicAssemblies 或 [INSTALLDIR] \Common7\IDE\PrivateAssemblies 使用配置文件或程序集冲突解决程序。

## <a name="change-reduce-registry-impact"></a>更改： 降低注册表的影响

### <a name="global-com-registration"></a>全局 COM 注册

* 以前，Visual Studio 安装到 HKEY_CLASSES_ROOT 和 HKEY_LOCAL_MACHINE 配置单元，以支持本机 COM 注册多个注册表项。 为了消除这种影响，Visual Studio 现在使用[免注册激活 COM 组件](https://msdn.microsoft.com/en-us/library/ms973913.aspx)。
* 因此，大多数 TLB / OLB / 默认情况下，由 Visual Studio 不再安装在 %programfiles (x86) %\Common Files\Microsoft Shared\MSEnv 的 DLL 文件。 这些文件现在已经安装在 [INSTALLDIR] 下与 Visual Studio 主机进程使用的相应免注册 COM 清单。
* 因此，依赖于 Visual Studio COM 接口的全局 COM 注册的外部代码将无法再找到这些注册。 Visual Studio 进程内运行的代码不会看到差异。

### <a name="visual-studio-registry"></a>Visual Studio 注册表

* 以前，Visual Studio 安装到系统的 HKEY_LOCAL_MACHINE 和 HKEY_CURRENT_USER 配置单元下的 Visual Studio 特定密钥许多注册表项：
  * HKLM\Software\Microsoft\VisualStudio\\**版本**： 创建的 MSI 安装程序和每台计算机扩展的注册表项。
  * HKCU\Software\Microsoft\VisualStudio\\**版本**: Visual Studio 来存储特定于用户的设置创建注册表项。
  * HKCU\Software\Microsoft\VisualStudio\\**版本**_Config： 从.pkgdef 文件合并的扩展的 Visual Studio HKLM 密钥更高版本，加上的注册表项的副本。
* 为了减少对注册表影响，Visual Studio 现在使用[RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx)函数来存储在私有二进制文件中 [VSAPPDATA]\privateregistry.bin 下注册表项。 仅 Visual Studio 特定密钥的极小的数字将保留在系统注册表中。
* 在 Visual Studio 进程内运行的现有代码不会受到影响。 Visual Studio 将重定向到私有注册表 HKCU Visual Studio 特定项下的所有注册表操作。 读取和写入注册表中的其他位置将继续使用系统注册表。
* 外部代码需要加载并从 Visual Studio 注册表项此文件中读取。

### <a name="reacting-to-this-breaking-change"></a>对此项重大更改的作出反应

* 外部代码应将转换为的 COM 组件以及使用免注册激活。
* 外部组件可以找到 Visual Studio 位置[按照此处的指南](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)。
* 我们建议使用外部组件[外部设置管理员](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx)而不是直接向 Visual Studio 注册表项读取/写入。
* 检查是否可能已使用你的扩展的组件实现另一种注册方法。 例如，调试器这些扩展可以是能够充分利用新[msvsmon JSON 文件 COM 注册](migrate-debugger-COM-registration.md)。

## <a name="change-lightweight-solution-load"></a>更改： 轻型解决方案负载

轻量解决方案加载 (LSL) 未完全加载项目，直到在用户与其开始工作，从而减少解决方案负载时间。 这可能会影响假定项目是完全加载的扩展。 请参阅[轻型解决方案负载](lightweight-solution-load-extension-impact.md)若要了解你的扩展是否可能会受到影响，并获取更新你的扩展的指导。

