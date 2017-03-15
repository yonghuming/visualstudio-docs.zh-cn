---
title: "检测系统要求 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安装程序，VSPackage"
  - "启动条件"
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 50
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 50
---
# 检测系统要求
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

除非安装了 Visual Studio 将 VSPackage 无法工作。 当使用 Microsoft Windows 安装程序来管理你的 VSPackage 的安装时，您可以配置要检测是否安装了 Visual Studio 的安装程序。 此外可以配置它来检查系统的其他要求，例如，特定版本的 Windows 或特定 RAM 量。  
  
## 检测 Visual Studio 版本  
 若要确定是否安装了 Visual Studio 的版本，验证安装注册表项的值是 \(REG\_DWORD\) 1 中相应的文件夹，如下表中列出。 请注意，Visual Studio 版本的层次结构︰  
  
1.  企业  
  
2.  Professional  
  
3.  社区  
  
 当安装"高"版本时，将添加与"lower"的版本以及该版本的注册表项。 也就是说，如果安装的 Enterprise edition，则安装密钥设置为 1 企业版和专业版和社区版。 因此，您需要仅检查所需的"高"版本。  
  
> [!NOTE]
>  在注册表编辑器的 64 位版本，32 位注册表 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\ 下显示。 Visual Studio 密钥是在 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\ 下。  
  
|产品|键|  
|--------|-------|  
|Visual Studio Enterprise 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\enterprise|  
|Visual Studio Professional 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\professional|  
|Visual Studio Community 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\community|  
|Visual Studio 2015 Shell （集成和隔离）|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell|  
  
## 在 Visual Studio 运行时检测  
 如果 Visual Studio 正在安装 VSPackage 时，你的 VSPackage 无法正确注册。 安装程序必须运行 Visual Studio 时进行检测，然后拒绝安装程序。 Windows 安装程序不允许您使用表项来启用此类检测。 相反，必须创建自定义操作，如下所示︰ 使用 `EnumProcesses` 函数来检测 devenv.exe 进程，然后或者设置或有条件地启动条件中使用的安装程序属性显示一个对话框，提示用户关闭 Visual Studio。  
  
## 请参阅  
 [使用 Windows Installer 安装 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)