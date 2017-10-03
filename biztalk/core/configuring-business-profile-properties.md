---
title: "設定商務設定檔屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.businessprofile.properties
ms.assetid: d3c87777-9bcd-4482-bbb7-efea08cdeead
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b43f6af9999b0c09698d6cebe6fbe9af505a42a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-business-profile-properties"></a>設定商務設定檔屬性
商務設定檔代表組織中的商務部門。 就像組織可以有許多部門一樣 (會計、採購、出貨等)，合作對象也可以有許多商務設定檔，分別代表組織中的各部門。 商務設定檔屬性包含下列資訊：  
  
-   一般資訊，例如商務設定檔名稱  
  
-   可以與商務設定檔產生關聯的唯一識別項  
  
-   編碼設定 (適用於 X12 與 EDIFACT 訊息) 與通訊協定設定 (AS2)，用於定義商務設定檔可以如何和另一個合作對象往返傳送訊息。  
  
 如需商務設定檔的詳細資訊，請參閱[商務設定檔](http://msdn.microsoft.com/library/f8286130-57fe-40ed-9fd8-81da2c8baaaf)。 如需編碼與傳輸通訊協定設定的詳細資訊，請參閱[通訊協定設定](../core/protocol-settings.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-business-profile-properties"></a>若要設定商務設定檔屬性  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象**節點。 在**合作對象與商務設定檔** 窗格中，以滑鼠右鍵按一下合作對象，指向 新增，，然後按一下**商務設定檔**。  
  
2.  在**一般**索引標籤**一般**頁面上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|輸入商務設定檔名稱。|  
    |**說明**|輸入商務設定檔的說明。|  
    |**其他屬性 – 名稱/值**|請輸入名稱-值組來儲存合作對象的任何資訊。 您可以視需要新增任意數目的名稱-值組。 **注意：**名稱 / 值組不會由 BizTalk Server 進行任何處理; 此資料僅供資訊。|  
    |**Delete**|按一下選取的名稱-值組，加以刪除。|  
  
3.  視需要新增商務設定檔的商務識別。 在**一般**索引標籤**識別**頁面上，執行下列動作：  
  
    > [!NOTE]
    >  在此階段，新增商務識別並非必要動作。 您也可以稍後再新增商務識別，做為商務設定檔協議的一部分。 如果您選擇立即新增商務識別，則建立此商務設定檔的協議時將有這些識別可使用。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|按一下空白儲存格，然後從下拉式清單中，選取將唯一的商務識別身分提供給組織的驗證內文。 例如， **D-U-N-S (Dun & Bradstreet)**。 兩個商務夥伴可以選擇一個彼此都同意的商務識別。 如需這類案例中，選取**使用者相互定義**（適用於 EDIFACT) 或**使用者相互定義 (X12)** （適用 X12)。|  
    |**Qualifier**|會顯示您針對所選取的值為基礎的預先定義的值**名稱**。|  
    |**值**|輸入商務識別的值。 提供商務識別的值時，必須考量下列事項。<br /><br /> -針對指定的合作對象，您可以使用相同的識別名稱與識別值組合的多個商務設定檔。 例如，您可以讓兩個商務設定檔的合作對象**名稱**為**使用者相互定義 (X12)**和**值**為**THEM**。<br />-透過合作對象，您不能有兩個商務設定檔使用相同的識別名稱與識別值組合。|  
    |**Delete**|按一下可刪除選取的識別。|  
  
