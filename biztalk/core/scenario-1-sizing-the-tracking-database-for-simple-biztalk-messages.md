---
title: 案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: 5b8fed48-d9c9-4d1f-a320-d3e23b8b1ec9
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13faa8f149c70d7647ff9f2dbf1d3718472f4a0b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006719"
---
# <a name="scenario-1-sizing-the-tracking-database--for-simple-biztalk-messages"></a>實例 1：針對範例 BizTalk 訊息調整追蹤資料庫的大小
在下圖中，簡易 BizTalk Server 訊息不需經過任何訊息轉換即可在 BizTalk Server 傳入和傳出。  
  
 ![簡易 BizTalk Server 訊息&#45;不需轉換](../core/media/simple-bts-message.gif "Simple_BTS_Message")  
  
 **簡單的 BizTalk Server 訊息-不需轉換**  
  
 在您套用前一節的公式之前，需要收集此實例的一些相關事實。 在此範例中，將使用下列項目：  
  
- 訊息大小為 5K。  
  
- 不會升級屬性。  
  
- 您一年內所接收的訊息數目為三百五十萬。  
  
- 開啟所有事件的追蹤。 在此實例中有 4 個事件。 這些事件為：  
  
  -   收到訊息 M0  
  
  -   接收埠輸出訊息 M1  
  
  -   傳輸管線收到訊息 M1  
  
  -   傳送管線輸出訊息 M2  
  
- 在此實例中建立了兩個額外的訊息。 訊息 M0 是內送訊息，因此並不是由 BizTalk Server 所建立。 訊息 M1 是來自接收埠的輸出訊息，而 M2 是來自傳輸埠的輸出訊息。 M1 和 M2 是由 BizTalk Server 所建立。  
  
  將此資訊套用至公式會產生下列結果：  
  
```  
[(5*252 bytes) + (10*182 bytes) + (0*5(40 bytes + 0) * 3,500,000]/1024/1024  
[(1620 + 1820 + 0) * 3,500,000]/1024/1024 = 10280.61 MB ~ 10.04 GB per year  
```  
  
## <a name="messages-with-a-single-promoted-property"></a>含有單一升級屬性的訊息  
 請再看一次這個範例，並新增另一個事實到實例中。 您想要從原始訊息升級單一欄位，欄位大小約為 10 個位元組。 升級的欄位大小上限為 256 個字元，或大約 256 個位元組 (若字元是 Unicode，則為 512 個位元組)。  
  
 新增此額外的事實後，方程式現在看起來如下所示：  
  
```  
[(2*150 bytes) + (4*230 bytes) + (1*2(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(300 + 920 + 124) * 3,500,000]/1024/1024 = 4486 MB ~ 4.38 GB per year  
```  
  
 若您要升級 10 個位元組大小的額外欄位，方程式將如下所示：  
  
```  
[(2*150 bytes) + (4*230 bytes) + ((1*2*(52 bytes + 10 bytes) + (1*2*(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(300 + 920 + 248) * 3,500,000]/1024/1024 = 4899 MB ~ 4.78 GB per year  
```  
  
 如您所見，若您在此實例中升級一個 10 個位元組的屬性，將會使 BizTalk 追蹤資料庫每年增加 333.79 MB 到 0.33 GB 的大小。  
  
 若升級兩個 10 個位元組的屬性，將會使 BizTalk 追蹤資料庫每年增加 667.58 MB 到 0.65 GB 的額外空間大小。  
  
## <a name="messages-with-message-body-tracking-activated"></a>已啟動訊息內文追蹤的訊息  
 在此範例中，假設我們正計劃啟動訊息內文追蹤。 這將需要新增第二個訊息追蹤方程式，如上一節所示。 此範例的方程式看起來將如下所示：  
  
```  
[3,500,000 * 4 * 5KB]/1024 = 68359.375 MB ~ 66.75 GB per year  
  
```  
  
 在新增兩個方程式的結果後，可以預估 BizTalk 追蹤資料庫每年將成長大約 54.48 GB 到 54.88 GB。  
  
## <a name="see-also"></a>另請參閱  
 [使用訊息變數調整追蹤資料庫的大小](../core/using-message-variables-to-size-the-tracking-database.md)   
 [追蹤訊息內文追蹤資料庫設定大小](../core/sizing-the-tracking-database-to-track-message-bodies.md)   
 [案例 2： 在協調流程中的訊息調整追蹤資料庫](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)   
 [案例 4： 針對所有訊息調整追蹤資料庫](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)   
 [案例 3：為外送到通訊群組清單的訊息調整追蹤資料庫的大小](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)