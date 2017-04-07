---
title: "注册互操作程序集命令处理程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 19
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 774266bbcd64e87229f8f97626cdff1462b27fcb
ms.lasthandoff: 04/05/2017

---
# <a name="registering-interop-assembly-command-handlers"></a>注册互操作程序集命令处理程序
VSPackage 必须注册[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，以便集成的开发环境 (IDE) 将正确路由其命令。  
  
 通过手动编辑或通过注册机构 (.rgs) 文件，可以更新注册表。 有关详细信息，请参阅[创建注册器脚本](/cpp/atl/creating-registrar-scripts)。  
  
 托管包框架 (MPF) 提供此功能通过<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>类。</xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>  
  
 [命令表格式引用](http://msdn.microsoft.com/en-us/09e9c6ef-9863-48de-9483-d45b7b7c798f)资源位于非托管附属 UI dll。  
  
## <a name="command-handler-registration-of-a-vspackage"></a>命令处理程序注册的 VSPackage  
 VSPackage 充当的处理程序用户界面 (UI) 的基于的命令需要一个名为后 VSPackage 的注册表项`GUID`。 此注册表项指定的 VSPackage 的 UI 资源文件以及该文件中的菜单资源的位置。 本身的注册表项位于 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<版本 1>*\Menus，其中*\<版本 1>*是版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，例如 9.0。  
  
> [!NOTE]
>  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio 的根路径\\*\<版本 1>*可以替换备用根时[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]初始化 shell。 根路径有关的详细信息，请参阅[与 Windows Installer 安装 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。  
  
### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU 资源注册表条目  
 注册表项的结构是︰  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*GUID*1> 是`GUID`{XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX} 形式的 vspackage。  
  
 *\<资源信息 1>*用逗号分隔的三个元素组成。 这些元素处于顺序的不同而不同︰  
  
 \<*资源 DLL 路径*1>， \<*菜单资源 ID*1>， \<*菜单版本*>  
  
 下表描述的字段\<*资源信息*1>。  
  
|元素|说明|  
|-------------|-----------------|  
|\<*资源 DLL 路径*>|这是资源包含菜单资源 DLL 的完整路径或此保留为空，指示 VSPackage 的资源 DLL 要使用 （如指定在其中注册 VSPackage 本身的包子项）。<br /><br /> 它是通常将此字段保留为空。|  
|\<*菜单资源 ID*>|这是资源 ID `CTMENU` vspackage 包含所有的 UI 元素，如从编译的资源[.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)文件。|  
|\<*菜单版本*>|这是用来为进行版本`CTMENU`资源。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用此值来确定它是否需要 remerge 的内容`CTMENU`具有其缓存的所有资源`CTMENU`资源。 Remerge 触发的执行 devenv 安装程序命令。<br /><br /> 此值应最初设置为 1，在每次更改后递增`CTMENU`资源和 remerge 发生之前。|  
  
### <a name="example"></a>示例  
 下面是几个资源条目示例︰  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>另请参阅  
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [使用互操作程序集的命令和菜单](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
