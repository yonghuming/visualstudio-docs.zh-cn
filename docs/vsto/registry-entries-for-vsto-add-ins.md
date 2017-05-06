---
title: "VSTO 外接程序的注册表项"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "LoadBehavior 项"
  - "外接程序 [Visual Studio 中的 Office 开发]，注册表项"
  - "注册表项 [Visual Studio 中的 Office 开发]"
  - "应用程序级外接程序 [Visual Studio 中的 Office 开发]，注册表项"
  - "注册表项 [Visual Studio 中的 Office 开发]"
ms.assetid: 319e5bbc-0234-4af0-91ce-54bcfafc173f
caps.latest.revision: 79
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 78
---
# VSTO 外接程序的注册表项
  部署使用 Visual Studio 创建的 VSTO 外接程序时，必须创建一组特定的注册表项。 这些注册表项可提供一些信息，使 Microsoft Office 应用程序能够发现和加载 VSTO 外接程序。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 生成项目时，Visual Studio 在开发计算机上创建这些注册表项，以便可以轻松运行和调试 VSTO 外接程序。 如果使用 ClickOnce 部署 VSTO 外接程序，则将自动在最终用户计算机上创建注册表项。 如果使用 Windows Installer 部署 VSTO 外接程序，则必须配置 InstallShield Limited Edition 项目才能在最终用户计算机上创建注册表项。  
  
 有关如何在 VSTO 外接程序加载过程中使用注册表项的详细信息，请参阅 [VSTO 外接程序的体系结构](../vsto/architecture-of-vsto-add-ins.md)。  
  
> [!NOTE]  
>  在本主题中，文本*外接程序 ID* 表示 VSTO 外接程序的唯一 ID。 默认情况下，该 ID 是 VSTO 外接程序程序集的名称。  
  
## 针对如下用户注册 VSTO 外接程序：当前用户与所有用户  
 安装 VSTO 外接程序后，可以按两种方式注册：  
  
-   仅针对当前用户注册（即，它仅供安装 VSTO 外接程序时登录到计算机的用户使用）。 在这种情况下，在 HKEY\_CURRENT\_USER 下创建注册表项。  
  
-   针对所有用户注册（即，登录到计算机的所有用户均可使用该 VSTO 外接程序）。 在这种情况下，在 HKEY\_LOCAL\_MACHINE 下创建注册表项。  
  
 使用 Visual Studio 创建的所有 VSTO 外接程序均可针对当前用户注册。 但是，仅在特定场景下才可针对所有用户注册 VSTO 外接程序。 这些场景取决于计算机上 Microsoft Office 的版本和 VSTO 外接程序的部署方式。  
  
