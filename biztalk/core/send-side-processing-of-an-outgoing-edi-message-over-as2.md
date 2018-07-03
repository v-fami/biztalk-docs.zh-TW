---
title: 傳送端處理透過 AS2 外寄 EDI 訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dfb63b22-6e2e-4d4f-b028-301c8d4d53b0
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c00aaae104bfe685945c7b20b62912970582381
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995415"
---
# <a name="send-side-processing-of-an-outgoing-edi-message-over-as2"></a>透過 AS2 外寄之 EDI 訊息的傳送端處理
透過 AS2 外寄之 EDI 訊息的傳送端處理的作業，包括透過 EDI 內容來傳送 AS2 訊息，以及接收 MDN 和 EDI 通知 (若已啟用)。  
  
 AS2EDISend 傳送管線會透過 HTTP/HTTPS，將組合的 EDI/AS2 訊息傳送至接收端的交易夥伴。 AS2EDIReceive 接收管線會接收為了回應 AS2 訊息而傳回的 MDN，以及為了回應 EDI 訊息而傳回的 EDI 通知。 這些管線每一個都會處理 AS2 訊息，並處理 AS2 訊息內的 EDI 內容。 您可以將這些管線包含在 HTTP 雙向請求-回應傳送埠中，或是單向的 HTTP 傳送埠和單向的 HTTP 接收埠中。  
  
 為了透過 AS2 傳送 EDI 交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會執行下列步驟：  
  
-   處理要傳送的 EDI 內容  
  
-   傳送 AS2 訊息  
  
-   接收傳回的 MDN  
  
-   接收傳回的 EDI 通知  
  
## <a name="processing-the-edi-payload-for-sending"></a>處理要傳送的 EDI 內容  
 建立 AS2 訊息之前，AS2EdiSend 管線必須先處理 EDI 交換。 如果已啟用輸出批次處理中, 所述，交易集將會批次處理[組合批次 EDI 交換](../core/assembling-a-batched-edi-interchange.md)。 「 EDI 組合器 」 會建立 EDI 交換中所述[EDI 組合器的運作方式](../core/how-the-edi-assembler-works.md)。  
  
## <a name="sending-the-as2-message"></a>傳送 AS2 訊息  
 AS2 傳送管線中的 AS2 編碼器會先執行協議解析，以判斷要用來處理外寄訊息的協議屬性。 如需詳細資訊，請參閱 <<c0> [ 外寄 AS2 訊息的協議解析](../core/agreement-resolution-for-outgoing-as2-messages.md)。  
  
 AS2 編碼器會建置傳送 AS2 訊息時所需的一組 HTTP 標頭。 它會將這些標頭加入至 `HTTP.UserHttpHeaders` 內容屬性 (標頭值的單一字串)。 AS2 編碼器會建置下列位在 `HTTP.UserHttpHeaders` 中的 AS2 標頭。 這些標頭一定會出現在 AS2 訊息中。  
  
- AS2-To  
  
- AS2-From  
  
- AS2-Version  
  
- MessageID  
  
- OriginalMessageID (僅適用於 MDN)  
  
  如果**的 要求 MDN**會檢查屬性，管線會將設定配置通知給、 回條傳遞選項，以及簽署-回條-MICalg AS2 標頭，訊息中對應的屬性，以及它的值中如果設定為"pcks7-signature"簽署回條通訊協定 AS2 標頭**要求簽署的 MDN**會檢查屬性。  
  
  如果 `HTTP.UserHttpHeaders` 內容屬性不存在，AS2 編碼器會建立它。 如果 `HTTP.UserHttpHeaders` 已存在，AS2 編碼器就會使用它，而不重新建立它。 如果您建立 `HTTP.UserHttpHeaders`，將標頭寫入其中，然後將此內容屬性寫入訊息內容中，AS2 編碼器就會使用這些標頭，而且這些標頭的優先順序高於其他來源的標頭。 唯一的例外是 AS2-From 標頭，它一定是取自協議屬性。  
  
  如果 AS2 標頭不在 `HTTP.UserHttpHeaders` 中，AS2 編碼器會從單一內容屬性加入它。 這表示，您可以藉由將 AS2 標頭升級或寫入訊息內容中，加入 AS2 標頭 (如果 AS2 標頭不在 `HTTP.UserHttpHeaders` 中)。 如果 AS2 標頭不在 `HTTP.UserHttpHeaders` 中，也不是內容中的屬性，AS2 編碼器就會從協議屬性將它加入至 `HTTP.UserHttpHeaders` 中。  
  
  在 AS2 編碼器建置 `HTTP.UserHttpHeaders` 屬性中的標頭之後，它會將此屬性加入訊息的內容中。 HTTP 配接器會收取 `HTTP.UserHttpHeaders`，並將 `HTTP.UserHttpHeaders` 中的標頭值附加到訊息的前面。  
  
> [!NOTE]
>  AS2 傳輸只適用於 HTTP 配接器。 不過，如果您手動設定適當的內容屬性，也可以使用 FILE 配接器傳輸 AS2 訊息。 如需詳細資訊，請參閱 <<c0> [ 透過 FILE 傳送埠傳送 AS2 訊息](../core/sending-an-as2-message-over-a-file-send-port.md)。  
  
## <a name="processing-the-returned-mdn"></a>處理傳回的 MDN  
 如果 MDN 已啟用，與雙向傳送埠相關聯的接收管線就會從接收 AS2 訊息的合作對象接收 MDN。  
  
> [!NOTE]
>  如需有關 AS2 傳送管線對內送 Mdn 執行處理的詳細資訊，請參閱[傳送外寄 MDN](../core/sending-an-outgoing-mdn.md)。  
  
## <a name="processing-the-returned-edi-acknowledgment"></a>處理傳回的 EDI 通知  
 如果 EDI 通知已啟用，與雙向傳送埠相關聯的接收管線也會從 EDI 訊息接收者接收 EDI 通知 (因為它會篩選 BizTalk EDI 通知訊息類型)。 如需詳細資訊，請參閱 <<c0> [ 處理收到的通知](../core/processing-a-received-acknowledgment.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何傳送 AS2 訊息](../core/how-biztalk-server-sends-as2-messages.md)