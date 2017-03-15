---
title: "演练：使用自动化调入 Visual Studio SDK | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "演练 [Visual Studio SDK], 使用自动化进行调用"
ms.assetid: ca4dab48-632c-4c2a-8c84-57c027e37987
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# 演练：使用自动化调入 Visual Studio SDK
本演练演示如何创建使用 Visual Studio 服务的 Visual Studio 外接程序。 创建的外接程序会获取服务提供程序并使用它来获取服务。 可以使用此相同技术来获取任何提供的 Visual Studio 服务。 有关服务和服务提供程序的详细信息，请参见 [使用并提供服务](../extensibility/using-and-providing-services.md)。 以下过程演示如何创建一个外接程序，然后从该外接程序获取服务。  
  
## 创建外接程序  
 在本部分中，会使用 Visual Studio 外接程序项目模板创建一个 Visual Studio 外接程序。  
  
#### 创建外接程序  
  
1.  创建一个新 Visual Studio 项目（“文件\/新建\/项目”）。  
  
2.  在“新建项目”对话框的左窗格中展开“其他项目类型”节点，然后单击“扩展性”节点。 选择“Visual Studio 外接程序”。  
  
3.  创建一个名为 `Addin` 的新外接程序项目。  
  
     在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 外接程序向导中，单击“下一步”。  
  
4.  在“选择编程语言”页上，选择“使用 Visual C\# 创建外接程序”或“使用 Visual Basic 创建外接程序”。  
  
5.  在“选择应用程序主机”页上，选择“Microsoft Visual Studio \<版本\>”。  
  
6.  在“输入名称和说明”页上，在“名称”框中输入 `MyAddin`，在“说明”框中输入 `MyAddin Walkthrough`。  
  
7.  在“选择外接程序选项”页上，在“是否为外接程序创建命令栏用户界面?”下选择工具菜单项的对应选项。 清除其他复选框。  
  
8.  接受所有其他默认值。  
  
9. 生成解决方案并确认编译时不会产生错误。  
  
## 从外接程序获取服务  
 以下步骤指导你完成从外接程序获取服务的过程。  
  
#### 获取服务  
  
1.  打开文件 Connect.cs 或 Connect.vb 并将这些行添加到 `using` \(C\#\) 或 `Imports` \(Visual Basic\) 语句：  
  
     [!CODE [VSSDKAddin#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkaddin#1)]  
  
2.  在“解决方案资源管理器”中右键单击项目节点，然后添加这些 .NET 引用：  
  
    ```  
    Microsoft.VisualStudio.OLE.Interop Microsoft.VisualStudio.Shell.Interop  
    ```  
  
3.  将这些代码行添加到 `Exec` 方法的 `if(commandName == "Addin.Connect.Addin")` 或 `If commandName = "Addin.Connect.Addin" Then` 子句：  
  
     [!CODE [VSSDKAddin#2](../CodeSnippet/VS_Snippets_VSSDK/vssdkaddin#2)]  
  
     此代码将当前应用程序对象（类型为 `DTE2`）强制转换为 `IOleServiceProvider`，然后调用 `QueryService` 以获取 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 服务。 此服务提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 接口。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> 方法在外接程序运行时显示一个消息框。  
  
4.  通过按 F5 在调试模式下生成并启动外接程序项目。  
  
     这会启动 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的另一个实例。  
  
5.  在新的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 实例中，在“工具”菜单上，单击“外接程序”。 消息框会显示以下内容：  
  
    ```  
    MyAddin Inside Addin.Connect  
    ```  
  
## 请参阅  
 [如何：停用并移除外接程序](../Topic/How%20to:%20Deactivate%20and%20Remove%20an%20Add-In.md)