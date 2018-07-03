---
title: 協議解析和外寄 EDI 訊息的結構描述判斷 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e37aeb9d-1e95-464d-bb71-73653c1d4674
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a718f386686b8a23bc8c97108b94b5fba717ee90
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992023"
---
# <a name="agreement-resolution-and-schema-determination-for-outgoing-edi-messages"></a>外寄 EDI 訊息的協議解析和結構描述判斷
若要產生給交易夥伴的 EDI 訊息，EDI 傳送管線必須執行下列動作：  
  
-   判斷訊息會解析為的協議  
  
-   判斷要用來驗證訊息的結構描述  
  
## <a name="agreement-resolution"></a>協議解析  
 EDI 傳送管線會執行一系列的步驟來執行協議尋查，以判斷外寄交換和協議屬性之間是否相符。 一旦 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 判斷出協議，就會決定套用到交換的文件結構描述 (請參閱下文)。 它會使用與相符協議關聯的屬性和相關的結構描述，產生及驗證外寄訊息。  
  
 為執行協議解析，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行的步驟如下：  
  
1. 比對 AgreementPartIDForSend 內容屬性與單向協議的識別碼，以解析協議。 此屬性應該為整數類型，您可以在自訂元件中加以設定；這不是由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定。  
  
2. 如果步驟 1 未成功，則比對下列三個內容屬性與協議屬性，以解析協議：AgreementNameForSend、SenderPartyNameForSend、ReceiverPartyNameForSend。 請注意，這三個屬性必須全都已設定好，才能成功解析為協議。 您可以在自訂元件中設定這些屬性；這並不是由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定。  
  
3. 如果步驟 2 未成功，則在比對訊息內容屬性設定為其他的協議解析程式中的 DestinationPartyName 屬性中的合作對象名稱解析協議**識別碼** 索引標籤協議屬性。  
  
4. 如果步驟 3 未成功，則比對訊息內容中與協議屬性中的下列屬性，以解析協議：DestinationPartySenderIdentifier、DestinationPartySenderQualifier、DestinationPartyReceiverIdentifier 和 DestinationPartyReceiverQualifier。 請注意，這四個屬性必須全都已設定好，才能成功解析為協議。 您可以在自訂元件中設定這些屬性；這並不是由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定。 如需詳細資訊，請參閱下面。  
  
   > [!NOTE]
   >  如果有任何上述內容屬性升級，而 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 找不到與這些內容屬性關聯的協議，則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會擱置訊息。  
   > 
   >  如果使用者刻意撰寫一組內容屬性來協助解析協議，而解析程式無法識別 OnewayAgreement，則會擱置訊息。 無法根據一組內容屬性來解析協議時，EventLog 中會擲回對應的警告訊息。  
  
5. 如果步驟 4 不成功，或上述內容屬性都未升級，則會將訂閱訊息的傳送埠與和協議關聯的傳送埠比對，將 EDI 訊息解析為協議。  
  
   > [!NOTE]
   >  如果同一個傳送埠與多個協議相關聯，則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會產生錯誤。  
  
6. 如果在步驟 1、2、3 或 4 中找不到協議，傳送管線會使用後援協議設定來產生外寄訊息。  
  
   **比對傳送者和接收者內容屬性的協議解析**  
  
   在上述步驟 2 中，比對作業所使用的四個內容屬性為 EDI.DestinationPartySenderIdentifier、EDI.DestinationPartySenderQualifier、EDI.DestinationPartyReceiverIdentifier 和 EDI.DestinationPartyReceiverQualifier。 這些內容屬性的命名空間是 `http://schemas.microsoft.com/Edi/PropertySchema`。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會嘗試比對這些值相關的寄件者和接收者識別碼和在單向協議屬性中的限定詞。 對於 X12，這些欄位是 ISA05 ISA06、 ISA07 和 ISA08，在**識別碼**單向協議索引標籤中的頁面**協議屬性**對話方塊中，對於 EDIFACT，這些欄位是 UNB2.1、 UNB2.2，UNB3.1 和 UNB3.2 中的**識別碼**單向協議索引標籤中的頁面**協議屬性** 對話方塊。  
  
   若要使用全部四個傳送者和接收者識別碼和辨識符號來解析傳送端協議，必須設定全部這四個內容屬性。 這樣就會唯一識別協議。 使用這個協議尋查方法，您在傳送端處理方面就可擁有更大的彈性。 例如，這個方法可避免您在某些狀況下建立多個傳送埠，以及避免使用複雜的傳送埠篩選條件。 視需要，也可以避免設定 OneWayAgreementId 屬性。  
  
   如果已為訊息設定全部的四個內容屬性，而這些內容屬性與合作對象屬性完全不符，訊息就會遭到擱置。 只有在未設定全部四個內容屬性時，才會使用與協議相關聯的傳送埠來解析協議。  
  
> [!NOTE]
>  EDI 管線中的訊息會進入協議解析的後續步驟，直到訊息在協議為啟用狀態的步驟中獲得解析為止。 例如，如果訊息在協議解析的第一個步驟獲得解析，但協議處於停用狀態，則訊息會進入後續解析步驟。  
  
## <a name="schema-determination"></a>結構描述判斷  
 EDI 傳送管線會根據每個交易集的中繼 XML 檔案中包含的結構描述名稱和結構描述命名空間 (做為文件類型資訊或在根節點中)，判斷套用至訊息的結構描述。  
  
 對於已經保留的交換，傳送管線會針對整個交換，使用中繼 XML 檔案之個別交易集中的文件類型資訊。 它會使用控制區段結構描述來處理信封區段。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何傳送 EDI 訊息](../core/how-biztalk-server-sends-edi-messages.md)