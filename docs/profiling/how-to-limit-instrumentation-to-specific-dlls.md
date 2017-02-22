---
title: "如何：将检测限定为特定 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "性能工具, 运行时分析控件窗口"
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：将检测限定为特定 DLL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过使用检测分析方法，可以将分析数据的收集限定为应用程序中的一个或多个 DLL。  要分析应用程序中的一个或多个 DLL，请创建将 .dll 文件作为目标包括的性能会话。  可以将要分析的 DLL 指定为 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案中的项目或独立的二进制文件。  
  
### 将检测限定为 Visual Studio 解决方案中的特定 DLL  
  
1.  在 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]中打开包含该 DLL 的解决方案。  
  
2.  在**“分析”**菜单上，选择**“启动性能向导”**。  
  
3.  选择**“检测”**作为分析方法，然后单击**“下一步”**。  
  
4.  从**“要分析以下哪些可用目标?”**中，选择 .dll 项目的名称，然后单击**“下一步”**。  
  
5.  单击**“完成”**退出向导，将在**“性能资源管理器”**窗口中显示新的性能会话。  
  
6.  右击**“目标”**，然后选择**“添加目标项目”**。  
  
7.  在**“添加目标项目”**列表中，选择执行 DLL 时要使用的可执行项目。  
  
     可选。  您可以添加任何要分析的 DLL 项目。  
  
8.  若要防止对某个已添加的项目进行数据收集，请右击该项目的名称，然后清除**“检测”**复选框。  
  
### 将要分析的特定 DLL 指定为独立的二进制文件  
  
1.  打开 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]。  
  
2.  在**“分析”**菜单上，选择**“启动性能向导”**。  
  
3.  在**“要分析以下哪些可用目标?”**中，选择**“分析动态链接库\(.DLL\)”**，然后单击**“下一步”**。  
  
4.  在该向导的第二页上，执行下列步骤：  
  
    -   在**“DLL 路径”**中键入要分析的 .dll 文件的路径和文件名。  您还可以单击省略号按钮 \(...\) 在**“要分析的动态链接库”**对话框中查找该文件。  请注意，必须指定您接下来将选择的可执行 \(.exe\) 文件将启动的 .dll 文件的副本。  
  
    -   在**“可执行文件路径”**中键入将执行该 .dll 的可执行 \(.exe\) 文件的路径和文件名。  您还可以单击省略号按钮 \(...\) 在**“要启动的可执行文件”**对话框中查找该文件。  
  
    -   可选。  在**“命令行参数”**中键入要传递给可执行文件的任何命令行参数。  如有必要，请在**“工作目录”**中指定应用程序的工作目录。  
  
    -   单击**“下一步”**。  
  
5.  选择**“检测”**作为分析方法，然后单击**“下一步”**。  
  
6.  单击**“完成”**退出向导，将在**“性能资源管理器”**窗口中显示新的性能会话。  
  
7.  可选。  若要添加更多 .dll 文件，请右击**“目标”**，然后选择**“添加目标二进制文件”**。  在**“添加目标二进制文件”**对话框中选择这些文件。  
  
    > [!NOTE]
    >  请勿指定执行 DLL 的可执行 \(.exe\) 文件。  
  
## 请参阅  
 [控制数据收集](../profiling/controlling-data-collection.md)   
 [如何：将检测限定为特定函数](../profiling/how-to-limit-instrumentation-to-specific-functions.md)