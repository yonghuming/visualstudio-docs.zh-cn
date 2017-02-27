---
title: "为 Windows Installer 部署做好准备扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "vsix msi"
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 为 Windows Installer 部署做好准备扩展
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows Installer 程序包 \(MSI\) 不能用于部署一个 VSIX 包。 但是，您可以提取 MSI 部署一个 VSIX 包的内容。 本文档说明如何准备其默认输出是包含在安装项目中一个 VSIX 包的项目。  
  
## 为 Windows Installer 部署做好准备一个扩展项目  
 将添加到安装项目之前在新的扩展插件项目上执行这些步骤。  
  
#### 若要为 Windows Installer 部署准备一个扩展项目  
  
1.  创建 VSPackage，MEF 组件、 编辑器修饰或其他包括 VSIX 清单的可扩展性项目类型。  
  
2.  在代码编辑器中打开的 VSIX 清单。  
  
3.  设置 VSIX 清单到 InstalledByMsi 元素 `true`。 VSIX 清单的详细信息，请参阅 [VSIX 扩展架构 2.0 参考](../extensibility/vsix-extension-schema-2-0-reference.md)。  
  
     这可以防止 VSIX 安装程序尝试安装该组件。  
  
4.  右键单击该项目中的 **解决方案资源管理器** ，然后单击 **属性**。  
  
5.  选择 **VSIX** 选项卡。  
  
6.  选中标记为框 **到以下位置复制 VSIX 内容** 键入到安装项目将拾取这些文件的路径。  
  
## 从现有的 VSIX 包中提取文件  
 执行以下步骤将现有的 VSIX 包的内容添加到安装项目时不具备的源文件。  
  
#### 若要从现有的 VSIX 包中提取文件  
  
1.  重命名。包含从扩展的 VSIX 文件 *filename*到.vsix *filename*.zip。  
  
2.  将.zip 文件的内容复制到一个目录。  
  
3.  从目录中删除 \[Content\_types\].xml 文件。  
  
4.  编辑 VSIX 清单中，如在前面过程中所示。  
  
5.  将剩余的文件添加到你的安装项目。  
  
## 请参阅  
 [Visual Studio Installer Deployment](http://msdn.microsoft.com/zh-cn/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Walkthrough: Creating a Custom Action](http://msdn.microsoft.com/zh-cn/4bd4b63a-2b91-431e-839c-5752443f0eaf)