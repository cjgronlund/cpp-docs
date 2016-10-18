---
title: "How to: Perform Map and Reduce Operations in Parallel"
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
  - "parallel_transform function, example"
  - "parallel map and reduce, example"
  - "parallel_reduce function, example"
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
caps.latest.revision: 7
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
# How to: Perform Map and Reduce Operations in Parallel
This example shows how to use the [concurrency::parallel_transform](../Topic/parallel_transform%20Function.md) and [concurrency::parallel_reduce](../Topic/parallel_reduce%20Function.md) algorithms and the [concurrency::concurrent_unordered_map](../parallel/concurrent_unordered_map-class.md) class to count the occurrences of words in files.  
  
 A *map* operation applies a function to each value in a sequence. A *reduce* operation combines the elements of a sequence into one value. You can use the Standard Template Library (STL) [std::transform](../Topic/transform.md)[std::accumulate](../Topic/accumulate.md) classes to perform map and reduce operations. However, to improve performance for many problems, you can use the `parallel_transform` algorithm to perform the map operation in parallel and the `parallel_reduce` algorithm to perform the reduce operation in parallel. In some cases, you can use `concurrent_unordered_map` to perform the map and the reduce in one operation.  
  
## Example  
 The following example counts the occurrences of words in files. It uses std::vector to represent the contents of two files. The map operation computes the occurrences of each word in each vector. The reduce operation accumulates the word counts across both vectors.  
  
 [!code[concrt-parallel-map-reduce#1](../parallel/codesnippet/CPP/how-to--perform-map-and-reduce-operations-in-parallel_1.cpp)]  
  
## Compiling the Code  
 To compile the code, copy it and then paste it in a Visual Studio project, or paste it in a file that is named `parallel-map-reduce.cpp` and then run the following command in a Visual Studio Command Prompt window.  
  
 **cl.exe /EHsc parallel-map-reduce.cpp**  
  
## Robust Programming  
 In this example, you can use the `concurrent_unordered_map` class—which is defined in concurrent_unordered_map.h—to perform the map and reduce in one operation.  
  
 [!code[concrt-parallel-map-reduce#2](../parallel/codesnippet/CPP/how-to--perform-map-and-reduce-operations-in-parallel_2.cpp)]  
  
 Typically, you parallelize only the outer or the inner loop. Parallelize the inner loop if you have relatively few files and each file contains many words. Parallelize the outer loop if you have relatively many files and each file contains few words.  
  
## See Also  
 [Parallel Algorithms](../parallel/parallel-algorithms.md)   
 [parallel_transform Function](../Topic/parallel_transform%20Function.md)   
 [parallel_reduce Function](../Topic/parallel_reduce%20Function.md)   
 [concurrent_unordered_map Class](../parallel/concurrent_unordered_map-class.md)