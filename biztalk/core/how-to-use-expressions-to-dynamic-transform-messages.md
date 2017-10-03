---
title: "如何使用運算式動態地轉換訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48387d97-9312-4df5-b614-727ea9035bf8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b9d16c38fefb4e2732bd05f7c3489acaa8ca645
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-expressions-to-dynamic-transform-messages"></a>如何使用運算式動態地轉換訊息
您可使用運算式在協調流程中動態地轉換訊息。 XLANG 公開可以呼叫內的轉換方法**訊息指派**圖形內**建構訊息**圖形。 這是相同的方法時，會呼叫**轉換**圖形會使用，但可讓您以程式設計方式轉換訊息使用您指定在協調流程中的對應。 當您進行類型不可知的訊息處理時，這點便會相當有用。 例如，如果您有商務程序需要從一系列對應中選擇，以便根據接收之輸入訊息所提供的參數轉換輸入訊息，可使用「運算式」圖形中的轉換方法來進行，而且同時可維持整體商務程序的完整。  
  
## <a name="transforming-messages"></a>轉換訊息  
 您可以使用下列範例程式碼，以程式設計方式轉換中的訊息**訊息指派**圖形：  
  
```  
MyMapType = typeof(MyMapName);  
transform(MyOutputMsg) = MyMapType(MyInputMsg);  
```  
  
 在此範例中，MyMapType 宣告為類型的變數**System.Type**協調流程中。 MyMapName 是已經在您的 BizTalk 專案中建立之對應的名稱。 如果您要參考個別 BizTalk 組件中的對應，您便需要在 BizTalk 專案中參考該組件。 MyInputMsg 是來源訊息，而 MyOutputMsg 則是目的訊息。 如果您的對應使用多個來源訊息，您就可以使用下列範例程式碼來轉換這些訊息：  
  
```  
MyMapType = typeof(MyMapName);  
transform(MyOutputMsg) = MyMapType(MyInputMsg1, MyInputMsg2);  
```  
  
> [!NOTE]
>  如果您有多個來源訊息，則必須根據在對應中指示的輸入訊息部分編號，將訊息分別依序放置在運算式中。  
  
> [!IMPORTANT]
>  當動態地轉換「運算式」圖形中的訊息時，建議您在使用者程式碼中寫入快取，以便快取已編譯的對應，然後使用「運算式」圖形中的快取，在執行訊息轉換之前擷取對應。 如果您沒有快取對應，便有可能看到 Common Language Runtime (CLR) 記憶體顯著地成長。 動態對應需要 .NET Runtime 執行程式碼存取檢查，讓 .NET Evidence 物件放置在每個轉換的「大型物件堆積」，而且在協調流程完成之前，都不會處置這個物件。 因此，當有許多這些類型的轉換同時發生時，您便可能會看到記憶體使用的顯著增加，如此也會導致記憶體不足的例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程圖形](../core/orchestration-shapes.md)   
 [使用 BizTalk 對應工具建立對應](../core/creating-maps-using-biztalk-mapper.md)