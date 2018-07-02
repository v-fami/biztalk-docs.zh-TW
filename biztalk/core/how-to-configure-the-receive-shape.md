---
title: 如何設定 「 接收 」 圖形 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- filter expressions, Receive shape [Orchestration Designer]
- Receive shape [Orchestration Designer], about Receive shape
- configuring [Orchestration Designer], Receive shapes
- Receive shape [Orchestration Designer]
- Receive shape [Orchestration Designer], filter expressions
ms.assetid: 15aadee4-fa05-4edd-a191-e4d191c1ea22
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60d2a0913e6921b5868a16c58c7ed2c7ae3d46e4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989703"
---
# <a name="how-to-configure-the-receive-shape"></a>如何設定接收圖形
![](../core/media/ebiz-orch-receive.gif "ebiz_orch_receive")  
接收圖形  

 A**接收**圖形可以用來啟動協調流程。 如果您設定**Activate**屬性設 **，則為 True**，執行階段引擎會測試內送訊息以查看它是否屬於正確的類型以及如果套用的篩選，是否在篩選條件運算式滿足。 如果符合接收訊息的準則，在執行階段引擎會建立並執行新的協調流程執行個體，而**接收**圖形接收訊息。  

> [!NOTE]
>  如果**Activate**的 「 接收 」 圖形的屬性設定為 True，**接收**必須在協調流程中的第一個動作。  

> [!NOTE]
>  如果**Activate**屬性設定為 False，所有**接收**圖形，您的協調流程必須由呼叫另一個協調流程才能執行。  

> [!NOTE]
>  如果您將放**接收**範圍內的圖形**Activate**屬性設定為 **，則為 True**，而不需要變更，然後將.NET 類別變數新增至您的協調流程變數的**使用預設建構函式**屬性設**False**，則啟動接收陳述式會產生的 XLANG/S 程式碼，在範圍外，但仍會繼續在設計介面顯示為在範圍內。  

 每個協調流程必須至少一個**接收**圖形**Activate**屬性設定為**True**。  

 若您預期收到您已送出之訊息的間接或非同步回應 (不使用要求-回應連接埠)，則需要將訊息與目前正在執行的協調流程執行個體建立相互關聯，讓回應者能將回應送給正確的執行個體。 您可以套用初始化的相互關聯，如果您打算執行後續的相互關聯，內送訊息中的值設定為 「 接收 」 圖形或以下的相互關聯集合相互關聯使用先前初始化的相互關聯集。 如需詳細資訊，請參閱 <<c0> [ 協調流程中使用的相互關聯](../core/using-correlations-in-orchestrations.md)。  

### <a name="to-configure-a-receive-shape"></a>設定接收圖形  

1.  設定訊息和連接埠作業。  

    1.  在 [協調流程檢視] 視窗中，確認您的協調流程已經為接收的訊息類型，定義訊息和連接埠作業。  

         在 屬性 視窗中，選取 從接收訊息**訊息**屬性下拉式清單。  

    2.  在 屬性 視窗中，選取 連接埠作業，以接收來自訊息**作業**下拉式清單。  

         -或-  

         從接收連接器拖曳到**接收**圖形以將接收的訊息的連接埠通訊端。  

2.  指定**接收**圖形啟動協調流程。  

3.  在 [屬性] 視窗中，將 [啟動] 屬性設定為 True。  

    1.  在 [屬性] 視窗中，按一下**省略符號**(**...**) 按鈕來建立篩選器，以限制的訊息篩選條件運算式屬性的這個**接收**圖形接受。  

         -或-  

         以滑鼠右鍵按一下**接收**圖形，然後按一下**編輯篩選條件運算式**。  

    2.  **篩選條件運算式** 對話方塊隨即出現。 使用此對話方塊來建立一或多個篩選條件運算式。  

        > [!NOTE]
        >  必須定義訊息類型，並指派給**接收**圖形之前，您可以將篩選套用至它。  

