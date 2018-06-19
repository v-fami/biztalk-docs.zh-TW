---
title: BizTalk 訊息佇列大型訊息延伸模組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Message Queuing Large Message Extension
- utilities, BizTalk Message Queuing Large Message Extension
ms.assetid: 5d6892d3-fda8-41a3-8111-d28c11bd71fb
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 399c8e02d59a931dbf30bfa31ca28980dfa312be
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006399"
---
# <a name="biztalk-message-queuing-large-message-extension"></a>BizTalk 訊息佇列大型訊息延伸模組
原生訊息佇列無法處理的訊息內文大於 4megabytes (MB)。 不過，Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含原生訊息佇列的附加元件可以處理大於 4 MB 的訊息。 此附加元件當做 Mqrtlarge.dll 檔案，會傳遞，而且會公開**MQSendLargeMessage**和**MQReceiveLargeMessage**應用程式發展介面 (Api)，以及類似的 COM 模型。 這些函式會實作為標準訊息佇列應用程式開發介面， **MQSendMessage**和**MQReceiveMessage**分別。  
  
 若要參與大型訊息交換，訊息佇列電腦必須安裝 Mqrtlarge.dll 檔案，而且訊息佇列應用程式必須使用附加元件 API。 否則，完整訊息會被分割。  
  
 **SDK 中的位置**  
  
 \<*安裝路徑*\>\SDK\ Mqrtlarge.dll  
  
 **檔案庫存**  
  
 下表顯示此公用程式所使用的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|Mqrtlarge.dll|公開的 Win32 動態連結程式庫**MQSendLargeMessage**和**MQReceiveLargeMessage**。<br /><br /> 標頭檔位於*\<安裝路徑\>* \SDK\Include 目錄。 **注意：** 必須安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]到 64 位元版本的 Windows，才能存取 64 位元版本的 Mqrtlarge.dll。|  
  
 **使用此公用程式**  
  
 請依照下列程序執行 Mqrtlarge.dll 檔案。  
  
### <a name="to-use-the-mqrtlargedll-file"></a>若要使用 Mqrtlarge.dll 檔案  
  
1.  > [!NOTE]
    >  MSMQ 未搭配 BizTalk Server 解決方案，MQRTLarge.dll 可能仍正常運作。 不過，這不是建議的設定，Microsoft 支援，而且如果在 BizTalk Server 環境之外使用，可能會發生非預期的結果。  
  
     將 Mqrtlarge.dll 檔案新增至不包含 BizTalk Server 安裝的電腦。 「訊息佇列」會使用 Mqrtlarge.dll，傳送訊息至 BizTalk Server 或從其接收訊息。  
  
2.  若要存取 Mqrtlarge.dll 檔案中的 API，請在傳送訊息至連接 BizTalk「訊息佇列」結束點的其他電腦或從中接收訊息的應用程式中，新增 Mqrtlarge.dll 檔案的參考。  
  
 **註解**  
  
 大型訊息會傳送至標準「訊息佇列」(也稱為 MSMQ) 佇列。 您只能在這些佇列上使用大型訊息 API，但這並非強制性。  
  
 您仍然可以使用**MQSendMessage**將訊息傳送至您傳送大型訊息的佇列。 同樣地，您可以使用**MQReceiveMessage** ，從這些佇列接收訊息，但不建議因為它可能會影響效能的**MQReceiveLargeMessage**應用程式開發介面。  
  
 進行復原，建議您改用**DEAD_LETTER**日誌。  
  
 **片段**  
  
 一般而言，大型訊息會分割成數個訊息，每個訊息都小於 4 MB。 只分割內文，瞭解這一點非常重要。 其餘的屬性會隨著每個片段傳送。  
  
 片段數目是由訊息大小和片段大小所定義。 Mqrtlarge.dll 檔案或 BizTalk「訊息佇列」的適當部分可能會自動決定片段大小。 應用程式也可以明確地指定片段大小。  
  
 請注意，大型訊息延伸模組需要新增常數大小的額外內部資料，以便延伸訊息。  
  
 **PROPID_M_EXTENSION**  
  
 您可以使用**PROPID_M_EXTENSION/PROPID_M_EXTENSION_LEN**屬性來簽署訊息。 簽章包含 40 位元組 (B)。 下表顯示簽章片段。  
  
|Description|大小|  
|-----------------|----------|  
|此項表示應使用傳送此訊息的全域唯一識別碼 (GUID) **MQSendLargeMessage**|16 B|  
|訊息的 GUID： 通用於所有訊息部分的唯一的每個大型訊息識別碼|16 B|  
|大型訊息的總大小|4 B|  
|部分編號|2 B|  
|訊息部分數目|2 B|  
  
 在決定来使用**PROPID_M_EXTENSION**還有其他。 Microsoft Host Integration Server MSMQ-MQSeries Bridge 會使用此屬性，傳遞包含 MQSeries 和訊息佇列訊息之間未直接對應之屬性的結構。 將訊息明確或隱含傳送至 MQSeries 或從中接收訊息的應用程式會使用此結構。 當接收端應用程式已從佇列接收訊息時，「訊息佇列」都會產生通知。 該通知會傳送至傳送端應用程式所指定的佇列。 至於大型訊息，您只針對其最後部分傳送此通知。  
  
## <a name="see-also"></a>請參閱  
 [SDK 中的公用程式](../core/utilities-in-the-sdk.md)