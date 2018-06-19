---
title: 設定傳送和接收 EDI 通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3db1c9f7-bafa-4659-a3c4-0faa56606081
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d1ffc367e4b87d29e372bc434c0eda18da4363a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969756"
---
# <a name="configuring-the-sending-and-receiving-of-edi-acknowledgments"></a>設定傳送及接收 EDI 通知
如果要設定傳送 EDI 通知來回應收到的交換，您必須執行下列工作：  
  
-   在由收到的交換解析成的協議中啟用通知。 這樣是宣告傳送交換的合作對象預期收到通知。  
  
-   如果通知必須設定特定屬性 (例如啟用 CR LF、分隔符號字元應不同等) 再傳回，請在其他單向協議索引標籤中設定那些屬性。這樣做可以設定合作對象傳回通知的方式。  
  
    > [!NOTE]
    >  如果交換解析協議中定義**party a-> partyb**  索引標籤中設定與應如何產生通知有關的屬性**partyb-> party a**  索引標籤。這是必要的因為通知內容屬性為傳送者和接收者辨識符號都會設定為您在指定的值相反**party a-> partyb**  索引標籤。例如，如果在交換訊息所解析成的協議中，傳送者與接收者識別碼是設為 THEM 與 US，則通知裡的傳送者與接收者內容屬性將設為 US 與 THEM。 一般而言，其他單向協議索引標籤也會分別將傳送者與接收者識別項設定為 US 與 THEM。 因此，通知訊息會解析成該協議，並將挑選屬性設定。 因此，如果您想要讓通知使用不同的項目分隔符號，或是如果您想要讓通知使用 CR LF 中, 指定內容**partyb-> party a**  索引標籤。  
  
     在概念上，將會從傳送者與接收者辨識符號與在通知的內容屬性中所設定值相同的任一個單向協議索引標籤中挑選通知的屬性。 但為便於實際應用，通常會在您所建立由交換解析而成之協議的其他單向協議索引標籤中設定此屬性。  
  
-   如果您是 EDI 通知傳送至傳送原始交換的合作對象的合作對象，設定單向傳送埠以收取通知並傳送或雙向接收埠以傳送通知。 如需詳細資訊，請參閱[設定靜態傳送埠以傳送 EDI 交換和通知](../core/configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments.md)。  
  
-   如果您是預期收到 EDI 通知的合作對象，請設定雙向傳送埠或單向接收埠以接收通知。 如需詳細資訊，請參閱[設定連接埠來接收 EDI 訊息和通知](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md)。  
  
-   BizTalk EDI 應用程式包含控制結構描述。 因此，包含 EDI 解決方案的應用程式必須包含 BizTalk EDI 應用程式的參考。 如需詳細資訊，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-request-an-acknowledgment-for-the-party-that-sent-the-original-interchange"></a>為傳送原始交換的合作對象要求通知回覆  
  
1.  > [!NOTE]
    >  透過執行此程序中的步驟，您可以設定傳送交換的合作對象預期收到通知回覆。  
  
     在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象**節點。 在**合作對象與商務設定檔**頁面上，按一下您要啟用通知的協議的合作對象。 在**協議**區段頁面上，以滑鼠右鍵按一下 在協議，按一下**屬性**。 在**協議屬性** 對話方塊中單向協議索引標籤上 （要輸入的交換將解析），執行下列動作：  
  
    1.  在**識別碼**頁面上，輸入的值傳送者和接收者辨識符號。  
  
         對於 X12 編碼的通知，輸入 ISA5、ISA6、ISA7 與 ISA8 的值。 對於 ISA5 與 ISA6，輸入將傳送交換之合作對象的值。 對於 ISA7 與 ISA8，輸入將接收交換之合作對象的值。  
  
         對於 EDIFACT 編碼的通知，輸入 UNB2.1、UNB2.2、UNB3.1 與 UNB3.2 的值。 對於 UNB2.1 與 UNB2.2，輸入將傳送交換之合作對象的值。 對於 UNB3.1 與 UNB3.2，輸入將接收交換之合作對象的值。  
  
    2.  在**通知**頁面上，選取 屬性定義的傳送者合作對象預期之通知種類：  
  
         對於 X12 通知，選取**預期 TA1**及/或**預期 997**應根據哪一個通知。 每個通知類型 選取**不要批次處理\<通知類型\>** 如果您想要當做個別的交換傳送通知的每個執行個體。  
  
         對於 EDIFACT 通知選取**訊息回條 (CONTRL 必須是)** 及/或**通知 (CONTRL) 必須是**應根據哪一個通知。 每個通知類型 選取**不要批次處理\<通知類型\>** 如果您想要當做個別的交換傳送通知的每個執行個體。  
  
    3.  在**本機主機設定**頁面**交換設定**區段中，清除**通知的路由設定為傳送管線在要求-回應接收埠**傳回以非同步方式透過單向傳送埠的通知。 讓此屬性維持選取狀態，則會透過雙向接收埠同步傳回通知。  
  
    4.  在**傳送埠**頁面上，於**名稱**資料行**傳送埠**方格中，選取您已設定來傳送通知的傳送埠。  
  
        > [!NOTE]
        >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用此傳送埠設定判斷處理訊息時要使用的合作對象。 如需詳細資訊，請參閱[協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)。  
  
        > [!NOTE]
        >  如果您尚未設定傳送埠，則稍後再執行此步驟。  
  