4.  指定相互關聯集來限制的訊息**接收**圖形接受。  

    -   針對您想要遵循每個相互關聯集，檢查相互關聯集從下拉式清單上**沿用相互關聯集**屬性。  

    -   用於每個相互關聯集您想要初始化，請檢查相互關聯集從下拉式清單上**初始相互關聯集**屬性。  

## <a name="filter-expression-grid-control"></a>篩選條件運算式格線控制項  
 您可以使用此格線控制項定義構成運算式的述詞，以建置篩選條件運算式。 您可以在格線的儲存格中新增、編輯和刪除述詞。 此格線控制項有四個資料行： 屬性、 運算子、 值和群組。  

- **屬性。** 您可以輸入屬性參考，或從儲存格的下拉式清單中選取一個屬性。 該清單包含內送訊息的屬性。  

- **運算子。** 您可以在此儲存格輸入運算子，或從下拉式清單中選取運算子。 可能的選項為：  


  | 運算元 |           意義           |
  |---------|-----------------------------|
  |   ==    |         等於         |
  |   !=    |       不等於       |
  |    <    |        小於         |
  |   \<=   |  小於或等於   |
  |    >    |       大於       |
  |   \>=   | 大於或等於 |
  | Exists  |           Exists            |


- **值。** 中的儲存格**值**資料行可以保存您在中輸入任何常數： 字串常值、 整數常值或 null。  

  > [!NOTE]
  >  如果所選取屬性的類型為字串，該值必須在引號中。 例如，SMTP.From = "MyServer"。  

- **群組。** 您可以使用此欄來控制述詞群組。 篩選條件運算式一律以 DNF (Disjunctive Normal Form) 來表示，以便自動決定群組。 [AND] 表示將述詞和其後的述詞群組起來，而 [OR] 表示述詞和下一列的述詞是分開的。 當述詞組成群組時，格線控制項左邊會出現灰色中括弧。 述詞無法組成巢狀群組。 若未在此儲存格中指定值，儲存格的預設值為 AND。  

  例如，您可能建立如下的運算式：  

  `MSMQ.MsgID = 1`  

  依照這個篩選條件，傳送埠群組將只能訂閱 MSMQ 訊息識別碼為 1 的訊息。  

  您可以建立額外的運算式，並指定這些運算式與其他運算式之間有 AND 或 OR 關係，例如：  

  `MSMQ.MsgID = 1 OR`  

  `SMTP.From = "MyServer"`  

  在此例中，傳送埠群組將會訂閱 MSMQ 訊息識別碼為 1 的或從名為 MyServer 的 SMTP 伺服器所傳送的所有訊息。  

## <a name="hint-label"></a>提示標籤  
 此欄位會指引使用者。 標籤文字會隨著包含作用中儲存格的資料行改變。 此文字會顯示資料行名稱，後面接著引導文字，如下所示：  

-   **屬性。** 請從清單選取內送訊息上的屬性。  

-   **運算子。** 選取運算子，以進行 [屬性] 與 [值] 的比較。  

-   **值。** 從清單選取訊息屬性，或輸入常值。  

-   **群組。** 指定此列如何與下一列群組在一起。 'AND' 將會聯結資料列，而 'OR' 會分開它們。  

## <a name="move-up-button"></a>上移按鈕  
 按一下此按鈕，將選取的列上移 (第一次，即可選取資料列*向右箭號*(**>)** ，格線控制項左邊的按鈕。)  

## <a name="move-down-button"></a>下移按鈕  
 按一下此按鈕，將選取的列下移 (第一次，即可選取資料列*向右箭號*(**>)** ，格線控制項左邊的按鈕。)  

## <a name="filter-expression-created-field"></a>建立的篩選條件運算式欄位  
 這個唯讀文字方塊會在您建立運算式時顯示它。  

## <a name="in-this-section"></a>本節內容  
 [搭配使用篩選與接收訊息圖形](../core/using-filters-with-the-receive-message-shape.md)