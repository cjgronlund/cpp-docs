---
title: "message Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::message"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "message class"
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
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
# message Class
The basic message envelope containing the data payload being passed between messaging blocks.  
  
## Syntax  
  
```
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```  
  
#### Parameters  
 `T`  
 The data type of the payload within the message.  
  
## Members  
  
### Public Typedefs  
  
|Name|Description|  
|----------|-----------------|  
|`type`|A type alias for `T`.|  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[message Constructor](#ctor)|Overloaded. Constructs a `message` object.|  
|[~message Destructor](#dtor)|Destroys the `message` object.|  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[add_ref Method](#add_ref)|Adds to the reference count for the `message` object. Used for message blocks that need reference counting to determine message lifetimes.|  
|[msg_id Method](#msg_id)|Returns the ID of the `message` object.|  
|[remove_ref Method](#remove_ref)|Subtracts from the reference count for the `message` object. Used for message blocks that need reference counting to determine message lifetimes.|  
  
### Public Data Members  
  
|Name|Description|  
|----------|-----------------|  
|[payload Data Member](#payload)|The payload of the `message` object.|  
  
## Remarks  
 For more information, see [Asynchronous Message Blocks](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## Inheritance Hierarchy  
 `message`  
  
## Requirements  
 **Header:** agents.h  
  
 **Namespace:** concurrency  
  
##  <a name="add_ref"></a> add_ref 

 Adds to the reference count for the `message` object. Used for message blocks that need reference counting to determine message lifetimes.  
  
```
long add_ref();
```  
  
### Return Value  
 The new value of the reference count.  
  
##  <a name="ctor"></a> message 

 Constructs a `message` object.  
  
```
message(
    T const& _P);

message(
    T const& _P,
    runtime_object_identity _Id);

message(
    message const& _Msg);

message(
    _In_ message const* _Msg);
```  
  
### Parameters  
 `_P`  
 The payload of this message.  
  
 `_Id`  
 The unique ID of this message.  
  
 `_Msg`  
 A reference or pointer to a `message` object.  
  
### Remarks  
 The constructor that takes a pointer to a `message` object as an argument throws an [invalid_argument](../../../standard-library/invalid-argument-class.md) exception if the parameter `_Msg` is `NULL`.  
  
##  <a name="dtor"></a> ~message 

 Destroys the `message` object.  
  
```
virtual ~message();
```  
  
##  <a name="msg_id"></a> msg_id 

 Returns the ID of the `message` object.  
  
```
runtime_object_identity msg_id() const;
```  
  
### Return Value  
 The `runtime_object_identity` of the `message` object.  
  
##  <a name="payload"></a> payload 

 The payload of the `message` object.  
  
```
T const payload;
```  
  
##  <a name="remove_ref"></a> remove_ref 

 Subtracts from the reference count for the `message` object. Used for message blocks that need reference counting to determine message lifetimes.  
  
```
long remove_ref();
```  
  
### Return Value  
 The new value of the reference count.  
  
## See Also  
 [concurrency Namespace](concurrency-namespace.md)
