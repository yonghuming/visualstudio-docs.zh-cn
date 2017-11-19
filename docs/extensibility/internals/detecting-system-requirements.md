---
title: "检测系统要求 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: "50"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92c4d51d575ffd6e5723bf80b8adc700b83f6afd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="detecting-system-requirements"></a>检测系统要求
除非安装了 Visual Studio 将无法工作 VSPackage。 当你使用 Microsoft Windows Installer 管理你的 VSPackage 的安装时，你可以配置要检测是否安装了 Visual Studio 的安装程序。 你还可以配置它以检查系统的其他要求，例如，特定版本的 Windows 或特定 RAM 量。  
  
## <a name="detecting-visual-studio-editions"></a>检测 Visual Studio 版本  
 若要确定是否安装了 Visual Studio 的一个版本，验证安装注册表项的值 (REG_DWORD) 1 的相应文件夹中下, 表中列出。 请注意，Visual Studio 版本的层次结构：  
  
1.  企业  
  
2.  Professional  
  
3.  社区  
  
 如果安装了"较高"的版本将添加以及"较低"的版本与该版本的注册表项。 也就是说，如果安装 Enterprise edition，则安装密钥设置为 1 企业，以及专业版和社区版。 因此，你需要仅检查所需的"高"版本。  
  
> [!NOTE]
>  在注册表编辑器的 64 位版本，32 位密钥会显示在 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\。 Visual Studio 密钥正在 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\。  
  
|产品|键|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell （集成和隔离）|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>检测 Visual Studio 运行时  
 如果 Visual Studio 正在安装 VSPackage 时，不能正确注册你的 VSPackage。 安装程序必须运行 Visual Studio 时进行检测，然后拒绝安装程序。 Windows Installer 不允许你使用表项来启用此类检测。 相反，必须创建自定义操作，如下所示： 使用`EnumProcesses`函数 devenv.exe 过程中，并在启动条件或有条件地使用安装属性，是将设置显示一个对话框，提示用户关闭Visual Studio。  
  
## <a name="see-also"></a>另请参阅  
 [使用 Windows Installer 安装 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)