---
title: "在脱机环境中安装 Visual Studio 时的特别注意事项 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 05/09/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: timsneath
ms.author: tims
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: b596b6b6f9cff58525d253157534b6b990c68fcd
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>在脱机环境中安装 Visual Studio 时的特别注意事项

Visual Studio 主要可供在已连接 Internet 的计算机上安装，因为许多组件需要定期更新。 不过，通过额外执行一些步骤，可以在未连接 Internet 的环境中部署 Visual Studio。

## <a name="create-a-network-installation-layout"></a>创建网络安装布局
* 有关详细信息，请参阅[创建基于网络的 Visual Studio 安装](create-a-network-installation-of-visual-studio.md)

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>安装 Visual Studio 脱机安装所需的证书
Visual Studio 安装程序引擎仅安装受信任的内容。  它会检查正在下载内容的验证码签名，并在安装前验证签名是否受信任。  可连接 Internet 的计算机会自动下载并安装验证文件签名所需的任何证书。  不过，如果是在脱机环境或 Internet 连接质量不佳的系统中进行安装，则可能会失败。  对于此类环境中的用户，必须确保必要证书已预安装。  如果创建的是脱机安装，执行计算机会将这些证书下载到“证书”文件夹中。

可以手动双击证书文件，然后单击后到达证书管理器向导，从而在客户端上安装证书。 如果看到输入密码提示，请将密码留空。

若要编写证书安装脚本，请按照以下步骤操作：

1. 将 certmgr.exe 复制到安装共享（例如，`\server\share\vs2017`）中。 `certmgr.exe` 包含在 Windows SDK 中，可作为_通用Windows平台开发_工作负载中的可选组件进行安装。 （例如：`"C:\Program Files (x86)\Windows Kits\10\bin\x86\certmgr.exe"`）

2. 使用下面的命令创建批处理文件：

```cmd
\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
```

3. 通过管理员命令行界面或提升的进程在客户端上运行批处理文件。

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>为什么无法自动安装 `certificates` 文件夹中的证书？
如果是在联机环境中验证签名，Windows API 可用于下载证书并将其添加到系统中。 在此过程中，可通过管理设置验证证书是否受信任且已获允许。 在大多数脱机环境中，无法执行此验证过程。 手动安装证书可允许用户确保证书不仅受信任，而且还满足管理员要求。

## <a name="install-visual-studio"></a>安装 Visual Studio
安装证书后，可以按[此处的说明](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation)操作，脱机部署 Visual Studio，无需执行其他特殊步骤。


## <a name="see-also"></a>请参阅
* [安装 Visual Studio](install-visual-studio.md)
* [Visual Studio 管理员指南](visual-studio-administrator-guide.md)
* [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 工作负荷和组件 ID](workload-and-component-ids.md)

