---
title: "如何： 保存和编辑连接字符串 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 4a7482c269cd978d2c1848c896985b1194797e42
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-save-and-edit-connection-strings"></a>如何：保存和编辑连接字符串
可以保存在应用程序配置文件 （也称为应用程序设置） 或硬编码在你的应用程序中直接在 Visual Studio 应用程序中的连接字符串。 在应用程序配置文件中保存连接字符串简化了维护应用程序的任务。 如果连接字符串需要进行更改，则可以在应用程序设置文件中对其进行更新（这与必须在源代码中对其进行更改并重新编译应用程序相反）。

将敏感信息（如密码）存储在连接字符串中可能会影响应用程序的安全性。 保存在应用程序配置文件中的连接字符串是未经加密处理的，因此其他人有可能访问该文件并查看其内容。 若要控制对数据库的访问，一种较为安全的方法是使用 Windows 集成安全性。

如果不选择使用 Windows 集成安全性，并且数据库需要用户名和密码，则可以在连接字符串中省略这些内容，但需要应用程序提供此信息才能成功连接到数据库。 例如，可以创建一个对话框提示用户提供此信息并在运行时动态生成连接字符串。 如果在发送到数据库的途中该信息被截获，则安全性将得不到保证。 有关详细信息，请参阅[保护连接信息](/dotnet/framework/data/adonet/protecting-connection-information)。

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>若要保存连接字符串中数据源配置向导
在**数据源配置向导**，选择将连接保存在连接字符串保存到应用程序配置文件页上的选项。

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>将连接字符串直接保存到应用程序设置中
- 在解决方案资源管理器中，双击我的项目图标 (Visual Basic 中) 或属性图标 (C#) 以打开项目设计器。
- 选择设置选项卡。
- 输入连接字符串的名称。 当在代码中访问该连接字符串时引用此名称。
- 设置 （连接字符串） 的类型。
- 将范围设置为应用程序。
- 在值字段中，键入你的连接字符串，或单击值字段，以打开连接属性对话框中，以生成连接字符串中的省略号 （...） 按钮。  

## <a name="editing-connection-strings-stored-in-application-settings"></a>编辑存储在应用程序设置的连接字符串
你可以修改通过使用项目设计器保存在应用程序设置的连接信息。  

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>编辑存储在应用程序设置中的连接字符串
- 在解决方案资源管理器中，双击我的项目图标 (Visual Basic 中) 或属性图标 (C#) 以打开项目设计器。
- 选择设置选项卡。
- 找到你想要编辑，并在值字段中选择文本的连接。
- 编辑连接字符串的值字段中，或单击要编辑与连接属性对话框中的连接的值字段中的省略号 （...） 按钮。  

## <a name="editing-connection-strings-for-datasets"></a>编辑数据集的连接字符串
你可以修改为数据集中的每个 TableAdapter 的连接信息。  

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>若要编辑数据集中 TableAdapter 的连接字符串
- 在解决方案资源管理器中，双击具有你想要编辑的连接的数据集 （.xsd 文件）。
- 选择具有想要编辑的连接的查询的 TableAdapter。
- 在属性窗口中，展开连接节点。
- 若要快速修改连接字符串，编辑 ConnectionString 属性，或单击连接属性的向下箭头，然后选择新的连接。

## <a name="security"></a>安全性
将敏感信息（如密码）存储在连接字符串中可能会影响应用程序的安全性。 若要控制对数据库的访问，一种较为安全的方法是使用 Windows 集成安全性。
有关详细信息，请参阅[保护连接信息](/dotnet/framework/data/adonet/protecting-connection-information)。
  
## <a name="see-also"></a>请参阅
[添加连接](../data-tools/add-new-connections.md)