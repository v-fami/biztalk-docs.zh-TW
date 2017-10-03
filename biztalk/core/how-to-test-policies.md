---
title: "如何測試原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, policies
- Business Rule Composer, testing
- Business Rule Composer, policies
- testing, Business Rule Composer
- policies, testing
ms.assetid: 122dee26-d1f1-49a6-a6d5-a9d3d861a66b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7a0f8c0d63d14d5a529039a6e1c8af5b363cc9c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-test-policies"></a>如何測試原則
若要測試原則，您需要可在其上執行規則的事實。 您可以透過指定 XML 文件中的值或指定您要在原則測試器中指向的資料庫資料表，以新增事實，或是使用事實建立者以提供 .NET 物件陣列給引擎作為事實。 如需詳細資訊，請參閱[建立事實建立者](../core/how-to-create-a-fact-creator.md)。  
  
### <a name="to-test-a-policy-in-the-business-rule-composer"></a>在商務規則編輯器中測試原則  
  
1.  在 [原則總管] 視窗中，按一下您要測試的原則版本。  
  
2.  按一下**測試原則**功能表列上的按鈕 （綠色箭頭）。  
  
     頂端窗格會顯示原則規則參考的事實類型。  
  
3.  若要新增事實執行個體，請按一下**XML 文件**或**資料庫資料表**事實類型，然後再按**新增執行個體**。  
  
4.  如果您想要移除事實執行個體，按一下對應的事實類型，然後按一下**移除執行個體**。  
  
5.  如果您想要新增您所撰寫的事實建立者，請按一下**新增**事實建立者窗格中。  
  
6.  按一下**測試**。  
  
     原則測試追蹤輸出會顯示在測試輸出視窗中。  
  
7.  在輸出視窗中，使用滑鼠右鍵按一下以儲存、清除、選取或複製輸出文字。  
  
     ![](../core/media/ebiz-testpolicy.gif "ebiz_testpolicy")  
選取事實以測試原則