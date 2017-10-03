---
title: "BizTalk Server 中的 EDI 處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bdc60423-24b6-4920-a870-520f575085ed
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a91afb8542284b5c83b19886a417350aebbc0ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-processing-in-biztalk-server"></a>BizTalk Server 中的 EDI 處理
本主題將提供概觀，介紹在接收端與傳送端進行的 EDI 訊息處理，以及交易夥伴協議如何協助完成 EDI 訊息處理。  
  
## <a name="trading-partner-agreements-for-edi-processing"></a>適用於 EDI 處理的交易夥伴協議  
 在 [!INCLUDE[prague](../includes/prague-md.md)] 的 EDI 支援中，交易夥伴協議扮演了關鍵的角色。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，大部分與 EDI 處理有關的組態與管理功能都是藉由設定商務設定檔之間的交易夥伴協議來完成。 協議會將在雙方合作對象所屬商務設定檔中共同的雙向訊息處理屬性收集在一起。 協議是根據針對每個商務設定檔所定義的通訊協定設定而建置。 若要在兩個商務設定檔之間實作交易夥伴協議，您需為每個會交換訊息的商務設定檔定義屬性。 您需為每個做為交換接收者和交換傳送者的商務設定檔設定屬性。 為了處理內送訊息或產生外寄訊息，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須知道訊息會解析成的協議，以及套用至訊息的結構描述。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 若是無法判斷協議，就會使用 TPM 介面中針對後援交易夥伴協議所定義的屬性。  
  
 有兩個主要組編碼通訊協定設定在 TPM 中： 一個用於 EDIFACT 屬性，一個適用於 X12 屬性。 這兩組屬性近乎相同。 如需通訊協定設定的詳細資訊，請參閱[通訊協定設定](../core/protocol-settings.md)。 如需協議的詳細資訊，請參閱[交易夥伴協議](../core/trading-partner-agreement.md)。 您可以在交易夥伴管理 (TPM) 使用者介面中設定通訊協定設定與交易夥伴協議。 TPM 畫面位於**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您不需要身為開發人員，就可以設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的 EDI 處理。  
  
 如需如何交易夥伴協議 EDI 處理的詳細資訊，請參閱[中協議的角色中處理 EDI](../core/the-role-of-agreements-in-edi-processing.md)。  
  
## <a name="edi-receive-side-processing"></a>EDI 接收端處理  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在收到 EDI 訊息時，會在 EDI 接收管線中處理該訊息。 接收管線會執行下列基本處理：  
  
-   查閱交易夥伴協議及判斷結構描述。  
  
    > [!NOTE]
    >  在舊版的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，合作對象定義也包含協議定義。 因此，接收管線在查閱合作對象屬性時，會在合作對象定義內部尋找協議定義，然後據以處理訊息。 使用 [!INCLUDE[prague](../includes/prague-md.md)] 時，由於合作對象 (或交易夥伴) 不同於交易夥伴協議，因此接收管線會特別去尋找交易夥伴協議。  
  
    > [!NOTE]
    >  如果某個訊息所解析的所有目標協議都已停用，就會擱置此訊息。 此外，事件日誌也會記錄一則警告。  
  
-   如果單一 EDI 訊息包含多個交換，則會分割此交換，分開處理每個交換 (如果啟用此功能的話)。 如需詳細資訊，請參閱[啟用接收的多個交換單一訊息中](../core/enabling-the-receiving-of-multiple-interchanges-in-a-single-message.md)。  
  
-   剖析每個 EDI 交換，並將 X12 或 EDIFACT 編碼資料轉換為 XML 文件。  
  
-   根據 EDI 標準、夥伴協議和訊息結構描述來驗證信封與其訊息。  
  
-   如果已批次處理交換，則會分割此批次交換 (包括為每個交易集建立 XML 檔案，以及升級批次處理所需的屬性) 或保留交換。  
  
-   產生通知。  
  
-   將 EDI 信封轉換為內容屬性，以及升級 EDI 處理的其他屬性。  
  
-   升級可控制批次處理的屬性， 這包含將解除批次的交易集傳送至多個合作對象。  
  
 以下是您在使用 EDI 接收端處理時必須考量的一些事項：  
  
