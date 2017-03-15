---
title: "对 VSIX 包签名 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 12
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: da489f0fd0483cddbefb2899eb91bd1d56735d62
ms.lasthandoff: 02/22/2017

---
# <a name="signing-vsix-packages"></a>对 VSIX 包签名
扩展插件程序集不需要它们可以运行在 Visual Studio 中，但它是作为最佳做法，这样做之前进行签名。  
  
 如果您想要保护您的扩展，并确保它尚未被篡改，您可以将数字签名添加到 VSIX 包。 VSIX 中进行签名，VSIX 安装程序将显示一条消息指出进行签名，以及有关签名本身的详细信息。 如果 VSIX 内容已被修改，并且不重新签署 VSIX，VSIX 安装程序将显示签名无效。 未停止安装，但警告用户。  
  
> [!IMPORTANT]
>  从 2015 年开始，使用 SHA256 加密以外的任何签署 VSIX 包将被标识为具有无效的签名。 VSIX 安装不会被阻止，但将警告用户。  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>签名与 VSIXSignTool VSIX  
 没有签名工具可从一个 SHA256 加密[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)在 nuget.org 上[VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)。  
  
#### <a name="to-use-the-vsixsigntool"></a>若要使用 VSIXSignTool  
  
1.  向项目中添加您的 VSIX。  
  
2.  右键单击解决方案资源管理器中的项目节点选择**添加 |管理 NuGet 包**。  有关详细信息 NuGet 和添加 NuGet 程序包，请参阅[NuGet 概述](http://docs.nuget.org/)和[使用对话框管理 NuGet 包](http://docs.nuget.org/Consume/Package-Manager-Dialog)。  
  
3.  从 VisualStudioExtensibility VSIXSignTool 搜索并安装 NuGet 程序包。  
  
4.  现在可以从项目的本地包位置运行 VSIXSignTool。 该工具的命令行帮助，请查阅以您签名的方案 (VSIXSignTool.exe /？)。  
  
 对于要用密码保护的证书文件进行签名的示例︰  
  
 VSIXSignTool.exe 登录 /f \<certfile&1;>/p\<密码&1;> \<VSIXfile&1;>  
  
## <a name="see-also"></a>另请参阅  
 [传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)
