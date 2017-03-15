---
title: "注册互操作程序集的命令处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "互操作程序集，命令处理程序"
  - "使用互操作程序集注册处理命令"
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# 注册互操作程序集的命令处理程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

必须使用注册 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，以便集成的开发环境 \(IDE\) 将其命令的路由正确。  
  
 通过手动编辑或使用注册机构 \(.rgs\) 文件，可以更新注册表。 有关详细信息，请参阅[Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)。  
  
 管理包框架 \(MPF\) 提供此功能通过 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 类。  
  
 [Command Table Format Reference](http://msdn.microsoft.com/zh-cn/09e9c6ef-9863-48de-9483-d45b7b7c798f) 资源位于非托管附属 UI dll 中。  
  
## 作为 VSPackage 的命令处理程序注册  
 作为用户界面 \(UI\) 的处理程序的 VSPackage 的基于的命令需要一个名为 VSPackage 后的注册表项 `GUID`。 此注册表项指定的 VSPackage 的用户界面资源文件和该文件内的菜单资源的位置。 注册表项本身位于 HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\*\< 版本 \>*\\Menus，其中 *\< 版本 \>* 是版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ，例如 9.0。  
  
> [!NOTE]
>  HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\ 的根路径*\< 版本 \>* 可以将其覆盖备用根时 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 初始化外壳程序。 根路径的详细信息，请参阅 [使用 Windows Installer 安装 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。  
  
### CTMENU 资源注册表条目  
 注册表项的结构为:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\ Menus\ <GUID> = <Resource Information>  
```  
  
 \<*GUID*\> 是 `GUID` 的 VSPackage 中窗体 {XXXXXX\-XXXX\-XXXX\-XXXX\-XXXXXXXXX}。  
  
 *\< 资源信息 \>* 用逗号分隔的三个元素组成。 这些元素的顺序:  
  
 \<*资源 DLL 路径*\>，\<*菜单资源 ID*\>，\<*菜单版本*\>  
  
 下表描述的字段 \<*资源信息*\>。  
  
|元素|描述|  
|--------|--------|  
|\<*资源 DLL 路径*\>|这是资源包含菜单资源的 DLL 的完整路径或为空，指示 VSPackage 的资源 DLL 要使用 \(如包子项: 注册 VSPackage 本身中指定\)。<br /><br /> 这也十分常见，若要将此字段留空。|  
|\<*菜单资源 ID*\>|这是资源 ID `CTMENU` 资源，其中包含用于 VSPackage 所有 UI 元素，如从编译 [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) 文件。|  
|\<*菜单版本*\>|这是为进行版本使用一个数字 `CTMENU` 资源。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用此值来确定它是否需要重新合并的内容 `CTMENU` 具有其缓存的所有资源 `CTMENU` 资源。 由执行 devenv 安装程序命令触发重新合并。<br /><br /> 此值最初应设为 1，在每次更改后递增 `CTMENU` 资源并重新合并发生之前。|  
  
### 示例  
 下面是几个资源条目示例:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\ Menus\ {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10 {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## 请参阅  
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令和使用互操作程序集的菜单](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)