-   接收位置可以使用任何類型的傳輸類型。  
  
-   如需有關 EDI 接收端處理的詳細資訊，請參閱[如何 BizTalk Server 接收 EDI 訊息](../core/how-biztalk-server-receives-edi-messages.md)。  
  
-   如需 EDI 解譯器會在接收管線中執行之特定處理的詳細資訊，請參閱[EDI 解譯器的運作方式](../core/how-the-edi-disassembler-works.md)。  
  
## <a name="edi-batch-processing"></a>EDI 批次處理  
 如果內送訊息為已批次處理的交換，則 EDI 接收管線會根據組態將此批次交換分割為其組成交易集，或保留此批次交換。 EDIReceive 管線會使用 BatchMarker 管線元件，將要批次處理的任何交換路由傳送至批次處理協調流程或路由協調流程。  
  
 在接收端處理之後，批次處理協調流程會對交易集進行批次處理以供傳送。 批次處理協調流程會根據篩選準則、啟動範圍和釋放準則來建立批次。  
  
 如果需要將未批次處理的 EDI 交易集傳送至批次，則路由協調流程會處理這些交易集。 此時會為每個相符的批次各建立交易集的一個複本。  
  
 如需有關在批次處理中執行之特定處理的詳細資訊，請參閱[處理內送批次](../core/processing-incoming-batches.md)或[批次處理外寄 EDI 訊息](../core/batching-outgoing-edi-messages.md)。  
  
## <a name="edi-send-side-processing"></a>EDI 傳送端處理  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在產生並傳送外寄 EDI 訊息時，會在 EDI 傳送管線中處理該訊息。 傳送管線會執行下列基本處理：  
  
-   查閱交易夥伴協議及判斷結構描述。  
  
    > [!NOTE]
    >  在舊版的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，合作對象定義也包含協議定義。 因此，傳送管線在查閱合作對象屬性時，會在合作對象定義內部尋找協議定義，然後據以處理訊息。 使用 [!INCLUDE[prague](../includes/prague-md.md)] 時，由於合作對象 (或交易夥伴) 不同於交易夥伴協議，因此傳送管線會特別去尋找交易夥伴協議。  
  
    > [!NOTE]
    >  如果某個訊息所解析的所有目標協議都已停用，就會擱置此訊息。  此外，事件日誌也會記錄一則警告。  
  
-   序列化 EDI 訊息，並將 XML 文件轉換為 X12 或 EDIFACT 編碼資料。  
  
-   如果訊息資料中有些字元同時也是 X12 分隔符號，您可以設定傳送管線，以其他字元取代內容中的這些字元。  
  
-   如果 EDI 訊息是已批次處理的交換，在批次處理協調流程建置批次之後，傳送管線會從 BizTalk MessageBox 取用此交換。  
  
-   驗證外寄訊息。  
  
-   根據在執行階段指定的合作對象屬性或 EDI 信封屬性，建立 EDI 信封。  
  
-   處理接收的通知。  
  
 以下是您在使用 EDI 傳送端處理時必須考量的一些事項：  
  
-   傳送埠可以使用任何類型的傳輸。  
  
-   如需有關 EDI 傳送端處理的詳細資訊，請參閱[如何 BizTalk Server 傳送 EDI 訊息](../core/how-biztalk-server-sends-edi-messages.md)。  
  
-   如需在傳送管線中執行之特定處理的詳細資訊，請參閱[EDI 組合器的運作方式](../core/how-the-edi-assembler-works.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 中的 EDI 支援](../core/edi-support-in-biztalk-server1.md)   
 [EDI 支援問題](../core/edi-support-issues.md)   
 [中協議 EDI 處理的角色](../core/the-role-of-agreements-in-edi-processing.md)   
 [BizTalk Server 如何接收 EDI 訊息](../core/how-biztalk-server-receives-edi-messages.md)   
 [BizTalk Server 如何傳送 EDI 訊息](../core/how-biztalk-server-sends-edi-messages.md)   
 [開發和設定 BizTalk Server EDI 解決方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md)