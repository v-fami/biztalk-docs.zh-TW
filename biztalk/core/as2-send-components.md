---
title: AS2 傳送元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35113732-fe32-4776-be25-971ec66c365c
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1dbee64dc2e3484e85e6d8e41ce31a77713ffec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231966"
---
# <a name="as2-send-components"></a>AS2 傳送元件
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用數種元件來傳送 AS2 訊息。  
  
## <a name="as2-send-pipelines"></a>AS2 傳送管線  
 大部分 AS2 傳送處理會在下列 AS2 傳送管線中執行。 這些管線安裝在`Microsoft.BizTalk.Edi.EdiIntPipelines.dll`\Program Files\Microsoft 20xx\Pipeline 的 BizTalk Server 元件中。  
  
> [!NOTE]
>  只有在 32 位元 BizTalk 主控件程序中，才支援 AS2 傳送管線。  
  
 **AS2EDISend 管線**  
  
 這個管線會透過 AS2 產生和傳送 EDI 訊息。 這個管線包含下列管線元件：  
  
-   EDI 組合器  
  
-   AS2 編碼器  
  
 此管線不會用來透過 AS2 產生和傳送 MDN，因為 MDN 不需要經過 EDI 組合器處理。 請使用 AS2SendPipeline 傳送 MDN。  
  
> [!NOTE]
>  不支援從協調流程執行 AS2EDISend 管線。  
  
 **AS2Send 管線**  
  
 這個管線會在訊息未以 EDI 編碼時，透過 AS2 傳送訊息。 此外還會透過 AS2 傳送 MDN。 這個管線包含下列管線元件：  
  
-   AS2 編碼器。  
  
 如果要透過 AS2 傳送的訊息不是 EDI 也不是 XML 訊息，則您可以建立自訂的 AS2Send 管線來處理這些訊息。 此管線必須擁有自訂的組合器，才能在以 EDIINT/AS2 編碼訊息之前，先在 BizTalk Server 中將中繼 XML 轉換成其他格式。  
  
> [!NOTE]
>  不支援從協調流程執行 AS2Send 管線。  
  
## <a name="as2-send-pipeline-components"></a>AS2 傳送管線元件  
 AS2 傳送管線會使用下列管線元件。 這些元件安裝在`Microsoft.BizTalk.EdiInt.PipelineComponents.dll`\Program Files\Microsoft 20xx\Pipeline 的 BizTalk Server 元件中\\。  
  
 **EDI 組合器**  
  
 在 EDIINT 傳送管線中，EDI 組合器會將 EDI 交換序列化。  
  
 **AS2 編碼器**  
  
 AS2 編碼器包含在 AS2 傳送管線的編碼階段中。 它會使用 BizTalk S/MIME 管線元件為 AS2 和 MDN 訊息提供 S/MIME 編碼功能。 AS2 編碼器會執行下列工作：  
  
-   套用 AS2/HTTP 標頭  
  
-   簽署外寄訊息 (如果已啟用)  
  
-   加密外寄訊息 (如果已啟用) (針對 EDI/AS2 而非 MDN)  
  
-   壓縮訊息 (如果已啟用) (針對 EDI/AS2 而非 MDN)  
  
-   以電傳格式儲存內容，如果**為輸出的解碼 AS2 訊息啟用 NRR**屬性已選取，並以電傳格式儲存訊息，如果**為輸出的編碼 AS2 訊息啟用 NRR**選取屬性  
  
-   計算 MIC 值並將它儲存到資料存放區  
  
-   在不可否認性的接收資料庫中更新記錄並使其相互關聯  
  
-   針對 MDN 訊息，做為通過管線使用，路由 AS2Receive 接收管線中的 AS2 解碼器產生的 MDN。 如果組態設定需要，AS2 編碼器將簽署 MDN。  
  
    > [!NOTE]
    >  AS2 訊息使用八位元編碼， Base64 編碼只適用於 AS2 訊息和 MDN 中的簽章。  
  
## <a name="http-adapter"></a>HTTP 配接器  
 EDIINT AS2 處理所使用的傳送埠會使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 配接器。 HTTP 配接器設定同時適用於單向和請求-回應傳輸。  
  
## <a name="non-repudiation-database"></a>不可否認性的資料庫  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用不可否認性的資料庫 (BizTalkDTADb 資料庫的 EdiMessageContent 資料表) 來執行下列動作：  
  
> [!NOTE]
>  只有在已核取其中一個不可否認性的儲存區協議屬性時，BizTalkDTADb 資料庫中才有 EdiMessageContent 資料表。  
  
-   為已簽署的 MDN 提供不可否認性的線索  
  
-   使輸出訊息與其內送 MDN 相互關聯  
  
-   儲存各種狀態變更的訊息  
  
-   使錯誤碼與 HTTP 回應和 MDN 產生關聯  
  
-   根據篩選準則顯示記錄  
  
-   封存已標示的記錄  
  
> [!IMPORTANT]
>  為了確保不可否認性資料庫中所儲存訊息的真實性和完整性，資料庫中將儲存的所有訊息，包括原始 AS2 訊息和 MDN，都應使用數位簽章。 如需詳細資訊，請參閱的 9.1 節 < [RFC 1430、 」 以 MIME 為基礎安全端對端商務資料交換使用 HTTP，Applicability Statement 2 (AS2) >](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212))。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 傳送 AS2 訊息的方式](../core/how-biztalk-server-sends-as2-messages.md)