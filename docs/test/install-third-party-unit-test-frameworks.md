---
title: "安装第三方单元测试框架 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 10
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 10
---
# 安装第三方单元测试框架
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 测试资源管理器可以运行任何针对该资源管理器开发了适配器接口的单元测试框架。  框架的安装程序会安装二进制文件，并为它支持的语言添加 Visual Studio 项目模板。  使用模板创建项目时，框架会向测试资源管理器注册。  Visual Studio 解决方案可以包含使用不同框架和面向不同语言的单元测试项目。  测试资源管理器可运行所有这些解决方案。  
  
 **要求**  
  
-   Visual Studio Enterprise、Visual Studio Professional  
  
## 获取第三方框架  
 可以使用 Visual Studio 扩展管理器，或是从 MSDN 网站上的 Visual Studio 库下载并安装很多第三方单元测试框架。  还可以从其他站点（如框架的网站）下载框架。  
  
### 从 Visual Studio 安装  
  
1.  在标准菜单上选择**“工具”**，然后选择**“扩展和更新”**。  
  
2.  依次展开**“联机”**、**“Visual Studio 库”**和**“工具”**。  选择**“测试”**。  
  
3.  浏览列表以查找框架。  
  
4.  选择框架，然后选择**“下载”**。  
  
 有关详细信息，请参阅[查找和使用 Visual Studio 扩展](../ide/finding-and-using-visual-studio-extensions.md)。  
  
### 从 Web 安装  
 如果你了解所需框架：  
  
1.  在 MSDN 网站上打开 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkId=236267)。  
  
2.  在**“查找”**框中输入框架的名称。  
  
3.  在结果列表中选择框架以导航到用于该工具的 Visual Studio 库页面。  
  
 浏览框架以及其他测试工具的列表：  
  
1.  在 MSDN 网站上打开 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkId=236267)。  
  
2.  选择**“浏览”**。  
  
3.  在**“类别”**列表中，展开**“工具”**节点，然后选择**“测试”**。  
  
4.  在结果列表中选择框架以导航到用于该工具的 Visual Studio 库页面。  
  
## 请参阅  
 [单元测试代码](../test/unit-test-your-code.md)