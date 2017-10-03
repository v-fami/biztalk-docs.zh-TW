---
title: "如何建立原則和規則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, business rules
- policies, rules
- policies, predicates
- business rules, creating
- creating, policies
- policies, logical operators
- policies, examples
- policies, default actions
- policies
- policies, arguments
- policies, creating
ms.assetid: 59f06a67-edde-443b-9fbb-55ec4429837a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52fb3d835b39a4059fc7a4a1644d7653257ea3dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-policies-and-rules"></a>如何建立原則和規則
您可以使用邏輯群組的邏輯運算子的條件建立規則 (**AND**， **OR**，和**不**) 套用到述詞 （內建或使用者定義函式或運算子），不接受引數 （內建或使用者定義的事實參考）。 您也可以以滑鼠右鍵按一下**條件**或邏輯運算子，從內容功能表中選取邏輯運算子或內建述詞。  
  
 您可以定義若規則條件評估為要執行的動作 （內建或使用者定義函式） **true**。  
  
> [!NOTE]
>  若在一個規則中包含一個以上的述詞，則所有述詞必須顯示為邏輯運算子的引數。 (最上層可以是屬於布林類型的單一 .NET 成員、資料庫資料行或 XML 欄位/屬性。)  
  
### <a name="to-create-a-policy"></a>若要建立原則  
  
1.  在 原則總管 窗格中，以滑鼠右鍵按一下**原則**，然後按一下 **新增原則**。  
  
     新的資料夾， **[policy1]**，下方會建立**原則**。 依照預設，會為您建立版本 1 的新原則。  
  
2.  按一下**[policy1]**。  
  
3.  在 [名稱] 屬性窗格中輸入名稱。  
  
### <a name="to-add-a-rule-to-a-policy-version"></a>新增規則到原則版本  
  
-   在 [原則總管] 窗格中，展開 [**原則**]，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後選取**新增規則**。  
  
### <a name="to-add-a-logical-operator-to-a-rule-condition"></a>新增邏輯運算子到規則條件  
  
-   在 [規則定義] 視窗中，以滑鼠右鍵按一下**條件**，然後按一下其中一個**新增邏輯 AND**，**新增邏輯 OR**，或**新增邏輯 NOT**.  
  
### <a name="to-add-a-built-in-predicate-to-a-rule-condition-or-logical-operator"></a>新增內建述詞到規則條件或邏輯運算子  
  
1.  在 [事實總管] 視窗中，按一下**詞彙**索引標籤，然後再按一下**述詞**資料夾。  
  
2.  展開述詞詞彙的已發佈版本，然後按一下所需的述詞。  
  
3.  將述詞拖曳到邏輯運算子，或拖曳至**條件**如果您的規則將會包含一個述詞。  
  
    > [!NOTE]
    >  您也可以加入述詞直接從資料來源，前提是資料元素做為述詞 (評估為**true**或**false**)。  
  
### <a name="to-add-a-built-in-action-to-a-rule"></a>新增內建動作到規則  
  
1.  在 [事實總管] 視窗中，按一下**詞彙**索引標籤，然後再按一下**函式**資料夾。  
  
2.  展開函式詞彙的已發佈版本，然後按一下所需的函式。  
  
3.  拖曳函式到**動作**。 您也可以以滑鼠右鍵按一下**動作**，然後從內容功能表選取內建動作。  
  
### <a name="to-add-an-argument-to-a-condition-or-action"></a>新增引數到條件或動作  
  
1.  在 [事實總管] 視窗中，按一下**詞彙**索引標籤，然後再按一下 [詞彙] 資料夾。  
  
2.  展開詞彙的已發佈版本，然後按一下所需的詞彙。 該詞彙必須是述詞或函式所預期的類型。  
  
3.  將詞彙拖曳到條件中的述詞引數或動作中的函式引數。  
  
    > [!NOTE]
    >  您也可以從資料來源直接新增引數，或者在 XML 中，可以在選取欄位時在屬性中指定欄位類型，但必須與資料本身相容，且資料項目必須是述詞或動作所預期的類型。 若要直接從資料來源新增引數，在 [事實總管] 視窗中，按一下適當的索引標籤，巡覽至您所需的項目，然後拖曳到述詞引數或函式引數。  
  
    > [!NOTE]
    >  按一下引數並輸入想要的常數值，即可直接新增常數值到引數。