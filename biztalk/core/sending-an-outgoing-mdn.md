---
title: "傳送外寄 MDN |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dce7620-d354-4b76-bcbc-f97dc93c3fc3
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d947751e06e0dc9892ab63e109b417047ad91b59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sending-an-outgoing-mdn"></a>傳送外寄 MDN
外寄 MDN 是由 AS2EDIReceive 或 AS2Receive receive 管線產生，並且由 AS2Send 管線傳送。 本主題將描述如何傳送 MDN。 如需有關如何產生 MDN 的詳細資訊，請參閱[產生外寄 MDN](../core/generating-an-outgoing-mdn.md)。  
  
> [!NOTE]
>  AS2EDISend 傳送管線不是用來傳送外寄 MDN，因為該管線中的 EDI 組合器不是在處理 MDN 時使用。  
  
## <a name="agreement-resolution-for-an-mdn"></a>MDN 的協議解析  
 MDN 會自動路由。 它包含路由至目標協議時所需的資訊。 傳送管線會使用 AS2 協議屬性來處理外寄 MDN。 不過，MDN 不必擁有它路由傳送至合作對象解析協議。  
  
 當 AS2Send 管線處理外寄 MDN 時，它會使用 AS2 的訊息內容取得來處理 MDN 的協議屬性中的值。 它是藉由比對 AS2-內容屬性與 [AS2-協議屬性中**識別碼**單向 AS2 協議索引標籤中的頁面**協議屬性**] 對話方塊。 如果此 mdn 的協議解析可能會失敗，AS2-以值未設定協議。 如果無法判斷協議，預設的協議用來產生 MDN。  
  
 在外寄 MDN 的預設協議中，會執行憑證解析清單驗證。 如果您不要執行此驗證，請確認已設定正確的 AS2-To 協議屬性，以便解析接收的合作對象並判斷協議屬性。 如此一來，便不會使用預設協議 (會提示要驗證憑證解析清單)。 您也需要停用**檢查憑證撤銷清單**屬性**驗證**頁面的單向 AS2 協議索引標籤中**協議屬性**對話方塊。  
  
## <a name="synchronous-and-asynchronous-transmission"></a>同步和非同步傳輸  
 在預設 AS2 程序中，MDN 是以同步的方式傳送。 MDN 是由與雙向接收埠相關聯的傳送埠傳送。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]為 HTTP 回應至 HTTP POST 或 HTTPS 回應至 HTTPS POST，相同的 TCP/IP 連線傳送 MDN。 MDN 會包含在 [HTTP 回應] 命令的訊息內文中。  
  
 如果 MDN 將以非同步的方式傳送，則 MDN 必須透過不同的傳送埠傳送，該傳送埠會從 MessageBox 挑選 MDN。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您可以將 MDN 當成個別 HTTP Post 傳送唯一的 TCP/IP 連線，不同於用來傳遞原始 AS2 訊息。 即使 MDN 設為不同的 HTTP Post，Post 仍需要 [HTTP 回應] 命令。  
  
 非同步的 MDN 通常會傳送至原始 AS2 訊息的 Receipt-Delivery-Option 標頭中的 URL。 不過，如果**對驗證與 MDN 使用協議設定，而非訊息標頭**上設定屬性上**驗證**頁面的單向 AS2 協議索引標籤中**協議屬性**對話方塊中，將會傳送 MDN 的 url，**回條傳遞選項 (URL)**協議屬性設定為。  
  
## <a name="how-the-send-pipeline-processes-an-outgoing-mdn"></a>傳送管線如何處理外寄 MDN  
 AS2Send 管線處理外寄 MDN 的方式如下所示：  
  
-   如果已在 AS2 單向協議屬性中啟用，則執行 MIME 處理，包括套用數位簽章。  
  
-   在不可否認性資料庫 (BizTalkDTADb 資料庫的 EdiMessageContent 資料表) 中填入相互關聯項目。  
  
-   複製 MDN （以電傳格式） 並將它儲存在不可否認性資料庫中，如果在啟用**為輸出的 MDN 啟用 NRR**協議屬性。  
  
-   將 MDN 傳送至 HTTP 配接器  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 傳送 AS2 訊息的方式](../core/how-biztalk-server-sends-as2-messages.md)   
 [AS2 傳送元件](../core/as2-send-components.md)