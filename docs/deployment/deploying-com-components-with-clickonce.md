---
title: "部署 COM 组件与 ClickOnce |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: d3a8ae32afec789595ecd126eeaee0c5ea05a9e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="deploying-com-components-with-clickonce"></a>使用 ClickOnce 部署 COM 组件
旧的 COM 组件部署传统上已被一个困难的任务。 组件需要进行全局注册，并因此可能导致重叠的应用程序之间的意外副作用。 这种情况下通常不是.NET Framework 应用程序中的问题因为完全独立于应用程序或组件的并行兼容。 Visual Studio 允许你将部署在 Windows XP 或更高版本的操作系统上隔离的 COM 组件。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]提供了简便安全的机制，用于部署你的.NET 应用程序。 但是，如果你的应用程序使用旧的 COM 组件，你将需要执行有关部署它们的其他步骤。 本主题介绍如何部署隔离的 COM 组件和引用本机组件 （例如，从 Visual Basic 6.0 或 Visual c + +）。  
  
 有关部署独立的 COM 组件的详细信息，请参阅"简化应用程序部署[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]和免注册 COM"在[http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx)。  
  
## <a name="registration-free-com"></a>免注册 COM  
 免注册 COM 是一项新技术用于部署和激活隔离的 COM 组件。 它的工作方式是将所有组件的类型库和到系统注册表到 XML 文件调用一个清单，通常会对其进行安装的注册信息存储在应用程序所在的文件夹。  
  
 隔离的 COM 组件要求它注册开发人员在计算机上，但它无需在最终用户的计算机上注册。 若要隔离的 COM 组件，你需要做设置它的引用**Isolated**属性**True**。 默认情况下，此属性设置为**False**，，该值指示应视为与已注册的 COM 引用。 如果此属性为**True**，它使得在生成时为此组件生成的清单。 它还会导致在安装过程中要复制到应用程序文件夹的相应文件。  
  
 当清单生成器遇到独立的 COM 引用时，它的所有枚举`CoClass`组件的类型库，其对应的注册数据，每一项匹配并生成中的条目清单的所有 COM 定义类型库文件中的类。  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>使用 ClickOnce 部署免注册 COM 组件  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署技术非常适合于部署隔离的 COM 组件，因为同时[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]和免注册 COM 需要组件以便部署具有一个清单。  
  
 通常情况下，组件的作者应提供一个清单。 如果没有，但是，Visual Studio 就是能够生成清单自动以 COM 组件。 清单生成执行期间[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]发布过程; 有关详细信息，请参阅[发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)。 此功能还允许你利用旧在早期开发环境，如 Visual Basic 6.0 中编写的组件。  
  
 有两种方法，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署 COM 组件：  
  
-   引导程序用于部署你的 COM 组件;这适用于所有支持的平台。  
  
-   使用本机组件隔离 (也称为免注册 COM) 部署。 但是，这仅适用于 Windows XP 或更高版本的操作系统。  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>隔离和部署简单的 COM 组件的示例  
 为了演示免注册 COM 组件部署，此示例将在引用使用 Visual Basic 6.0 中，创建一个独立的本机 COM 组件的 Visual Basic 中创建基于 Windows 的应用程序并将其使用部署[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]。  
  
 首先，你将需要创建本机 COM 组件：  
  
##### <a name="to-create-a-native-com-component"></a>若要创建的本机 COM 组件  
  
1.  从使用 Visual Basic 6.0**文件**菜单上，单击**新建**，然后**项目**。  
  
2.  在**新项目**对话框中，选择**Visual Basic**节点，然后选择**ActiveX DLL**项目。 在“名称”框中键入 `VB6Hello`。  
  
    > [!NOTE]
    >  使用免注册 COM; 支持仅 ActiveX DLL 和 ActiveX 控件的项目类型不支持 ActiveX EXE 和 ActiveX 文档项目类型。  
  
