---
title: "如何開發詞彙 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, vocabularies
- vocabularies, business rules
- business rules, vocabularies
- vocabularies, creating
ms.assetid: 5c16eb98-2257-44f2-8a29-899e02f7e556
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2644cc938cbe5e42f4e124453d863741755d965d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-develop-vocabularies"></a>如何開發詞彙
規則條件和動作是以可能有冗長且難於閱讀的繫結資訊之來源為基礎，這些資訊幾乎或根本無法告訴使用者它們指的是什麼。 「商業規則架構」可讓您建立詞彙以簡化規則的開發，即透過提供使用者直覺和網域特定的詞彙，讓使用者可以聯想到規則條件和動作。  
  
 您可以指出要使用的資料來源、建立新詞彙，以及新增詞彙定義。 您可以將自己的詞彙版本儲存至規則存放區，而且當它已完整時，您可以將它發佈以提供使用者定義正確且不變並繫結至資料參考的詞彙集。  
  
 若將來需要變更詞彙，可以直接建立新版本的詞彙以反映變更。  
  
> [!CAUTION]
>  當新版本的詞彙已建立時，從舊版本建立的規則仍然會指向舊版本。  
  
### <a name="to-create-a-vocabulary"></a>建立詞彙  
  
1.  在 事實總管 視窗中，按一下**詞彙** 索引標籤。  
  
2.  以滑鼠右鍵按一下**詞彙**資料夾，然後再按一下**新增詞彙**。  
  
     新**詞彙**資料夾之下**詞彙**資料夾。  
  
3.  按一下新**詞彙**資料夾，然後再編輯 [屬性] 視窗中的名稱。  
  
    > [!NOTE]
    >  您必須儲存所有項目 (定義的所有版本) 後，才能重新命名詞彙或原則。