4.  視需要，新增要用於 X12 編碼訊息的通訊協定設定。  
  
    1.  在**設定檔屬性**對話方塊的右上角，按一下**新增通訊協定設定**，指向 **編碼設定**，然後按一下  **X12**.  
  
    2.  加入新的索引標籤旁**一般** 索引標籤。在**常見**新加入的頁面索引標籤的**通訊協定設定名稱**文字方塊中，輸入名稱來識別這一組編碼通訊協定設定。 索引標籤的名稱也會設為您在文字方塊中指定的值。  
  
    3.  您可以將 X12 屬性定義為商務設定檔的一部分，或直接定義於協議中。 如果您將屬性定義為商務設定檔的一部分，您建立協議時將會使用相同的設定。 由於相同的屬性可透過兩個位置來定義，因此本文件將只提供如何將屬性設定為協議一部分的指示。 如果您要將屬性定義為商務設定檔的一部分，下表提供了相關章節的連結，請參考其中所含的屬性設定資訊。  
  
        > [!NOTE]
        >  輸入的設定會套用到合作對象收到的所有訊息。 輸出的設定會套用到合作對象傳送的所有訊息。  
  
        > [!NOTE]
        >  即使您將通訊協定設定指定為商務設定檔的一部分，您仍可隨時覆寫特定協議的設定。  
  
        |設定|說明請見|  
        |-------------|------------------------------|  
        |**輸入設定 > 交換設定 > 驗證**|[設定驗證 （X12 交換設定）](../core/configuring-validation-x12-interchange-settings.md)|  
        |**輸入設定 > 交換設定 > 本機主機設定**|[設定本機主機設定 （X12 交換設定）](../core/configuring-local-host-settings-x12-interchange-settings.md) （接收者的設定）|  
        |**輸入設定 > 交易集設定 > 交易集清單**|[設定交易集清單 (X12)](../core/configuring-transaction-set-list-x12.md)|  
        |**輸入設定 > 交易集設定 > 驗證**|[設定驗證 （X12-交易集設定）](../core/configuring-validation-x12-transaction-set-settings.md)|  
        |**輸入設定 > 交易集設定 > 本機主機設定**|[設定本機主機設定 （X12-交易集設定）](../core/configuring-local-host-settings-x12-transaction-set-settings.md)|  
        |**輸出的設定 > 交換設定 > 其他識別項**|[設定識別項 (X12)](../core/configuring-identifiers-x12.md)|  
        |**輸出的設定 > 交換設定 > 通知**|[設定通知 (X12)](../core/configuring-acknowledgements-x12.md)|  
        |**輸出的設定 > 交換設定 > 信封**|[設定信封 （X12 交換設定）](../core/configuring-envelopes-x12-interchange-settings.md)|  
        |**輸出的設定 > 交換設定 > 字元集與分隔符號**|[設定字元集和分隔符號 (X12)](../core/configuring-charset-and-separators-x12.md)|  
        |**輸出的設定 > 交換設定 > 控制編號**|[設定本機主機設定 （X12 交換設定）](../core/configuring-local-host-settings-x12-interchange-settings.md) （寄件者的設定）|  
        |**輸出的設定 > 交易集設定 > 信封**|[設定信封 （X12-交易集設定）](../core/configuring-envelopes-x12-transaction-set-settings.md)|  
  
        > [!NOTE]
        >  您可以為一個商務設定檔定義多個 X12 編碼通訊協定設定。  
  
5.  視需要，新增要用於 EDIFACT 編碼訊息的通訊協定設定。  
  
    1.  在**設定檔屬性**對話方塊的右上角，按一下**新增通訊協定設定**，指向 **編碼設定**，然後按一下  **EDIFACT**。  
  
    2.  加入新的索引標籤旁**一般** 索引標籤。在**常見**新加入的頁面索引標籤的**通訊協定設定名稱**文字方塊中，輸入名稱來識別這一組編碼通訊協定設定。 索引標籤的名稱也會設為您在文字方塊中指定的值。  
  
    3.  您可以將 EDIFACT 屬性定義為商務設定檔的一部分，或直接定義於協議中。 如果您將屬性定義為商務設定檔的一部分，您建立協議時將會使用相同的設定。 由於相同的屬性可透過兩個位置來定義，因此本文件將只提供如何將屬性設定為協議一部分的指示。 如果您要將屬性定義為商務設定檔的一部分，下表提供了相關章節的連結，請參考其中所含的屬性設定資訊。  
  
        > [!NOTE]
        >  輸入的設定會套用到合作對象收到的所有訊息。 輸出的設定會套用到合作對象傳送的所有訊息。  
  
        > [!NOTE]
        >  即使您將通訊協定設定指定為商務設定檔的一部分，您仍可隨時覆寫特定協議的設定。  
  
        |設定|說明請見|  
        |-------------|------------------------------|  
        |**輸入設定 > 交換設定 > 其他識別項**|[設定識別項 (EDIFACT)](../core/configuring-identifiers-edifact.md)|  
        |**輸入設定 > 交換設定 > 驗證**|[設定驗證 （Edifact-interchange 設定）](../core/configuring-validation-edifact-interchange-settings.md)|  
        |**輸入設定 > 交換設定 > 本機主機設定**|[設定本機主機設定 （EDIFACT-交換設定）](../core/configuring-local-host-settings-edifact-interchange-settings.md) （接收者的設定）|  
        |**輸入設定 > 交易集設定 > 交易集清單**|[設定交易集清單 (EDIFACT)](../core/configuring-transaction-set-list-edifact.md)|  
        |**輸入設定 > 交易集設定 > 驗證**|[設定驗證 （EDIFACT 交易集設定）](../core/configuring-validation-edifact-transaction-set-settings.md)|  
        |**輸入設定 > 交易集設定 > 本機主機設定**|[設定本機主機設定 （EDIFACT 交易集設定）](../core/configuring-local-host-settings-edifact-transaction-set-settings.md)|  
        |**輸出的設定 > 交換設定 > 其他識別項**|[設定識別項 (EDIFACT)](../core/configuring-identifiers-edifact.md)|  
        |**輸出的設定 > 交換設定 > 通知**|[設定通知 (EDIFACT)](../core/configuring-acknowledgements-edifact.md)|  
        |**輸出的設定 > 交換設定 > 信封**|[設定信封 （Edifact-interchange 設定）](../core/configuring-envelopes-edifact-interchange-settings.md)|  
        |**輸出的設定 > 交換設定 > 字元集與分隔符號**|[設定字元集和分隔符號 (EDIFACT)](../core/configuring-charset-and-separators-edifact.md)|  
        |**輸出的設定 > 交換設定 > 控制編號**|[設定本機主機設定 （EDIFACT-交換設定）](../core/configuring-local-host-settings-edifact-interchange-settings.md) （寄件者的設定）|  
        |**輸出的設定 > 交易集設定 > 信封**|[設定信封 （EDIFACT 交易集設定）](../core/configuring-envelopes-edifact-transaction-set-settings.md)|  
  
        > [!NOTE]
        >  您可以為一個商務設定檔定義多個 EDIFACT 編碼通訊協定設定。  
  
