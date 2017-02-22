---
title: "添加命令行开关 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "添加的命令行开关"
  - "检索的命令行开关"
  - "IVsAppCommandLine::GetOption 方法"
  - "命令行开关"
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# 添加命令行开关
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以添加适用于你的 VSPackage，devenv.exe 执行时的命令行开关。 使用 <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> 来声明该开关并将其属性的名称。 在此示例中，MySwitch 交换机添加为一个名为 VSPackage 的子类 **AddCommandSwitchPackage** 不带任何参数且自动加载 VSPackage。  
  
```c#  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 下表所示命名的参数  
  
 参数  
 为该交换机的参数的数目。 可以是"\*"，或参数的列表。  
  
 DemandLoad  
 如果此值设置为 1，否则设置为 0，则会自动加载 VSPackage。  
  
 HelpString  
 帮助字符串或资源 ID 的字符串以显示与 **devenv \/?**。  
  
 名称  
 开关。  
  
 PackageGuid  
 包的 GUID。  
  
 第一个参数的值通常是 0 或 1。 特殊值 \* 可用于指示命令行的整个剩余部分是参数。 这可用于调试的方案，用户必须通过在调试器命令字符串。  
  
 DemandLoad 值是 `true` \(1\) 或 `false` \(0\) 指示应自动加载 VSPackage。  
  
 HelpString 值是 devenv 中显示的字符串的资源 ID \/?帮助显示。 此值应在窗体"\#nnn"其中 nnn 是一个整数。 资源文件中的字符串值应以换行符结尾。  
  
 名称值是该交换机的名称。  
  
 PackageGuid 值是包的实现此开关的 GUID。 IDE 将使用此 GUID 在命令行开关适用的注册表中查找 VSPackage。  
  
## 检索命令行开关  
 加载包时，您可以通过完成以下步骤来检索命令行开关。  
  
1.  在你的 VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 实现，请调用 `QueryService` 上 <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> 获取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> 接口。  
  
2.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> 来检索用户输入的命令行开关。  
  
 下面的代码演示如何查明是否由用户输入 MySwitch 命令行开关是:  
  
```c#  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine)); int isPresent = 0; string optionValue = ""; cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 它负责您每次加载包时检查命令行开关。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv 命令行开关](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef 实用程序](../extensibility/internals/createpkgdef-utility.md)   
 [.Pkgdef 文件](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)