### <a name="to-configure-how-the-party-sends-the-acknowledgement-back"></a>設定合作對象傳回通知的方式  
  
1.  > [!NOTE]
    >  透過執行此程序中的步驟，您可以設定收到交換的合作對象傳送通知回覆的方式。  
  
     在同一個**協議屬性**對話方塊中的，在其他單向協議索引標籤上，執行下列動作：  
  
    1.  在**識別碼**頁面上，輸入的值傳送者和接收者辨識符號。  
  
        > [!NOTE]
        >  傳送通知時，收到原始交換的合作對象會變成傳送者，而傳送原始交換的合作對象則會變成接收者。 因此，您現在於 [識別碼] 頁面所輸入的值，會與您在上一個步驟的單向協議索引標籤中輸入的值相反。 這有兩個目的：  
        >   
        >  -   目前所傳回的通知將解析成您正在建立的這個單向協議，因為通知的傳送者與接收者內容屬性，將與您現在於 [識別碼] 頁面中輸入的傳送者與接受者值相符。  
        > -   您可以在此協議索引標籤中設定要在通知中包含的自訂屬性。例如，您可以使用其他分隔符號，或是選擇啟用 CR LF 等。  
  
         對於 X12 編碼的通知，輸入 ISA5、ISA6、ISA7 與 ISA8 的值。 對於 ISA5 與 ISA6，輸入將傳送通知之合作對象的值 (與收到原始交換的合作對象相同)。 對於 ISA7 與 ISA8，輸入將接收通知之合作對象的值 (與傳送原始交換的合作對象相同)。  
  
         對於 EDIFACT 編碼的通知，輸入 UNB2.1、UNB2.2、UNB3.1 與 UNB3.2 的值。 對於 UNB2.1 與 UNB2.2，輸入將傳送的通知 （這會與收到原始交換的合作對象相同） 的合作對象的值。 對於 UNB3.1 與 UNB3.2，輸入將接收通知之合作對象的值 (與傳送原始交換的合作對象相同)。  
  
    2.  對於 X12 或 EDIFACT 通知，如有需要，在**字元集和分隔符號** 頁面上，指定您想要在通知中使用的分隔符號。 您也可以指定通知是否需使用 CR LF 尾碼。  
  
    3.  對於 EDIFACT 通知，如有需要，在**信封**頁面**交換設定**區段中，指定通知是否會包含 UNA 或 UNG 區段，選取適當的選項。  
  
## <a name="see-also"></a>請參閱  
 [設定 EDI 通知](../core/configuring-edi-acknowledgments.md)   
 [EDI 服務和控制結構描述](../core/edi-service-and-control-schemas.md)   
 [傳送 EDI 通知](../core/sending-an-edi-acknowledgment.md)   
 [如何建立接收埠](../core/how-to-create-a-receive-port.md)   
 [如何建立傳送埠](../core/how-to-create-a-send-port2.md)