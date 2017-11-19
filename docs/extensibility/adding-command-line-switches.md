---
title: "添加命令行开关 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e292a08e6d8ac9c6f59f84514fbb625779f82c4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-command-line-switches"></a>添加命令行开关
你可以添加时执行 devenv.exe 应用于你的 VSPackage 的命令行开关。 使用<xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute>声明对开关以及其属性名称。 在此示例中，添加名为的 VSPackage 的一个子类 MySwitch 交换机**AddCommandSwitchPackage**不带任何参数且自动加载 VSPackage。  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 以下表所示命名的参数  
  
 参数  
 为交换机参数的数目。 可以是"*"，或自变量列表。  
  
 DemandLoad  
 如果这设置为 1，否则设置为 0，则自动加载 VSPackage。  
  
 HelpString  
 帮助字符串或资源 ID 的字符串与一起显示**devenv /？**。  
  
 名称  
 开关。  
  
 PackageGuid  
 包的 GUID。  
  
 自变量的第一个值通常是 0 或 1。 特殊值 * 可用于指示命令行的整个其余部分是自变量。 这可用于调试的方案，用户必须通过中的调试器命令字符串。  
  
 DemandLoad 值可以是`true`(1) 或`false`(0) 指示应自动加载 VSPackage。  
  
 HelpString 值是资源 ID 的字符串的出现在 devenv /？显示帮助内容。 此值应采用格式"#nnn"其中 nnn 是一个整数。 资源文件中的字符串值应以将新行字符结尾。  
  
 名称值是该交换机的名称。  
  
 PackageGuid 值是实现此交换机的包的 GUID。 IDE 使用此 GUID 在命令行开关适用于的注册表中找到 VSPackage。  
  
## <a name="retrieving-command-line-switches"></a>检索命令行开关  
 你的包加载时，可以通过完成以下步骤来检索命令行开关。  
  
1.  在你的 VSPackage 的<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>实现，请调用`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine>获取<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>接口。  
  
2.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A>检索用户输入的命令行开关。  
  
 下面的代码演示如何找出是否由用户输入 MySwitch 命令行开关：  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 它由你负责每次加载你的包时检查命令行开关。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv 命令行开关](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef 实用程序](../extensibility/internals/createpkgdef-utility.md)   
 [.Pkgdef 文件](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)