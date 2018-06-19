---
title: 如何逐一查看商務規則中的 ArrayList |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, ArrayList
- business rules, arrays
- Business Rules Framework, programming
ms.assetid: 935e8648-72dc-4128-986c-72b0487bc074
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9010907cfe9fb6d79a8d9fcead533376b014640e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970788"
---
# <a name="how-to-iterate-arraylist-in-business-rules"></a>如何逐一查看商務規則中的 ArrayList
本節提供範例逐一查看成員**ArrayList**商務規則中。  
  
 假設您有**ArrayList**集合與**MyClass**物件。 您的商務規則看起來將如下所示。  
  
## <a name="rule-a"></a>規則 A  
 IF 1==1  
  
 THEN Assert (ArrayList.GetEnumerator)  
  
 **IEnumerator**類型判斷提示至工作記憶體中，因為規則條件 (1 = = 1) 一律評估為 true。  
  
## <a name="rule-b"></a>規則 B  
 IF IEnumerator.MoveNext  
  
 THEN    Assert (IEnumerator.get_Current)  
  
 Update (IEnumerator)  
  
 規則重複處理透過**ArrayList**，每個**MyClass**集合中的物件判斷提示至工作記憶體。  
  
## <a name="rule-c"></a>規則 C  
 IF MyClass.MyProperty==2  
  
 然後\<執行某個動作...\>  
  
 當物件的屬性值與條件相符時，此規則便會執行動作。