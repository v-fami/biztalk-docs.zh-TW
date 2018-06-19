---
title: 攔截器組態運算式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2695f509-fece-40b8-aa00-fa3c0c0f19c5
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 927afa60dc65fb014f0d44305db5e7f6e78b803b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973628"
---
# <a name="interceptor-configuration-expressions"></a>攔截器組態運算式
BAM 攔截器組態檔使用篩選條件運算式識別活動，並且使用資料運算式建構資料項目，用於儲存、做為相互關聯識別碼或接續 Token 使用，或是用於類似的目的。 無論目的為何，個別運算式是透過 `expression` 項目在攔截器組態檔中識別，並且包含一或多項使用 Reverse Polish Notation (亦稱為 Postfix 標記法) 的作業。  
  
## <a name="about-reverse-polish-notation"></a>關於 Reverse Polish Notation  
 在 Reverse Polish Notation (RPN) 中，運算元優先於運算子，因此不需要使用括號做為優先順序運算子。 堆疊是用來保留值和所有作業，包括將值推入堆疊、顯示 (移除) 來自堆疊的值，或是執行推入和顯示的組合動作來完成作業。  
  
 例如，如果您要評估運算式  
  
 `5 + (10 - 2)`  
  
 將此運算式轉換成同等的 RPN 會得出  
  
 `5 10 2 - +`  
  
 評估結果如下：  
  
|輸入|作業|堆疊|  
|-----------|---------------|-----------|  
|5|發送|5|  
|10|發送|5, 10|  
|2|發送|5, 10, 2|  
|-|減|5, 8|  
|+|加入|13|  
  
 假如 RPN 系統支援字串串連作業，那麼您也可以評估運算式  
  
 `"The quick brown " + "fox " + "jumped over the lazy " + "dog."`  
  
 將此運算式轉換成同等的 RPN 標記法會產生：  
  
 `"The quick brown " "fox " "jumped over the lazy " "dog" + + +`  
  
 評估結果如下：  
  
|輸入|作業|堆疊|  
|-----------|---------------|-----------|  
|"The quick brown"|發送|「 快速 brown"|  
|"fox"|發送|"The quick brown ", "fox "|  
|"jumped over the lazy"|發送|"The quick brown ", "fox ", "jumped over the lazy "|  
|"dog."|發送|"The quick brown ", "fox ", "jumped over the lazy ", "dog."|  
|+|串連|"The quick brown ", "fox ", "jumped over the lazy dog."|  
|+|串連|"The quick brown ", "fox jumped over the lazy dog."|  
|+|串連|"The quick brown fox jumped over the lazy dog."|  
  
 如您所見，任意數目的作業都可支援，包括比較、布林值作業，以及擷取適合本身所參與作業之值的自訂作業。 值會在堆疊上累積，並且根據個別作業推入和顯示。  
  
## <a name="reverse-polish-notation-in-the-interceptor-configuration-file"></a>攔截器組態檔中的 Reverse Polish Notation  
 您將撰寫兩種類型的運算式中攔截器組態檔： 篩選運算式和資料運算式。 篩選條件運算式要求 RPN 運算式的結果必須為布林值 `true` 或 `false`，而資料運算式則要求堆疊上只有單一值。  
  
### <a name="filter-expressions"></a>篩選條件運算式  
 篩選條件運算式會評估為布林值 `true` 或 `false`，並且用來識別 WF 或 WFC 應用程式中要追蹤的特定事件。 在 WF 應用程式中，通常會根據活動名稱或事件進行篩選。 例如，您可能想要選取**FoodAndDrinksPolicy**活動時，它**Closed**。 若使用 WF 作業，您就可以表示篩選條件，如下所示：  
  
 `(GetActivityName = "FoodAndDrinksPolicy") && (GetActivityEvent = "Closed")`  
  
 將此運算式轉換成 RPN 會產生：  
  
 `GetActivityName "FoodAndDrinksPolicy" == GetActivityEvent "Closed" == &&`  
  
 將此運算式轉換成適用攔截器組態檔的同等運算式，會得出下列 XML：  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 最後，此運算式會進行評估，如下所示假設**GetActivityName**傳回"DessertPolicy"和**GetActivityEvent**傳回"Closed":  
  
|輸入|作業|堆疊|  
|-----------|---------------|-----------|  
||GetActivityName|"DessertPolicy"|  
|"FoodAndDrinksPolicy"|常數|"DessertPolicy", "FoodAndDrinksPolicy"|  
|等於|比較|False|  
||GetActivityEvent|False, Closed|  
|"Closed"|常數|False, "Closed", "Closed"|  
|等於|比較|False, True|  
|And|邏輯 And|False|  
  
 留在堆疊上的值為布林值 `False`。 這樣將不會引發對應的事件。 如果活動名稱為 "FoodAndDrinksPolicy"，則可能會評估為布林值 `True`。  
  
 您可以使用 WCF 作業 `GetEndpointName` 和 `GetOperationName`，建構類似的運算式 (與類似的評估)。  
  
### <a name="data-expressions"></a>資料運算式  
 資料運算式是用來定義單一字串資料值。 資料運算式是未包含在 `Filter` 項目內的任何運算式。 資料運算式為 `OnEvent` 項目所使用，包括 `CorrelationID`、`ContinuationToken`、`Reference` 和 `Update`。  
  
 BAM 活動資料庫通常必須更新並且標示時間戳記。 例如，您可能想要擷取格式化為字串的事件開始的時間 」 開始： \<EventTime\>"。 若要執行這項操作，您必須使用類似下方的運算式 (其中 + 代表串連)：  
  
 `"Start: " + GetContextProperty(EventTime)`  
  
 將此運算式轉換成 RPN 會產生：  
  
 `"Start: " GetContextProperty(EventTime) +`  
  
 將此運算式轉換成適用攔截器組態檔中 `Update` 項目的同等運算式，會得出下列 XML：  
  
```  
<ic:Update DataItemName="NewOrderCreateTime" Type="NVARCHAR">  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Start:</ic:Argument>  
    </ic:Operation>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>EventTime</wf:Argument>  
    </wf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:Update>  
```  
  
 下表說明事件時間為 "12:00 PM" 時，如何解譯此運算式。  
  
|輸入|作業|堆疊|  
|-----------|---------------|-----------|  
|「 啟動:"|常數|「 啟動:"|  
|GetContextProperty(EventTime)|發送|「 啟動:"，"2006年-09-27T12:00:34.000Z"|  
|串連|串連|「 啟動： 2006年-09-27T12:00:34.000Z"|  
  
 更新命令所使用的值會是 「 啟動： 2006年-09-27T12:00:34.000Z"。  
  
> [!NOTE]
>  請不要在資料運算式中使用比較作業 "And" 或 "Equals"。 如果您使用比較作業的話，將在部署攔截器組態檔時收到錯誤。  
  
## <a name="in-this-section"></a>本節內容  
 [攔截器作業](../core/interceptor-operations.md)  
  
## <a name="see-also"></a>請參閱  
 [攔截器設定檔的結構](../core/structure-of-an-interceptor-configuration-file.md)