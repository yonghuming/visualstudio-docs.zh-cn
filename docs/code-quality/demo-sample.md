---
title: "演示示例 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "代码分析, 示例"
  - "演示示例 [Visual Studio ALM]"
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# 演示示例
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

以下过程演示如何创建[演练：对 C\/C\+\+ 代码进行缺陷分析](../Topic/Walkthrough:%20Analyzing%20C-C++%20Code%20for%20Defects.md)所对应的示例。  这些过程将创建：  
  
-   一个名为 CppDemo 的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案。  
  
-   一个名为 CodeDefects 的静态库项目。  
  
-   一个名为 Annotations 的静态库项目。  
  
 这些过程还提供静态库的头文件和 .cpp 文件的代码。  
  
### 创建 CppDemo 解决方案和 CodeDefects 项目  
  
1.  单击**“文件”**菜单，指向**“新建”**，然后单击**“新建项目”**。  
  
2.  在**“项目类型”**树列表中，如果 VS 中的默认语言不是 Visual C\+\+，请展开**“其他语言”**。  
  
3.  展开**“Visual C\+\+”**，然后单击**“常规”**。  
  
4.  在**“模板”**中，单击**“空项目”**。  
  
5.  在**“名称”**文本框中，键入 **CodeDefects**。  
  
6.  选中**“创建解决方案的目录”**复选框。  
  
7.  在**“解决方案名称”**文本框中，键入 **CppDemo**。  
  
### 将 CodeDefects 项目配置为静态库  
  
1.  在解决方案资源管理器中，右击**“CodeDefects”**，然后单击**“属性”**。  
  
2.  展开**“配置属性”**，然后单击**“常规”**。  
  
3.  在**“常规”**列表中，选择**“目标文件扩展名”**旁边列中的文本，然后键入 **.lib**。  
  
4.  在**“项目默认值”**中，单击**“配置类型”**旁边的列，然后单击**“静态库\(.lib\)”**。  
  
### 将头文件和源文件添加到 CodeDefects 项目中  
  
1.  在解决方案资源管理器中，展开**“CodeDefects”**，右击**“头文件”**，单击**“添加”**，再单击**“新建项”**。  
  
2.  在**“添加新项”**对话框中，单击**“代码”**，再单击**“头文件\(.h\)”**。  
  
3.  在**“名称”**框中，键入 **Bug.cpp**，然后单击**“添加”**。  
  
4.  复制下面的代码并将其粘贴到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 编辑器中的**“Bug.cpp”**文件。  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  在解决方案资源管理器中，右击**“源文件”**，指向**“新建”**，然后单击**“新建项”**。  
  
6.  在**“添加新项”**对话框中，单击**“C\+\+ 文件\(.cpp\)”**。  
  
7.  在**“名称”**框中，键入 **Bug.cpp**，然后单击**“添加”**。  
  
8.  复制下面的代码并将其粘贴到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 编辑器中的 Bug.h 文件。  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. 单击**“文件”**菜单，然后单击**“全部保存”**。  
  
### 添加 Annotations 项目并将其配置为静态库  
  
1.  在解决方案资源管理器中，单击**“CppDemo”**，指向**“添加”**，然后单击**“新建项目”**。  
  
2.  在**“添加新项目”**对话框中，展开“Visual C\+\+”，单击**“常规”**，再单击**“空项目”**。  
  
3.  在**“名称”**文本框中，键入 **Annotations**，然后单击**“添加”**。  
  
4.  在解决方案资源管理器中，右击**“Annotations”**，然后单击**“属性”**。  
  
5.  展开**“配置属性”**，然后单击**“常规”**。  
  
6.  在**“常规”**列表中，选择**“目标文件扩展名”**旁边列中的文本，然后键入 **.lib**。  
  
7.  在**“项目默认值”**中，单击**“配置类型”**旁边的列，然后单击**“静态库\(.lib\)”**。  
  
### 将头文件和源文件添加到 Annotations 项目中  
  
1.  在解决方案资源管理器中，展开**“Annotations”**，右击**“头文件”**，再单击**“添加”**，然后单击**“新建项”**。  
  
2.  在**“添加新项”**对话框中，单击**“头文件\(.h\)”**。  
  
3.  在**“名称”**框中，键入 **annotations.h**，然后单击**“添加”**。  
  
4.  复制下面的代码并将其粘贴到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 编辑器中的 **annotations.h** 文件。  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  在解决方案资源管理器中，右击**“源文件”**，指向**“新建”**，然后单击**“新建项”**。  
  
6.  在**“添加新项”**对话框中，单击**“代码”**，然后单击**“C\+\+ 文件\(.cpp\)”**。  
  
7.  在**“名称”**框中键入 **annotations.cpp**，再单击**“添加”**。  
  
8.  复制下面的代码并将其粘贴到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 编辑器中的 **annotations.cpp** 文件。  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. 单击**“文件”**菜单，然后单击**“全部保存”**。