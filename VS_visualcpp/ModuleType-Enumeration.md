---
title: "ModuleType Enumeration"
ms.custom: na
ms.date: 10/04/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
caps.latest.revision: 5
manager: ghogen
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - ru-ru
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - pl-pl
  - pt-br
  - tr-tr
---
# ModuleType Enumeration
Specifies whether a module should support an in-process server or an out-of-process server.  
  
## Syntax  
  
```  
enum ModuleType;  
```  
  
## Members  
  
### Values  
  
|Name|Description|  
|----------|-----------------|  
|`InProc`|An in-process server.|  
|`OutOfProc`|An out-of-process server.|  
|`DisableCaching`|Disable caching mechanism on Module.|  
|`InProcDisableCaching`|Combination of `InProc` and `DisableCaching`.|  
|`OutOfProcDisableCaching`|Combination of `OutOfProc` and `DisableCaching`.|  
  
## Requirements  
 **Header:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## See Also  
 [Microsoft::WRL Namespace](../VS_visualcpp/Microsoft--WRL-Namespace.md)