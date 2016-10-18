---
title: "invalid_scheduler_policy_value Class"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::invalid_scheduler_policy_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_scheduler_policy_value class"
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
caps.latest.revision: 18
ms.author: "mithom"
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
# invalid_scheduler_policy_value Class
This class describes an exception thrown when a policy key of a `SchedulerPolicy` object is set to an invalid value for that key.  
  
## Syntax  
  
```
class invalid_scheduler_policy_value : public std::exception;
```  
  
## Members  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[invalid_scheduler_policy_value::invalid_scheduler_policy_value Constructor](../parallel/invalid_scheduler_policy_thread_specification-class.md#invalid_scheduler_policy_value__invalid_scheduler_policy_value_constructor)|Overloaded. Constructs an `invalid_scheduler_policy_value` object.|  
  
## Inheritance Hierarchy  
 `exception`  
  
 `invalid_scheduler_policy_value`  
  
## Requirements  
 **Header:** concrt.h  
  
 **Namespace:** concurrency  
  
##  <a name="invalid_scheduler_policy_thread_specification__invalid_scheduler_policy_thread_specification_constructor"></a>  invalid_scheduler_policy_thread_specification::invalid_scheduler_policy_thread_specification Constructor  
 Constructs an `invalid_scheduler_policy_value` object.  
  
```
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```  
  
### Parameters  
 `_Message`  
 A descriptive message of the error.  
  
## See Also  
 [concurrency Namespace](../parallel/concurrency-namespace.md)   
 [SchedulerPolicy Class](../parallel/schedulerpolicy-class.md)   
 [PolicyElementKey Enumeration](../parallel/concurrency-namespace-enums.md)   
 [SchedulerPolicy::SetPolicyValue Method](../parallel/schedulerpolicy-class.md#schedulerpolicy__setpolicyvalue_method)   
 [SchedulerPolicy::SetConcurrencyLimits Method](../parallel/schedulerpolicy-class.md#schedulerpolicy__setconcurrencylimits_method)