3.  在**解决方案资源管理器**，双击**Class1.vb**打开文本编辑器。  
  
4.  在 Class1.vb，为生成的代码之后添加以下代码`New`方法：  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  生成所需组件。 从**生成**菜单上，单击**生成解决方案**。  
  
> [!NOTE]
>  免注册 COM 支持仅 Dll，COM 控制项目类型。 不能使用 Exe 使用免注册 com。  
  
 现在可以创建基于 Windows 的应用程序，并向其添加对 COM 组件的引用。  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>创建基于 Windows 的应用程序使用 COM 组件  
  
1.  使用 Visual Basic 中，从**文件**菜单上，单击**新建**，然后**项目**。  
  
2.  在**新项目**对话框中，选择**Visual Basic**节点，然后选择**Windows 应用程序**。 在“名称”框中键入 `RegFreeComDemo`。  
  
3.  在**解决方案资源管理器**，单击**显示所有文件**按钮以显示项目引用。  
  
4.  右键单击**引用**节点，然后选择**添加引用**从上下文菜单。  
  
5.  在**添加引用**对话框中，单击**浏览**选项卡上，导航至 VB6Hello.dll，然后将其选中。  
  
     A **vb6hello**引用出现引用列表中。  
  
6.  指向**工具箱**，选择**按钮**控制，并将其拖到**Form1**窗体。  
  
7.  在**属性**窗口中，设置按钮的**文本**属性**Hello**。  
  
8.  双击按钮以添加处理程序代码，并在代码文件中，添加代码，因此处理程序如下所示：  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. 运行该应用程序。 从**调试**菜单上，单击**启动调试**。  
  
 接下来，你需要隔离控件。 每个应用程序使用的 COM 组件是在你的项目中表示为 COM 引用。 下可以看到这些引用**引用**中的节点**解决方案资源管理器**窗口。 (请注意，你可以添加引用直接使用**添加引用**命令**项目**菜单上，或间接通过拖动到窗体 ActiveX 控件。)  
  
 以下步骤演示了如何隔离的 COM 组件和发布更新的应用程序包含独立的控件：  
  
##### <a name="to-isolate-a-com-component"></a>若要隔离的 COM 组件  
  
1.  在**解决方案资源管理器**中**引用**节点中，选择**vb6hello**引用。  
  
2.  在**属性**窗口中，更改的值**Isolated**属性从**False**到**True**。  
  
3.  从**生成**菜单上，单击**生成解决方案**。  
  
 现在，当按 F5，应用程序按预期工作，但它现在正在运行下免注册 com。 为了证明此操作，请尝试注销 VB6Hello.dll 组件，运行在 Visual Studio IDE 外部 RegFreeComDemo1.exe。 此时单击按钮时，它仍然正常工作。 如果你暂时重命名应用程序清单，它将再次失败。  
  
> [!NOTE]
>  可以通过暂时注销模拟 COM 组件不存在。 打开命令提示符下，通过键入，请转到你的系统文件夹`cd /d %windir%\system32`，然后将该组件取消注册通过键入`regsvr32 /u VB6Hello.dll`。 通过键入，可以再次注册该`regsvr32 VB6Hello.dll`。  
  
 最后一步是发布应用程序使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>若要发布应用程序更新与非隔离的 COM 组件  
  
1.  从**生成**菜单上，单击**发布 RegFreeComDemo**。  
  
     出现“发布向导”。  
  
2.  在发布向导中，您可以在其中访问并检查已发布的文件的本地计算机的磁盘上指定的位置。  
  
3.  单击**完成**发布应用程序。  
  
 如果检查已发布的文件，你将注意包含了 sysmon.ocx 文件。 该控件是控件的完全隔离到此应用程序，这意味着，如果最终用户的计算机已使用不同版本的另一个应用程序，将不会影响与此应用程序。  
  
