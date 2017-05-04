---
title: "Office 解决方案的事件日志 | Microsoft Docs"
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
  - "Office 应用程序 [Visual Studio 中的 Office 开发]，事件查看器"
  - "ClickOnce 部署 [Visual Studio 中的 Office 开发]，事件查看器"
  - "部署应用程序 [Visual Studio 中的 Office 开发]，事件查看器"
  - "Visual Studio 中的 Office 开发，事件查看器"
ms.assetid: 31a246fe-ce1c-4f0e-9a21-9cf974c247fe
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Office 解决方案的事件日志
  你可以使用 Windows 事件查看器来查看当你安装或卸载 Office 解决方案时，由 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 捕捉到的异常消息。 你可使用事件记录器中的这些消息来解决安装和部署问题。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 读取事件日志  
 打开“事件查看器”和筛选器以筛选出你想要查看的事件。  
  
#### 读取 Windows Server 2003 和 Windows XP 中的事件日志  
  
1.  在“控制面板”中，打开“管理工具”。  
  
2.  启动“事件查看器”。  
  
3.  在事件日志的列表中，选择“应用程序”。  
  
4.  在“视图”菜单中，单击“筛选器”。  
  
5.  在“事件源”列表中，选择“VSTO 4.0”。  
  
6.  对于安装事件，在“事件 ID”框中，键入 **4096**。  
  
7.  单击“确定”，以查看已筛选的视图。  
  
#### 读取 Windows 7、Windows Vista 和 Windows Server 2008 中的事件日志  
  
1.  在“控制面板”中，打开“管理工具”。  
  
2.  启动“事件查看器”。  
  
3.  展开“Windows 日志”。  
  
4.  在事件日志的列表中，选择“应用程序”。  
  
5.  在“操作”菜单上，单击“筛选当前日志”。  
  
6.  在“事件源”列表中，选择“VSTO 4.0”。  
  
7.  对于安装事件，在“事件 ID”框中，键入 **4096**。  
  
8.  单击“确定”，以查看已筛选的视图。  
  
 事件查看器包括以下信息：  
  
-   解决方案部署清单的位置。  
  
-   描述此错误或异常原因的消息。  
  
 这些异常消息可以帮助你确定安装问题的原因，例如不受信任的证书、不受信任的文档位置或无效的部署清单。  
  
 卸载 Office 解决方案后，异常消息保留在事件日志中。  
  
 若要在运行 Office 解决方案时显示或记录异常消息，请参阅[调试 Office 项目](../vsto/debugging-office-projects.md)和[调试 Office 项目](../vsto/debugging-office-projects.md)。  
  
### 本地化  
 异常消息的语言由 Visual Studio Tools for Office 运行时语言确定。 例如，如果最终用户的计算机已安装了日语语言包，则以日语将异常消息写入事件日志。  
  
## 禁用事件记录器  
 默认情况下，安装或卸载 Office 解决方案时事件记录器处于禁用状态。 你可以通过将 VSTO\_EVENTLOGDISABLED 环境变量设置为“1”（一）来禁用事件记录器。  
  
#### 禁用事件日志  
  
1.  在“控制面板”中，打开“系统”。  
  
2.  在**“高级”**选项卡上，单击**“环境变量”**。  
  
3.  在“系统变量”窗格中，单击“新建”。  
  
4.  在“新建系统变量”对话框中，在“变量名称”框中键入 **VSTO\_EVENTLOGDISABLED**。  
  
5.  在“变量值”框中，键入 **1**。  
  
6.  单击“确定”。  
  
## 请参阅  
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)   
 [Office 解决方案部署疑难解答](../vsto/troubleshooting-office-solution-deployment.md)  
  
  