---
title: "AS2 BizTalk Server 中的處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0027d3db-24a5-459d-9f4e-a75f49d31d82
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11a5bb12d9a7b21a18b92162370d7be14feda8dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="as2-processing-in-biztalk-server"></a>BizTalk Server 中的 AS2 處理
本主題將提供概觀，介紹在接收端與傳送端進行的 AS2 訊息處理，以及交易夥伴協議如何協助完成 AS2 訊息處理。  
  
## <a name="trading-partner-agreements-for-as2-processing"></a>適用於 AS2 處理的交易夥伴協議  
 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 AS2 支援中，交易夥伴協議扮演了關鍵的角色。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，大部分與 AS2 處理有關的組態與管理功能都是藉由設定商務設定檔之間的交易夥伴協議來完成。 協議會將在雙方合作對象所屬商務設定檔中共同的雙向訊息處理屬性收集在一起。 協議是根據針對每個商務設定檔所定義的通訊協定設定而建置。 若要在兩個商務設定檔之間實作交易夥伴協議，您需為每個會交換訊息的商務設定檔定義屬性。 您可以在「交易夥伴管理」(TPM) 使用者介面中，將每個商務設定檔的屬性設定為 AS2 訊息接收者和 AS2 訊息傳送者。 TPM 畫面位於**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您不需要身為開發人員，就可以設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的 AS2 處理。  
  
 您可以將 AS2 屬性指定為商務設定檔之「傳輸通訊協定設定」的一部分，也可以直接在交易夥伴協議中指定 AS2 設定。 如需通訊協定設定的詳細資訊，請參閱[通訊協定設定](../core/protocol-settings.md)。 如需協議的詳細資訊，請參閱[交易夥伴協議](../core/trading-partner-agreement.md)。  您可以透過設定 AS2 特有屬性，設定下列 AS2 功能：  
  
-   選取不可否認性儲存選項  
  
-   指定外寄訊息的簽章、壓縮或加密屬性  
  
-   要求外寄訊息的 MDN  
  
-   透過在 AS2 訊息的標頭中覆寫簽章、壓縮、加密和 MDN 屬性，設定內送 MDN 的屬性。  
  
 如需如何交易夥伴協議，AS2 處理中的詳細資訊，請參閱[中協議的角色中的 AS2 處理](../core/the-role-of-agreements-in-as2-processing.md)。  
  
> [!NOTE]
>  目前沒有適用於 AS2 處理的全域屬性，如同 EDI 處理。  
  
## <a name="as2-receive-side-processing"></a>AS2 接收端處理  
 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 收到 AS2 訊息時，它會在 AS2 接收管線中處理該訊息。 其中有一個用於透過 AS2 接收 EDI 訊息的管線 (AS2EdiReceive)，它可同時執行 AS2 和 EDI 處理。 另一個管線 (AS2Receive) 只會針對透過 AS2 接收的非 EDI 訊息執行 AS2 處理。  
  
 AS2 接收端處理包括下列作業：  
  
-   交易夥伴協議查閱  
  
    > [!NOTE]
    >  在舊版的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，合作對象定義也包含協議定義。 因此，接收管線在查閱合作對象屬性時，會在合作對象定義內部尋找協議定義，然後據以處理訊息。 使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，由於合作對象 (或交易夥伴) 不同於交易夥伴協議，因此接收管線會特別去尋找交易夥伴協議。  
  
    > [!NOTE]
    >  如果某個訊息所解析的所有目標協議都已停用，就會擱置此訊息。  此外，事件日誌也會記錄一則警告。  
  
-   在不可否認性資料庫中儲存訊息的複本  
  
-   檢查重複的訊息  
  
-   處理包含多個文件的訊息  
  
-   從 MIME 信封中擷取文件檔案名稱  
  
-   解密訊息  
  
-   解壓縮訊息  
  
-   驗證訊息的數位簽章  
  
-   產生 HTTP 回應  
  
-   產生 MDN 回應  
  
 以下是您在使用 AS2 接收端處理時必須考量的一些事項：  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會以同步或非同步模式傳回 MDN。 若 MDN 將以非同步方式傳回，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 就必須透過不同的傳送埠傳送它。  
  
-   當您透過 AS2 接收非 EDI 檔案 (不是 XML)，而且需要執行非 EDI 內容的解譯時，就必須使用回送機制搭配第二個接收管線。 如需詳細資訊，請參閱[接收端處理透過 AS2 內送的非 EDI 訊息的](../core/receive-side-processing-of-an-incoming-non-edi-message-over-as2.md)。  
  
-   接收位置只能使用 HTTP 配接器。  
  
-   如需有關 AS2 接收端處理的詳細資訊，請參閱[如何 BizTalk Server 接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md)。  
  
-   如需有關 AS2 解譯器在接收管線中執行之特定處理的詳細資訊，請參閱[處理內送 AS2 訊息](../core/processing-an-incoming-as2-message.md)。  
  
## <a name="as2-send-side-processing"></a>AS2 傳送端處理  
 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 產生並傳送外寄 AS2 訊息時，它會在 AS2 傳送管線中處理該訊息。 其中有一個用於透過 AS2 傳送 EDI 訊息的管線 (AS2EdiSend)，它可同時執行 AS2 和 EDI 處理。 另一個管線 (AS2Send) 只會針對透過 AS2 傳送的非 EDI 訊息執行 AS2 處理。  
  
 AS2 傳送端處理包括下列作業：  
  
-   交易夥伴協議查閱  
  
    > [!NOTE]
    >  在舊版的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，合作對象定義也包含協議定義。 因此，傳送管線在查閱合作對象屬性時，會在合作對象定義內部尋找協議定義，然後據以處理訊息。 使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，由於合作對象 (或交易夥伴) 不同於交易夥伴協議，因此傳送管線會特別去尋找交易夥伴協議。  
  
    > [!NOTE]
    >  如果某個訊息所解析的所有目標協議都已停用，就會擱置此訊息。  此外，事件日誌也會記錄一則警告。  
  
-   在不可否認性資料庫中儲存訊息的複本  
  
-   套用 AS2 信封  
  
-   傳送多個文件  
  
-   將每個文件檔案名稱儲存成 MIME 信封的一部分  
  
-   簽署訊息  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可讓您覆寫預設的簽章憑證，並改用協議中同意的憑證。 如需覆寫預設憑證簽署外寄訊息的指示，請參閱[設定 AS2 屬性](../core/configuring-as2-properties.md)。  
  
-   壓縮訊息  
  
-   加密訊息  
  
-   計算 MDN 的 MIC 值  
  
-   處理內送 MDN (在同步 MDN 的情況下)  
  
-   重新傳送訊息 (如果沒有收到任何 MDN 的話)  
  
 以下是您在使用 AS2 接收端處理時必須考量的一些事項：  
  
-   傳送埠只能使用 HTTP 配接器。  
  
-   如需有關 AS2 傳送端處理的詳細資訊，請參閱[如何 BizTalk Server 傳送 AS2 訊息](../core/how-biztalk-server-sends-as2-messages.md)。  
  
-   如需在傳送管線中執行之特定處理的詳細資訊，請參閱[產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)。  
  
## <a name="see-also"></a>另請參閱  
 [中協議的 AS2 處理的角色](../core/the-role-of-agreements-in-as2-processing.md)   
 [BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md)   
 [BizTalk Server 傳送 AS2 訊息的方式](../core/how-biztalk-server-sends-as2-messages.md)