### Microsoft Office 版本  
 Office 应用程序可以加载在 HKEY\_LOCAL\_MACHINE 或 HKEY\_CURRENT\_USER 下注册的 VSTO 外接程序。  
  
 若要加载在 HKEY\_LOCAL\_MACHINE 下注册的 VSTO 外接程序，则计算机上必须已安装有更新程序包 976477。 有关详细信息，请参阅 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=184923](http://go.microsoft.com/fwlink/?LinkId=184923)。  
  
### 部署类型  
 如果使用 ClickOnce 部署 VSTO 外接程序，则仅可针对当前用户注册 VSTO 外接程序。 这是因为 ClickOnce 仅支持在 HKEY\_CURRENT\_USER 下创建密钥。 如果想要向计算机上的所有用户注册 VSTO 外接程序，则必须使用 Windows Installer 部署 VSTO 外接程序。 有关这些部署类型的详细信息，请参阅[使用 ClickOnce 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)和[使用 Windows Installer 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-windows-installer.md)。  
  
## 注册表项  
 对于除 Visio 外的所有应用程序，所需的 VSTO 外接程序注册表项都位于以下注册表项下，其中的 *Root* 是 HKEY\_CURRENT\_USER 或 HKEY\_LOCAL\_MACHINE。  
  
 **除 Visio 外的所有应用程序**  
  
|Office 版本|配置路径|  
|---------------|----------|  
|32 位|*根*\\Software\\Microsoft\\Office\\*应用程序名称*\\Addins\\*外接程序 ID*|  
|64 位|*根*\\Software\\Wow6432Node\\Microsoft\\Office\\*应用程序名称*\\Addins\\*外接程序 ID*|  
  
 **Visio**  
  
|Office 版本|配置路径|  
|---------------|----------|  
|32 位|*根*\\Software\\Microsoft\\Visio\\Addins\\*外接程序 ID*|  
|64 位|*根*\\Software\\Wow6432Node\\Visio\\Addins\\*外接程序 ID*|  
  
 下表列出了此注册表项下的条目。  
  
|条目|类型|值|  
|--------|--------|-------|  
|**Description**|REG\_SZ|必需。 VSTO 外接程序的简短说明。<br /><br /> 当用户在 Microsoft Office 应用程序的**“选项”**对话框的**“外接程序”**窗格中选择 VSTO 外接程序时，将会显示此说明。|  
|**FriendlyName**|REG\_SZ|必需。 Microsoft Office 应用程序中的**“COM 外接程序”**对话框中显示的 VSTO 外接程序的描述性名称。 默认值为 VSTO 外接程序 ID。|  
|**LoadBehavior**|REG\_DWORD|必需。 一个值，用于指定应用程序在何时尝试加载 VSTO 外接程序以及 VSTO 外接程序的当前状态（已加载或卸载）。<br /><br /> 默认情况下，此项设置为 3，指定在启动时加载 VSTO 外接程序。 有关详细信息，请参阅 [LoadBehavior 值](#LoadBehavior)。 **Note:**  如果用户禁用 VSTO 外接程序，则该操作会修改 HKEY\_CURRENT\_USER 注册表配置单元中的 **LoadBehavior** 值。 对于每个用户，HKEY\_CURRENT\_USER 配置单元中的 **LoadBehavior** 值将替代 HKEY\_LOCAL\_MACHINE 配置单元中定义的 **LoadBehavior** 默认值。|  
|**Manifest**|REG\_SZ|必需。 VSTO 外接程序部署清单的完整路径。 该路径可以是本地计算机上的某个位置，也可以是网络共享 \(UNC\) 或 Web 服务器 \(HTTP\)。<br /><br /> 如果使用 Windows Installer 部署解决方案，则必须向**清单**路径添加前缀 **file:\/\/\/**。 还必须将字符串 **&#124;vstolocal**（即竖线字符 **&#124;** 后接 **vstolocal**）追加到此路径的末尾。 这可确保从安装文件夹，而非 ClickOnce 缓存加载你的解决方案。 有关详细信息，请参阅[使用 Windows Installer 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-windows-installer.md)。 **Note:**  在开发计算机上生成 VSTO 外接程序时，Visual Studio 会自动将字符串 **&#124;vstolocal** 追加到此注册表项。|  
  
###  <a name="OutlookEntries"></a> Outlook 窗体区域注册表项  
 如果在 Outlook 的 VSTO 外接程序中创建自定义窗体区域，则会使用其他注册表项在 Outlook 中注册该窗体区域。 这些项是在针对窗体区域支持的每个邮件类别的不同注册表项下创建的。 这些注册表项位于以下位置，其中的*根*为 HKEY\_CURRENT\_USER 或 HKEY\_LOCAL\_MACHINE。  
  
 *根*\\Software\\Microsoft\\Office\\Outlook\\FormRegions\\*邮件类别*  
  
 与所有 VSTO 外接程序共享的其他注册表项类似，生成项目时，Visual Studio 会在开发计算机上创建窗体区域注册表项。 如果使用 ClickOnce 部署 VSTO 外接程序，则将自动在最终用户计算机上创建注册表项。 如果使用 Windows Installer 部署 VSTO 外接程序，则必须配置 InstallShield Limited Edition 项目才能在最终用户计算机上创建注册表项。  
  
 有关窗体区域注册表项的详细信息，请参阅[在 Windows 注册表中指定窗体区域](HV10038637)。 有关 Outlook 窗体区域的详细信息，请参阅[创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)。  
  
##  <a name="LoadBehavior"></a> LoadBehavior 值  
 *Root*\\Software\\Microsoft\\Office\\*application name*\\Addins\\*add\-in ID* 项下的 **LoadBehavior** 条目包含指定 VSTO 外接程序运行时行为的值的按位组合。 最低顺序位（值 0 和 1）指示 VSTO 外接程序当前是已卸载还是已加载。 其他位指示应用程序何时尝试加载 VSTO 外接程序。  
  
 通常，在最终用户计算机上安装 VSTO 外接程序时，**LoadBehavior** 条目将设置为 0、3 或 16（采用十进制）。 默认情况下，在生成或发布 VSTO 外接程序时，Visual Studio 会将外接程序的 **LoadBehavior** 条目设置为 3。  
  
 下表列出了 **LoadBehavior** 条目的所有可能的值。 此表中的一些描述涉及手动或以编程方式加载 VSTO 外接程序。 若要手动加载 VSTO 外接程序，在应用程序的**“COM 外接程序”**对话框中选择 VSTO 外接程序旁的复选框。 若要以编程方式加载 VSTO 外接程序，请将表示 VSTO 外接程序的 <xref:Microsoft.Office.Core.COMAddIn> 对象的 <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> 属性设置为 **true**。  
  
|值（采用十进制）|VSTO 外接程序状态|VSTO 外接程序加载行为|说明|  
|--------------|-----------------|-------------------|--------|  
|0|已卸载|不自动加载|应用程序从不尝试自动加载 VSTO 外接程序。 用户可尝试手动加载 VSTO 外接程序，也可以编程方式加载 VSTO 外接程序。<br /><br /> 如果 VSTO 外接程序加载成功，则 **LoadBehavior** 值保持为 0，但将更新**“COM 外接程序”**对话框中的 VSTO 外接程序状态，以指示已加载 VSTO 外接程序。|  
|1|已加载|不自动加载|应用程序从不尝试自动加载 VSTO 外接程序。 用户可尝试手动加载 VSTO 外接程序，也可以编程方式加载 VSTO 外接程序。<br /><br /> 虽然**“COM 外接程序”**对话框指示已在应用程序启动后加载 VSTO 外接程序，但只有在手动或以编程方式加载 VSTO 外接程序后，它才会真正加载。<br /><br /> 如果应用程序成功加载 VSTO 外接程序，则 **LoadBehavior** 值更改为 0，并在应用程序关闭后仍然保持为 0。|  
|2|已卸载|在启动时加载|应用程序不会尝试自动加载 VSTO 外接程序。 用户可尝试手动加载 VSTO 外接程序，也可以编程方式加载 VSTO 外接程序。<br /><br /> 如果应用程序成功加载 VSTO 外接程序，则 **LoadBehavior** 值更改为 3，并在应用程序关闭后仍然保持为 3。|  
|3|已加载|在启动时加载|应用程序在启动时尝试加载 VSTO 外接程序。 在 Visual Studio 中生成或发布 VSTO 外接程序时，这是默认值。<br /><br /> 如果应用程序成功加载 VSTO 外接程序，则 **LoadBehavior** 值保持为 3。 如果加载 VSTO 外接程序时出错，则 **LoadBehavior** 值更改为 2，并在应用程序关闭后仍然保持为 2。|  
|8|已卸载|按需加载|应用程序不会尝试自动加载 VSTO 外接程序。 用户可尝试手动加载 VSTO 外接程序，也可以编程方式加载 VSTO 外接程序。<br /><br /> 如果应用程序成功加载 VSTO 外接程序，则 **LoadBehavior** 值更改为 9。|  
|9|已加载|按需加载|VSTO 外接程序将仅在应用程序需要它时加载，例如，用户单击使用 VSTO 外接程序中的功能的 UI 元素（例如，功能区中的自定义按钮）时。<br /><br /> 如果应用程序成功加载 VSTO 外接程序，则 **LoadBehavior** 值保持为 9，但将更新**“COM 外接程序”**对话框中的外接程序状态，以指示当前已加载 VSTO 外接程序。 如果加载 VSTO 外接程序时出错，则 **LoadBehavior** 值更改为 8。|  
|16|已加载|第一次时加载，然后按需加载|如果想要按需加载 VSTO 外接程序，请设置此值。 用户第一次运行应用程序时，应用程序将加载 VSTO 外接程序。 用户下一次运行应用程序时，应用程序将加载 VSTO 外接程序定义的任何 UI 元素，但不会加载 VSTO 外接程序，直到用户单击与 VSTO 外接程序关联的 UI 元素。<br /><br /> 应用程序第一次成功加载 VSTO 外接程序时，**LoadBehavior** 值在加载 VSTO 外接程序后保持为 16。 应用程序关闭后，**LoadBehavior** 值更改为 9。|  
  
## 请参阅  
 [Visual Studio 中 Office 解决方案的体系结构](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [VSTO 外接程序的体系结构](../vsto/architecture-of-vsto-add-ins.md)   
 [生成 Office 解决方案](../vsto/building-office-solutions.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)  
  
  