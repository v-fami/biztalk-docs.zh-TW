---
title: "傳送 EDI 通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a036d08-8a65-43ad-b72c-2a246d302792
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a47a3fbe13f4cf054b6114050b8777231c4b217
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sending-an-edi-acknowledgment"></a>傳送 EDI 通知
通知可指示 EDI 訊息傳輸的狀態。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 收到 EDI 交換後，依據啟用的通知而定，會傳回一或多個通知給 EDI 交換的寄件者。  
  
 根據驗證層級而定，EDI 訊息通知可分成兩種：  
  
-   A**技術通知**標頭驗證之後產生。 技術通知會報告位址接收者對交換標頭和結尾的處理狀態。  
  
-   A**功能通知**主體驗證之後產生。 它會報告處理所接收文件時遇到的每個錯誤。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以傳回技術與功能通知以回應單一交換。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳回每個交換一個技術通知。 對於 X12 交換，它會為每個收到的群組傳回一個功能通知。 對於 EDIFACT 交換，無論交換包含多少個群組，它只會為每個交換傳回一個功能通知。  
  
## <a name="x12-acknowledgments"></a>X12 通知  
 **X12 技術通知**  
  
 如果 X12 訊息的 ISA 標頭和 IEA 結尾有效 (不管其他內容如何)，即會傳送正值 TA1 通知。 如需內容 TA1 通知的詳細資訊，請參閱[X12 TA1 通知](../core/x12-ta1-acknowledgment.md)。  
  
 **X12 功能通知**  
  
 997 通知是用來通知收到交換或功能群組、接受或拒絕一或多個功能群組或交易，或驗證和報告是否符合標準。 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 收到含有多個群組的交換，它會為每個群組傳回一個通知。 如果群組包含多個交易集，依據是否針對接受的交易集產生 AK2 迴圈而定，該群組的通知將會包含多個 AK2 迴圈 (每個交易集一個)。 多個內容 997 通知的詳細資訊，請參閱[X12 997 通知](../core/x12-997-acknowledgment.md)。  
  
> [!NOTE]
>  當 EDI 接收管線建立 X12 功能通知的「功能群組標頭」(GS) 區段時，會從接受通知的功能群組擷取「應用程式傳送者代碼」(GS02) 和「應用程式接收者代碼」(GS03)。 不過，內送訊息的 GS02 會對應至通知的 GS03，而內送訊息的 GS03 會對應至通知的 GS02。  
  
## <a name="edifact-acknowledgments"></a>EDIFACT 通知  
 **EDIFACT 技術通知**  
  
 對 EDIFACT 來說，不會使用單獨的技術通知，但接收通知會重複使用功能通知或 CONTRL 通知 (請參閱下文) 的區段。 這就相當於技術通知。  
  
 如需技術 CONTRL 通知的詳細資訊，請參閱[EDIFACT CONTRL 訊息為技術通知](../core/edifact-contrl-message-as-technical-acknowledgment.md)。  
  
 **EDIFACT 功能通知**  
  
 對 EDIFACT 來說，功能 CONTRL 通知是用來通知收到交換、群組和訊息、接受或拒絕收到的交換、群組和訊息，以及列出任何語法錯誤或其中包含的不受支援功能。 CONTRL 通知會報告針對完整接收的交換進行語法檢查的結果。  
  
 如需功能 CONTRL 通知的詳細資訊，請參閱[EDIFACT CONTRL 訊息做為功能通知](../core/edifact-contrl-message-as-functional-acknowledgment.md)。  
  
## <a name="when-an-acknowledgment-is-generated"></a>產生通知的時機  
 如果符合下列任一條件，EDI 接收管線將會產生通知：  
  
-   所接收交換中的資料項目提示通知。 對於 X12 編碼訊息，接收管線會產生技術 TA1 通知，如果 ISA14 資料項目設定為 1。 對於 EDIFACT 編碼訊息，接收管線會產生技術 CONTRL 通知，如果 UNB9 資料項目設定為 2，而且它會產生功能 CONTRL 通知，如果 UNB9 資料項目設定為 1。  
  
-   協議屬性提示通知。 對於 X12 交換，這些屬性是**預期 TA1**和**預期 997**中的屬性**通知**雙向協議索引標籤頁面**協議屬性** 對話方塊。 對於 EDIFACT 交換，這些屬性是**訊息回條 (CONTRL 必須是)**和**通知 (CONTRL) 必須是**中**通知**頁面雙向協議索引標籤的**協議屬性** 對話方塊。 若啟用一種通知，您也可以指定是否要批次處理該類型的通知。  
  
