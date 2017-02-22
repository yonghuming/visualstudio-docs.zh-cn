---
title: "如何：指定生成事件 (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "生成事件 [Visual Studio]"
  - "生成 [Visual Studio], 事件"
  - "事件 [Visual Studio], 生成"
  - "生成后事件"
  - "生成前事件"
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：指定生成事件 (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以使用生成事件指定在生成开始之前或生成完成之后运行的命令。  只有当生成成功到达生成过程中的这些时间点时，才执行生成事件。  
  
 项目生成后，预先生成事件将被添加到名为 PreBuildEvent.bat 的文件，而后期生成事件将被添加到名为 PostBuildEvent.bat 的文件。  如果要确保错误检查，请向生成步骤中添加您自己的错误检查命令。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 如何指定预先生成和后期生成事件  
  
#### 指定生成事件  
  
1.  在**“解决方案资源管理器”**中，选择要为其指定生成事件的项目。  
  
2.  在**“项目”**菜单上，单击**“属性”**。  
  
3.  选择**“生成事件”**选项卡。  
  
4.  在**“预先生成事件命令行”**框中指定生成事件的语法。  
  
    > [!NOTE]
    >  如果项目是最新的且没有触发任何生成，则不会运行预生成事件。  
  
5.  在**“后期生成事件命令行”**框中指定生成事件的语法。  
  
    > [!NOTE]
    >  在运行 .bat 文件的所有后期生成命令之前添加一个 `call` 语句。  例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。  
  
6.  在**“运行生成后事件”**框中指定运行生成后事件的条件。  
  
    > [!NOTE]
    >  若要添加长语法或从 [预生成事件\/生成后事件命令行对话框](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) 中选择任何生成宏，请单击省略号按钮 \(**…**\) 以显示编辑框。  
  
     该生成事件语法可以包括命令提示或 .bat 文件中任何有效的命令。  批处理文件名的前面应带有 `call`，以确保后面的所有命令都被执行。  
  
     **注意** 如果预先生成事件或后期生成事件不能成功完成，您可以通过使事件操作退出来终止生成，并显示指示操作成功的代码零 \(0\) 以外的其他代码。  
  
## 示例：如何使用后期生成事件更改清单信息  
 下面的过程说明如何使用从后期生成事件（项目目录中的 .exe.manifest 文件）中调用的 .exe 命令设置应用程序清单中的操作系统最低版本。  操作系统最低版本是一个由四个部分组成的编号，如 4.10.0.0。  为此，该命令会更改清单的 `<dependentOS>` 节：  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### 创建用于更改应用程序清单的 .exe 命令  
  
1.  针对该命令，创建一个控制台应用程序。  在**“文件”**菜单中，指向**“新建”**，然后单击**“项目”**。  
  
2.  在**“新建项目”**对话框中，展开**“Visual C\#”**，单击**“Windows”**，再单击**“控制台应用程序”**模板。  将项目命名为 `ChangeOSVersionCS`。  
  
3.  在 Program.cs 中，将以下行添加到文件顶部的其他 `using` 语句：  
  
    ```  
    using System.Xml;  
    ```  
  
4.  在 `ChangeOSVersionCS` 命名空间中，使用以下代码替换 `Program` 类的实现：  
  
    ```  
    class Program  
    {  
       /// <summary>  
       /// This function will set the minimum operating system version for a ClickOnce application.  
       /// </summary>  
       /// <param name="args">  
       /// Command Line Arguments:  
       /// 0 - Path to application manifest (.exe.manifest).  
       /// 1 - Version of OS  
       ///</param>  
       static void Main(string[] args)  
       {  
          string applicationManifestPath = args[0];  
          Console.WriteLine("Application Manifest Path: " + applicationManifestPath);  
  
          // Get version name.  
          Version osVersion = null;  
          if (args.Length >=2 ){  
             osVersion = new Version(args[1]);  
          }else{  
             throw new ArgumentException("OS Version not specified.");  
          }  
          Console.WriteLine("Desired OS Version: " + osVersion.ToString());  
  
          XmlDocument document;  
          XmlNamespaceManager namespaceManager;  
          namespaceManager = new XmlNamespaceManager(new NameTable());  
          namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");  
          namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");  
  
          document = new XmlDocument();  
          document.Load(applicationManifestPath);  
  
          string baseXPath;  
          baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";  
  
          // Change minimum required operating system version.  
          XmlNode node;  
          node = document.SelectSingleNode(baseXPath, namespaceManager);  
          node.Attributes["majorVersion"].Value = osVersion.Major.ToString();  
          node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();  
          node.Attributes["buildNumber"].Value = osVersion.Build.ToString();  
          node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();  
  
          document.Save(applicationManifestPath);  
       }  
    }  
    ```  
  
     此命令带两个参数：应用程序清单的路径（即生成过程在其中创建清单的文件夹，通常为 Projectname.publish），以及新的操作系统版本。  
  
5.  生成项目。  在**“生成”**菜单上，单击**“生成解决方案”**。  
  
6.  将 .exe 文件复制到一个目录（如 `C:\TEMP\ChangeOSVersionVB.exe`）。  
  
 然后，在后期生成事件中调用此命令以修改应用程序清单。  
  
#### 调用后期生成事件以修改应用程序清单  
  
1.  为要发布的项目创建一个 Windows 应用程序。  在**“文件”**菜单中，指向**“新建”**，然后单击**“项目”**。  
  
2.  在**“新建项目”**对话框中，展开**“Visual C\#”**，单击**“Windows”**，再单击**“Windows 窗体应用程序”**模板。  将项目命名为 `CSWinApp`。  
  
3.  在**“解决方案资源管理器”**中选择该项目，然后在**“项目”**菜单中单击**“属性”**。  
  
4.  在“项目设计器”中，找到**“发布”**页，并将**“发布位置”**设置为 `C:\TEMP\`。  
  
5.  通过单击**“立即发布”**发布该项目。  
  
     将生成清单文件，并将其置于 `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest` 中。  若要查看该清单，请右击该文件，单击**“打开方式”**，选择**“从列表中选择程序”**，然后单击**“记事本”**。  
  
     在该文件中搜索 `<osVersionInfo>` 元素。  例如，版本可能是：  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  在“项目设计器”中，单击**“生成事件”**选项卡并单击**“编辑后期生成”**按钮。  
  
7.  在**“后期生成事件命令行”**框中，键入以下命令：  
  
     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     生成项目时，此命令会将应用程序清单中的操作系统最低版本更改为 5.1.2600.0。  
  
     由于 `$(TargetPath)` 宏表示所创建的可执行文件的完整路径，因此 `$(TargetPath)`.manifest 将指定在 bin 目录中创建的应用程序清单。  发布时会将此清单复制到您先前设置的发布位置。  
  
8.  重新发布项目。  转到**“发布”**页，单击**“立即发布”**。  
  
     再次查看该清单。  若要查看该清单，请打开发布目录，右击该文件，单击**“打开方式”**，选择**“从列表中选择程序”**，然后单击**“记事本”**。  
  
     版本应显示为：  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## 请参阅  
 [“项目设计器”\-\>“生成事件”页 \(C\#\)](../ide/reference/build-events-page-project-designer-csharp.md)   
 [预生成事件\/生成后事件命令行对话框](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [如何：指定生成事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [在 Visual Studio 中构建应用程序](../ide/compiling-and-building-in-visual-studio.md)