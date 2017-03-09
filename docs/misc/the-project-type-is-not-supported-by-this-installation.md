---
title: "项目类型不被此安装支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectflavornotavailable"
ms.assetid: 50e92aff-3ce9-4600-94af-4a16e9dffc90
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 项目类型不被此安装支持
尝试打开需要软件开发工具包 \(SDK\) 不随一起安装 Visual Studio 项目中的类型则会出现此错误。  例如，如果您在未安装 Visual Studio SDK 并且然后尝试打开该 SDK 的一个项目文件的计算机上的 Visual Studio，例如 VSIX 项目则会出现此错误。\(有关 Visual Studio SDK版本的详细信息，请参见 [Extending Visual Studio](http://go.microsoft.com/fwlink/?LinkID=64968)。\)  
  
## 解决方法  
 您必须验证为您尝试打开项目的类型具有正确的 SDK 。  
  
#### 验证是否已具有 SDK 安装。  
  
1.  在菜单栏上，选择**“文件”**，**“新建**、**“项目”**。  
  
2.  在**“新建项目”**对话框的左侧窗格中，依次展开**安装** 节点， **“模板”**节点,选择**另外项目类型** 节点。  
  
3.  查看可用的项目类型确定尝试打开的项目是否可用。  
  
 如果未能找到您尝试打开项目的类型，您没有关联的 SDK 安装。  您必须找到并安装关联的 SDK 打开项目类型。  
  
## 请参阅  
 [Visual Studio 2015 中的新增功能](../ide/what-s-new-in-visual-studio-2015.md)   
 [移植、迁移和升级 Visual Studio 项目](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)