-   如果無法判斷交換的協議，全域屬性會提示通知。 這些屬性是：  
  
    -   **預期 TA1**和**預期 997**中的屬性**通知**協議索引標籤的頁面**X12 後援設定** 對話方塊。  
  
    -   **訊息回條 (CONTRL 必須是)**和**通知 (CONTRL) 必須是**中**通知**協議索引標籤的頁面**EDIFACT 後援設定** 對話方塊。  
  
 針對 EDIFACT，如果同時提示技術通知和功能通知，EDI 接收管線會傳回兩個個別 CONTRL 通知。 技術 CONTRL 通知只包含接收通知資訊， 功能 CONTRL 通知則同時包含接收資訊和功能通知資訊。 如需詳細資訊，請參閱[EDIFACT CONTRL 通知](../core/edifact-contrl-acknowledgment.md)。  
  
## <a name="identifying-an-acknowledgment-with-a-control-number"></a>識別含有控制編號的通知  
 每個通知都必須以 X12 的交易集控制編號 (ST2 資料項目) 或 EDIFACT 的交易集參考編號 (UNH1 資料項目) 來識別。 如果為外寄通知設定協議，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將依下列原則，將交易集控制或參考編號設為針對協議所設定的值：  
  
-   **對於 X12 通知**– (**ACK 控制編號 (ST02)**屬性**本機主機設定**頁面 (**接收者的設定**> 一節) 協議索引標籤中**協議屬性**對話方塊  
  
-   **對於 EDIFACT 通知**– (**Edifact Ack 控制編號**屬性**本機主機設定**頁面 (**接收者的設定**區段) 的協議索引標籤中的**協議屬性**對話方塊  
  
 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]無法判斷協議的通知，就會使用相同的屬性，為上面所述但協議索引標籤上可用**X12 後援設定**ad **EDIFACT 後援設定**對話方塊。 如果同時設定技術和功能通知，這個設定會同時套用到兩者。 每產生一個通知或交換，此整數編號就會遞增 1。  
  
 通知的信封是根據通知控制結構描述，從所收到訊息中的資料建立。  
  
## <a name="preparing-the-acknowledgment"></a>準備通知  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 建立通知信封的方式與建立訊息信封的方式一樣，都是查看「交換控制標頭」和「功能群組標頭」的定義。 如需詳細資訊，請參閱[協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)。  
  
 為使產生的通知 (TA1、997 或 CONTRL) 能順利路由傳送，「EDI 解譯器」會在通知中填入 `DestinationPartyReceiverQualifier`、`DestinationPartyReceiverIdentifier`、`DestinationPartySenderQualifier` 和 `DestinationPartySenderIdentifier` 屬性。  
  
## <a name="synchronous-and-asynchronous-acknowledgments"></a>同步和非同步通知  
 您可以選擇同步或非同步傳送 EDI 通知。 如果選擇同步傳送，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將通知直接路由傳送至雙向要求-回應接收埠的傳送管線。 如果選擇非同步傳送，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將通知路由傳送至 MessageBox，再由傳送埠訂閱該訊息。  
  
 若要指定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]同步執行，選取 將通知傳送**通知的路由設定為傳送管線在要求-回應接收埠**中**本機主機設定**頁面 (**接收者的設定**> 一節) 下**交換設定**雙向協議索引標籤 （適用於 X12 和 EDIFACT 協議） 中。 如果清除此屬性，則必須設定雙向接收埠的傳送管線，才能傳回 EDI 交換。  
  
 如果使用要求-回應接收埠，而且同時啟用了技術通知和功能通知，則技術通知會以同步方式傳回，而功能通知會以非同步方式傳回。  
  
 當透過 HTTP/HTTPS 接受 EDIINT/AS2 編碼訊息時，如果 (對相同的通訊端) 送出 MDN 以回應 MIME 包裝的 EDI 內容，則不會以同步方式送出 EDI 通知。 如果在此情況下**通知的路由設定為傳送管線在要求-回應接收埠**會檢查屬性，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會忽略此屬性。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 通知結構](../core/edi-acknowledgment-structure.md)   
 [EDI 服務和控制結構描述](../core/edi-service-and-control-schemas.md)   
 [X12 TA1 通知](../core/x12-ta1-acknowledgment.md)   
 [X12 997 通知](../core/x12-997-acknowledgment.md)   
 [EDIFACT CONTRL 通知](../core/edifact-contrl-acknowledgment.md)   
 [EDIFACT CONTRL 訊息為技術通知](../core/edifact-contrl-message-as-technical-acknowledgment.md)   
 [EDIFACT CONTRL 訊息做為功能通知](../core/edifact-contrl-message-as-functional-acknowledgment.md)