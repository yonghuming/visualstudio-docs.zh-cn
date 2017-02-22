---
title: "将单元测试作为 64 位进程运行 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "单元测试, 创建"
  - "单元测试, 运行"
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "mlearned"
manager: "douge"
---
# 将单元测试作为 64 位进程运行
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您有一台 64 位的计算机，则可以作为 64 位进程来运行单元测试并捕获代码覆盖率信息。  
  
## 作为 64 位进程运行单元测试  
  
#### 作为 64 位进程运行单元测试  
  
1.  如果您的代码或测试是以 32 位\/x86 形式编译的，但您现在想作为 64 位进程运行这些代码和测试，请以**“任何 CPU”**或**“64 位”**的形式对其进行重新编译。  
  
    > [!TIP]
    >  为了最大限度地提高灵活性，您应使用**“任何 CPU”**配置来编译测试项目。  然后，可以在 32 位和 64 位代理上运行。  使用**“64 位”**配置编译测试项目没有什么特别的用处。  
  
2.  从 Visual Studio 菜单中，选择 **测试**，然后选择 **设置**，然后选择 **处理器架构**。  选择 **x64** 运行测试作为 64 位进程。  
  
     \- 或 \-  
  
     指定 `<TargetPlatform>x64</TargetPlatform>` 中 .runsettings 文件。  此方法的一个优点是可以指定的设置组在不同文件和不同设置之间快速切换。  可以同时复制在解决方案间的设置。  有关详细信息，请参阅[使用 .runsettings 文件配置单元测试](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)。  
  
## 请参阅  
 [使用测试资源管理器运行单元测试](../test/run-unit-tests-with-test-explorer.md)   
 [单元测试代码](../test/unit-test-your-code.md)   
 [指定 Visual Studio 测试的测试设置](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests)