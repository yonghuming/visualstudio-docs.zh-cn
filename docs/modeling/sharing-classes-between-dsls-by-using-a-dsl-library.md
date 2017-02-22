---
title: "使用 DSL 库在 DSL 之间共享类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 7
caps.handback.revision: 7
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 使用 DSL 库在 DSL 之间共享类
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可视化和建模 SDK，则可以创建可导入到另一个 DSL 的不完全 DSL 定义。  这使您可以分解类似的模型的公共部分。  
  
## 创建和使用 DSL 库  
  
#### 创建 DSL 库  
  
1.  创建新的 DSL 项目，然后选择 DSL 库解决方案模板。  
  
     一个 DSL 项目中包含一个空的方式创建。  
  
2.  可以添加字段类，关系，形状等。  
  
     元素在库中必须形成一个嵌入的树。  
  
     若要定义导入程序中使用的关系，创建两个字段类并创建它们之间的关系。  
  
     考虑将字段设置类的 **继承修饰符** 到 `Abstract`。  
  
3.  可以添加在 DSL 资源管理器中定义的元素，如连接生成器。  
  
4.  可以将需要额外的代码的自定义项，如验证约束。  
  
5.  单击 **转换所有模板**。  
  
6.  生成项目。  
  
7.  当将其他人员的 DSL 可以使用时，必须提供生成程序集 \(dll\) 和文件 `DslDefinition.dsl`。  可以找到文件夹中生成程序集在下 `Dsl\bin\*`  
  
#### 导入 DSL 库  
  
1.  在另一个 DSL 定义，在 **DSL 资源管理器**，右击 DSL 的根类，然后单击 **添加新 DslLibrary 导入**。  
  
2.  在 " 属性 " 窗口中，将库的 **文件路径** 。  您可以使用一个相对路径或绝对路径。  
  
     导入的库出现在 DSL 资源管理器中，在只读模式下。  
  
3.  可以使用导入的类作为基类。  创建域类在导入的 DSL 和在 " 属性 " 窗口中，将 **基类** 对导入的类。  
  
4.  单击转换所有模板。  
  
5.  添加到 DSL 项目对由 DSL 库项目生成的程序集 \(dll\)。  
  
6.  生成解决方案。  
  
 DSL 库可以导入其他库。  当导入库时，其导入还自动出现在 DSL 资源管理器。  
  
## 请参阅  
 [如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)