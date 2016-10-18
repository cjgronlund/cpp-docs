---
title: "Automation in a DLL"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLLs [C++], Automation"
  - "Automation [C++], DLLs"
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
caps.latest.revision: 8
ms.author: "corob"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# Automation in a DLL
When you choose the Automation option in the MFC DLL Wizard, the wizard provides you with the following:  
  
-   A starter object description language (.ODL) file  
  
-   An include directive in the STDAFX.h file for Afxole.h  
  
-   An implementation of the `DllGetClassObject` function, which calls the **AfxDllGetClassObject** function  
  
-   An implementation of the `DllCanUnloadNow` function, which calls the **AfxDllCanUnloadNow** function  
  
-   An implementation of the `DllRegisterServer` function, which calls the [COleObjectFactory::UpdateRegistryAll](../Topic/COleObjectFactory::UpdateRegistryAll.md) function  
  
## What do you want to know more about?  
  
-   [Automation Servers](../mfc/automation-servers.md)  
  
## See Also  
 [DLLs in Visual C++](../build/dlls-in-visual-c--.md)