---
title: "索引運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Max Occurs property
- Index functoids, about Index functoids
- Index functoids
ms.assetid: 0c8ba427-881c-4b1f-92b9-61992d2a29df
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a22881e7694fee872b7820b8b99157ef2cf20170
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="index-functoid"></a>索引運算質
**索引**運算質可讓您從中選取一系列的記錄中的特定記錄資訊。 每個**索引**運算質均收集單一欄位的資訊。  
  
 輸入檔案中的特定記錄通常會發生多次。 例如，在氣象報告中， **DailySummary**項目可能會發生多次。 **DailySummary**項目可能包含溫度、 氣壓以及風速等屬性。 下列程式碼為氣象報告範例。  
  
```  
<ns0:WeatherReport xmlns:ns0="http://IndexFunctoid.WeatherReport">  
    <DailySummary Pressure="80" Windspeed="10" Temperature="20" />  
    <DailySummary Pressure="78" Windspeed="20" Temperature="23" />  
    <DailySummary Pressure="77" Windspeed="16" Temperature="24" />  
</ns0:WeatherReport>  
```  
  
 基礎結構描述， **Max Occurs**屬性**DailySummary**記錄會設定為 [unbounded]，表示週期性或迴圈記錄。 「BizTalk 對應工具」會將此記錄編譯為迴圈。  
  
 假設您想要收集氣象資訊的前兩個**DailySummary**氣象報告的記錄。 在 BizTalk 對應工具中，每個屬性**DailySummary**內送來源結構描述的記錄可以連線到**索引**運算質。 接著，每個**索引**運算質可以指定**DailySummary**要向資訊記錄： 第一個或第二個。 **索引**運算質就可以連接至目的結構描述的適當欄位。  
  
 下圖顯示**索引**以此方式使用的運算質。  
  
 ![](../core/media/ebiz-prog-map-index.gif "ebiz_prog_map_index")  
索引運算質範例  
  
 若要取得的第一天的每日摘要資訊，請上限設定三個**索引**運算質的索引值設為 1。 若要取得第二天的每日摘要資訊，較低設定三個**索引**運算質的索引值設為 2。  
  
 **索引**運算質使用**設定\<運算質\>運算質**對話方塊，即可設定其輸入的參數。 第一個輸入參數會識別在來源結構描述中迴圈記錄內的欄位。 第二個及後續的輸入參數會指定特定的記錄。 您可以指定多個索引值以選取巢狀重複結構中的記錄。 最內層結構的索引值為第二個參數。 下一個最外層結構的索引值為第三個參數等等。 例如，假設上述**DailySummary**內的資料已**WeeklyData**記錄。 擷取**不足的壓力**從第一個**DailySummary**中第二個**WeeklyData**、 第二個參數會是 1 和第三個參數為 2。  
  
 請注意，此範例假設**不足的壓力**欄位不會重複。 如果欄位重複，索引會關閉 — 計數會從**不足的壓力** 欄位中，而非**每日摘要**。  
  
> [!NOTE]
>  雖然索引順序輸入參數通常為常數，但可以使用來源結構描述中節點的連結。 若此連結來自迴圈記錄，且不是第一個輸入參數的父項，則索引順序輸入值來自輸入執行個體訊息中節點的第一個執行個體。  
  
> [!NOTE]
>  索引順序輸入值一律與來源文件中的目前內容相關。  
  
> [!IMPORTANT]
>  **索引**運算質必須為許多索引值，與欄位層級到根節點底下的第一個層級的父節點。 例如，在多個氣象報告執行個體訊息中，需要兩個索引值。 在單一氣象報告執行個體訊息中，僅需要一個索引值。 若未設定必要的索引值數目**索引**運算質建立根據符合第一個輸入的參數的來源執行個體訊息中的第一個節點的輸出**索引**運算質。  
  
## <a name="see-also"></a>請參閱  
 [如何新增索引運算質至對應](../core/how-to-add-index-functoids-to-a-map.md)   
 [進階運算質](../core/advanced-functoids.md)   
 [反覆項目運算質](../core/iteration-functoid.md)   
 [記錄計數運算質](../core/record-count-functoid.md)