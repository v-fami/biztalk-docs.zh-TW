---
title: "詞彙 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, vocabularies
- vocabularies, about vocabularies
- vocabularies
- Business Rules Engine, vocabularies
ms.assetid: 591673a0-2c4d-41ca-9997-b363c086dd66
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9e20dfead51d54822d3316c8819d04a259cfa83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="vocabularies"></a>詞彙
用以定義規則條件與動作的詞彙通常是以網域或業界特定的術語來表達。 例如，電子郵件使用者會根據「寄件者」訊息與「下列日期之後」訊息來撰寫規則，而保險商業分析師會根據「風險因素」與「保險金額」來撰寫規則。  
  
 在此網域特定術語下的是技術成品 (物件、資料庫表格，以及 XML 文件)，可實作規則條件與規則動作。 Vocabulariesare 設計來橋接商業語意與實作之間的差距。  
  
 例如，核准狀態的資料繫結有可能指向某個資料庫中某資料列內的某資料欄，以 SQL 查詢表示。 您不需在規則中插入此種的複雜表示法，可改為以「狀態」的易記名稱來建立詞彙定義，並與該資料繫結產生關聯。 之後您便可在任何數目的規則中包括「狀態」，而規則引擎可從表格中擷取對應資料。  
  
 A*詞彙*是定義規則條件和動作中所用之事實的易記名稱所組成的集合。 詞彙定義讓規則更易於閱讀、瞭解，並可讓特定商業領域的人共用。  
  
 您可以使用「商務規則編輯器」，定義放置於共用規則存放區中的詞彙。 詞彙也可供負責將撰寫規則以整合至新的或現有應用程式的工具開發人員所使用。  
  
 在您可以使用詞彙之前，它必須先加上版本的戳記，並發佈於規則存放區中。 這可保證詞彙中的定義不會變更，並保留參考的完整性。 這表示任何使用該特定版本之詞彙的原則，不會因基礎詞彙變更而意外失敗。  
  
## <a name="see-also"></a>另請參閱  
 [商務規則引擎](../core/business-rules-engine.md)