## <a name="referencing-native-assemblies"></a>引用的本机程序集  
 Visual Studio 支持对本机 Visual Basic 6.0 或 c + + 程序集; 的引用这种引用称为本机引用。 你可以判断是否为本机引用验证其**文件类型**属性设置为**本机**或**ActiveX**。  
  
 若要添加本机引用，使用**添加引用**命令，然后浏览到清单。 某些组件放置在 DLL 内部的清单。 在这种情况下，你可以轻松地选择 DLL 本身和 Visual Studio 会将其添加为本机引用如果它检测到组件包含嵌入的清单。 Visual Studio 还会自动将包括任何依赖的文件或程序集清单中列出的是否与引用的组件相同的文件夹。  
  
 COM 控件隔离可以轻松部署尚不具有清单的 COM 组件。 但是，如果包含清单提供组件，则你可以直接引用清单。 事实上，你应始终使用尽可能而不是使用由该组件的作者提供的清单**Isolated**属性。  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>免注册 COM 组件部署的限制  
 免注册 COM 提供了通过传统部署技术的明显优势。 但是，有几个限制和也应该指出需要注意的问题。最大的局限性是它仅适用 Windows XP 或更高版本。 免注册 COM 的实现所需核心操作系统中加载组件的方式的更改。 遗憾的是，免注册 com。 没有下层支持层  
  
 不是每个组件是适合作为免注册 com。 如果下列任一条件，组件不合适：  
  
-   组件是一个进程外服务器。 不支持 EXE 服务器;支持仅 Dll。  
  
-   组件是操作系统的一部分或系统组件，如 XML、 Internet Explorer 或 Microsoft 数据访问组件 (MDAC)。 你应遵循的组件作者; 的重新分发策略请咨询供应商。  
  
-   组件是一个应用程序，例如 Microsoft Office 的一部分。 例如，你不应尝试隔离 Microsoft Excel 对象模型。 这是 Office 的一部分，可以只能用于在计算机上安装的完整 Office 产品。  
  
-   该组件用于作为外接程序或管理单元，如 Office 外接程序或 Web 浏览器中的控件。 此类组件通常要求某些种类的注册方案定义由宿主环境之外清单本身的作用域。  
  
-   该组件管理系统，例如，设备驱动程序打印后台处理程序的物理或虚拟设备。  
  
-   组件是可再发行组件数据访问。 数据应用程序通常需要单独数据访问可再发行组件才能运行安装。 不应尝试隔离组件，如 Microsoft ADO 数据控件、 Microsoft OLE DB 或 Microsoft 数据访问组件 (MDAC)。 相反，如果你的应用程序使用 MDAC 或 SQL Server Express，你应将其设置为系统必备组件;请参阅[如何： 与 ClickOnce 应用程序的安装必备组件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)。  
  
 在某些情况下，有可能的组件开发人员用来重新设计免注册 com。 如果不做到这一点，你仍可以生成并发布的应用程序依赖于它们通过使用引导程序的标准注册方案。 有关详细信息，请参阅[创建引导程序包](../deployment/creating-bootstrapper-packages.md)。  
  
 只能一次每个应用程序隔离的 COM 组件。 例如，不能隔离同一从两个不同的 COM 组件**类库**属于同一个应用程序的项目。 这样将导致生成警告，且应用程序将无法在运行时加载。 若要避免此问题，Microsoft 建议封装单个类库中的 COM 组件。  
  
 即使应用程序的部署不需要注册，有几种应用场景中的 COM，注册开发人员计算机需要安装。 `Isolated`属性需要在开发人员计算机上注册 COM 组件，以自动生成过程生成清单。 没有在生成过程中调用自注册的注册捕获功能。 此外，在类型库中未显式定义的任何类将不会反映在清单中。 当使用预先存在的清单，如本机引用的 COM 组件时该组件可能不需要在开发期间注册。 但是，注册是必需的如果组件是 ActiveX 控件并且你想要将其包含在**工具箱**和 Windows 窗体设计器。  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)