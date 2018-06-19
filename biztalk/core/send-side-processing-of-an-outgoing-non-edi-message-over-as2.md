---
title: 外寄非 EDI 訊息處理透過 AS2 傳送端 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3f19b7df-fe6d-4105-8a44-3d6db0bba451
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 666f441b17049b0f4c302dbfdc89367aed8126a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271846"
---
# <a name="send-side-processing-of-an-outgoing-non-edi-message-over-as2"></a>透過 AS2 從傳送端處理外寄非 EDI 訊息
隨附於 AS2 管線[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以用來處理透過 AS2 傳輸的 EDI 訊息或非 EDI 訊息。 這兩種不同的內容類型會使用不同的管線。 您會使用 AS2EdiSend 管線來處理透過 AS2 外寄的 EDI 訊息，而使用 AS2Receive 管線接收關聯的 MDN (如果有啟用)。 您會使用 AS2Send 管線來處理透過 AS2 外寄的非 EDI 訊息，而使用 AS2Receive 管線接收關聯的 MDN (如果有啟用)。 非 EDI 訊息可以是任何二進位內容。  
  
 AS2Send 管線會組合非 EDI 內容並解譯 AS2 訊息。 AS2Receive 接收管線則會解譯 MDN 回應。 您可以將這些管線包含在 HTTP 雙向請求-回應傳送埠 (適用同步的 MDN) 中，或是單向的 HTTP 傳送埠和單向的 HTTP 接收埠 (適用非同步的 MDN) 中。  
  
 為了透過 AS2 傳送 EDI 交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會執行下列步驟：  
  
-   處理要傳送的非 EDI 內容  
  
-   傳送 AS2 訊息  
  
-   接收傳回的 MDN  
  
## <a name="processing-the-non-edi-payload-for-sending"></a>處理要傳送的非 EDI 內容  
 在建立 AS2 訊息之前，傳送埠必須使用適當的篩選條件運算式訂閱訊息，藉此選取非 EDI 內容。 根據 MDN 將會是同步或非同步而定，您可以使用雙向傳送埠或單向傳送埠。 接著 AS2Send 管線會將非 EDI 內容處理為 AS2 訊息。  
  
## <a name="sending-the-as2-message"></a>傳送 AS2 訊息  
 AS2 傳送管線中的 AS2 編碼器會先執行協議解析，以判斷要用來處理外寄訊息的協議屬性。 如需詳細資訊，請參閱[外寄 AS2 訊息的協議解析](../core/agreement-resolution-for-outgoing-as2-messages.md)。  
  
 AS2 編碼器會建置傳送 AS2 訊息時所需的一組 HTTP 標頭。 它會將這些標頭加入至 `HTTP.UserHttpHeaders` 內容屬性 (標頭值的單一字串)。 AS2 編碼器會建置下列位在 HTTP.UserHttpHeaders 中的 AS2 標頭。 這些標頭一定會出現在 AS2 訊息中。  
  
-   AS2-To  
  
-   AS2-From  
  
-   AS2-Version  
  
-   MessageID  
  
-   OriginalMessageID (僅適用於 MDN)  
  
 如果**要求 MDN**屬性已核取，則管線會將配置通知給、 回條傳遞選項，以及簽章-回條-MICalg AS2 標頭中的訊息中對應的屬性和它的值如果設定以 「 pcks7 簽章 」 之簽署回條通訊協定 AS2 標頭**要求簽署的 MDN**會檢查屬性。  
  
 如果 `HTTP.UserHttpHeaders` 內容屬性不存在，AS2 編碼器會建立它。 如果 `HTTP.UserHttpHeaders` 已存在，AS2 編碼器就會使用它，而不重新建立它。 如果您建立 `HTTP.UserHttpHeaders`，將標頭寫入其中，然後將此內容屬性寫入訊息內容中，AS2 編碼器就會使用這些標頭，而且這些標頭的優先順序高於其他來源的標頭。 唯一的例外是 AS2-From 標頭，它一定是取自協議屬性。  
  
 如果 AS2 標頭不在 `HTTP.UserHttpHeaders` 中，AS2 編碼器會從單一內容屬性加入它。 這表示，您可以藉由將 AS2 標頭升級或寫入訊息內容中，加入 AS2 標頭 (如果 AS2 標頭不在 `HTTP.UserHttpHeaders` 中)。 如果 AS2 標頭不在 `HTTP.UserHttpHeaders` 中，也不是內容中的屬性，AS2 編碼器就會從協議屬性將它加入至 `HTTP.UserHttpHeaders` 中。  
  
 在 AS2 編碼器建置 `HTTP.UserHttpHeaders` 屬性中的標頭之後，它會將此屬性加入訊息的內容中。 HTTP 配接器會收取 `HTTP.UserHttpHeaders`，並將 `HTTP.UserHttpHeaders` 中的標頭值附加到訊息的前面。  
  
> [!NOTE]
>  AS2 傳輸只適用於 HTTP 配接器。 不過，如果您手動設定適當的內容屬性，也可以使用 FILE 配接器傳輸 AS2 訊息。 如需詳細資訊，請參閱[透過 FILE 傳送埠傳送 AS2 訊息](../core/sending-an-as2-message-over-a-file-send-port.md)。  
  
## <a name="processing-the-returned-mdn"></a>處理傳回的 MDN  
 如果 MDN 已啟用，與雙向傳送埠相關聯的接收管線就會從接收 AS2 訊息的合作對象接收 MDN。  
  
> [!NOTE]
>  如需 AS2 傳送管線對內送 Mdn 執行處理的詳細資訊，請參閱[傳送外寄 MDN](../core/sending-an-outgoing-mdn.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 傳送 AS2 訊息的方式](../core/how-biztalk-server-sends-as2-messages.md)