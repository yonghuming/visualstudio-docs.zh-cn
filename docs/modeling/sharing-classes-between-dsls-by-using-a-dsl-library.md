---
title: "共享类之间使用 DSL 库 Dsl |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: "7"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: ed225f315c92cf9276eb97fcb78e1730250ecd4c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>使用 DSL 库在 DSL 之间共享类
在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可视化和建模 SDK，你可以创建，你可以导入到另一个 DSL 的 DSL 定义不完整。 这样可以考虑因素的类似模型的公共部分。  
  
## <a name="creating-and-using-dsl-libraries"></a>创建和使用 DSL 库  
  
#### <a name="to-create-a-dsl-library"></a>若要创建 DSL 库  
  
1.  创建一个新的 DSL 项目，并选择 DSL 库解决方案模板。  
  
     将使用一个空模型创建单个 DSL 项目。  
  
2.  你可以添加域类、 关系、 形状等。  
  
     库中的元素没有用于形成单个嵌入树。  
  
     若要定义一种关系，可以使用导入程序，创建两个域类，并创建它们之间的关系。  
  
     请考虑设置**继承修饰符**到的域类`Abstract`。  
  
3.  您可以添加在 DSL 资源管理器，如连接生成器中定义的元素。  
  
4.  您可以添加自定义需要其他代码，例如验证约束。  
  
5.  单击**转换所有模板**。  
  
6.  生成项目。  
  
7.  让其他人有机会使用 DSL 分发时，必须提供编译的程序集 (DLL) 和文件`DslDefinition.dsl`。 你可以在下的文件夹中找到编译的程序集`Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>若要导入 DSL 库  
  
1.  在另一个 DSL 定义中，在**DSL 资源管理器**，右键单击 DSL，根类，然后单击**添加新 DslLibrary 导入**。  
  
2.  在属性窗口中，设置**文件路径**的库。 你可以使用相对或绝对路径。  
  
     导入的库将显示在 DSL 资源管理器，在只读模式下。  
  
3.  你可以使用导入的类作为基类。 在导入的 DSL，创建域类并在属性窗口中，设置**基类**到导入的类。  
  
4.  单击转换所有模板。  
  
5.  DSL 项目中，添加对由 DSL 库项目生成的程序集 (DLL) 的引用。  
  
6.  生成解决方案。  
  
 DSL 库可以导入其他库。 当你导入的库，其导入也会自动出现在 DSL 资源管理器。  
  
## <a name="see-also"></a>另请参阅  
 [如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