6.  視需要，新增要用於 AS2 傳輸的通訊協定設定。  
  
    1.  在**設定檔屬性**對話方塊的右上角，按一下**新增通訊協定設定**，指向 **傳輸設定**，然後按一下  **AS2**.  
  
    2.  加入新的索引標籤旁**一般** 索引標籤。上**常見**新加入的頁面索引標籤的**通訊協定設定名稱**文字方塊中，輸入名稱來識別這組傳輸通訊協定設定。 索引標籤的名稱也會設為您在文字方塊中指定的值。  
  
    3.  您可以將 AS2 屬性定義為商務設定檔的一部分，或直接定義於協議中。 如果您將屬性定義為商務設定檔的一部分，您建立協議時將會使用相同的設定。 由於相同的屬性可透過兩個位置來定義，因此本文件將只提供如何將屬性設定為協議一部分的指示。 如果您要將屬性定義為商務設定檔的一部分，下表提供了相關章節的連結，請參考其中所含的屬性設定資訊。  
  
        > [!NOTE]
        >  輸入的設定會套用到合作對象收到的所有訊息。 輸出的設定會套用到合作對象傳送的所有訊息。  
  
        > [!NOTE]
        >  即使您將通訊協定設定指定為商務設定檔的一部分，您仍可隨時覆寫特定協議的設定。  
  
        |設定|說明請見|  
        |-------------|------------------------------|  
        |**輸入設定 > 驗證**|[設定驗證 (AS2)](../core/configuring-validation-as2.md)|  
        |**輸入設定 > 本機主機設定 > 訊息的 HTTP 設定**|[設定訊息的 HTTP 設定](../core/configuring-http-settings-for-messages.md)|  
        |**輸入設定 > 本機主機設定 > 產生 MDN 設定**|[設定接收者 MDN 設定](../core/configuring-receiver-mdn-settings.md)|  
        |**輸入設定 > 本機主機設定 > 訊息追蹤 (NRR)**|[設定接收者訊息追蹤 (NRR)](../core/configuring-receiver-message-tracking-nrr.md)|  
        |**輸出的設定 > 通知 (Mdn)**|[設定通知 (MDN) (AS2)](../core/configuring-acknowledgements-mdns-as2.md)|  
        |**輸出的設定 > 本機主機設定 > 一般**|[設定一般本機主機設定 (AS2)](../core/configuring-general-local-host-settings-as2.md)|  
        |**輸出的設定 > 本機主機設定 > MDN 的 HTTP 設定**|[設定 Mdn 的 HTTP 設定](../core/configuring-http-settings-for-mdns.md)|  
        |**輸出的設定 > 本機主機設定 > 訊息追蹤 (NRR)**|[設定寄件者訊息追蹤 (NRR)](../core/configuring-sender-message-tracking-nrr.md)|  
        |**輸出的設定 > 簽章憑證**|[設定簽章憑證 (AS2)](../core/configuring-signature-certificates-as2.md)|  
  
        > [!NOTE]
        >  您可以為一個商務設定檔定義多個 AS2 傳輸通訊協定設定。  
  
7.  按一下**套用**接受這些屬性，或按一下**確定**來完成組態設定。 任何一項動作都會驗證設定。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 屬性](../core/configuring-edi-properties.md)