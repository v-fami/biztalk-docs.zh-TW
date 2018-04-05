---
title: 使用失敗訊息路由 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.ops.tsroutingfailure
ms.assetid: d081934c-600e-44ce-8ba4-fb646d494589
caps.latest.revision: 33
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af6d006aeebd5e2a5f8625a994c8a6f9b0cb6f6a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-failed-message-routing"></a>使用失敗訊息路由
錯誤處理機制可讓設計師指定自動化的傳訊失敗處理方式，而不是依照傳統行為，將失敗的訊息放在已擱置佇列中 (現在的預設行為)。 此自動化處理將錯誤訊息路由至任何訂閱路由的目的地，像是傳送埠或協調流程。 錯誤訊息是原始訊息的複製，含有現在已降級之所有先前升級的屬性，以及已升級為訊息內容之與特定傳訊失敗相關的已選取屬性。  
  
> [!WARNING]
>  失敗的訊息包含原始訊息複本。 若原始訊息包含敏感性資訊，請設計手動和自動化失敗訊息程序，以避免它們意外洩漏。  
  
## <a name="what-does-failed-message-routing-consist-of"></a>失敗訊息路由包含哪些內容？  
 啟用失敗訊息路由時，BizTalk Server 不會擱置訊息，而是以路由訊息取代。 在接收埠和傳送埠上皆可啟用失敗訊息路由，結果如下：  
  
-   若在接收埠上啟用失敗訊息路由，且訊息在接收管線中或在路由時發生失敗，則會產生失敗的訊息。 當錯誤發生在解譯階段中或解譯階段前，則錯誤訊息為原始交換的複製。  
  
-   若在傳送埠上啟用失敗訊息路由，且訊息在傳送管線中發生失敗，則會產生失敗的訊息。  
  
 當失敗的訊息產生時，BizTalk Server 會升級錯誤報告相關的訊息內容屬性，並在發佈失敗的訊息之前降級一般訊息內容屬性。 此行為與未啟用失敗訊息路由時的下列預設行為不同：失敗的訊息會擱置。  
  
## <a name="what-kinds-of-messaging-failures-trigger-an-error-message"></a>哪些傳訊失敗會觸發錯誤訊息？  
 若啟用失敗訊息路由，則任何發生在配接器處理、管線處理、對應或訊息路由中的失敗，會導致錯誤訊息。 當傳訊錯誤發生在協調流程從接收埠接收或是傳送至傳送埠時，產生的錯誤訊息會與協調流程繫結的傳訊連接埠關聯。  
  
## <a name="subscribing-to-an-error-message"></a>訂閱錯誤訊息  
 錯誤訊息會傳遞到已訂閱要接收它們的協調流程或傳送埠。 訂閱一般會根據在其中發生傳訊錯誤的連接埠名稱 (傳送埠或接收埠) 來選取錯誤訊息。 訂閱也可能篩選其他升級至錯誤訊息內容的屬性 (例如， **[InboundTransportLocation]** 或 **[FailureCode]**)。  
  
## <a name="error-message-specification"></a>錯誤訊息規格  
 錯誤訊息是原始失敗訊息的複製，含有已降級之所有先前的升級屬性，以及一組已升級為訊息內容的錯誤特定屬性。 先前升級的屬性已降級，以避免非預期地傳遞給未被指定接收錯誤訊息的訂閱者。 錯誤訊息已發佈以供散佈給訂閱者 (協調流程、傳送埠以及傳送埠群組)。  
  
 升級至所有落在錯誤訊息內容屬性**ErrorReport** BizTalk Server 中的命名空間。 這些屬性如下所示：  
  
|屬性名稱|資料類型|已升級|描述|  
|-------------------|---------------|--------------|-----------------|  
|[FailureCode]|System.String|是|錯誤碼。 報告在 [BizTalk Server 管理] 主控台中的一個十六進位值。|  
|FailureCategory|System.Int32|是|不會使用此屬性。 未定義其值。|  
|描述|System.String|否|錯誤描述。 與寫入有關此傳訊失敗的應用程式事件記錄檔中之診斷文字相同的診斷文字。|  
|MessageType|System.String|是|若訊息類型未確定，則訊息類型為失敗的訊息或空白。<br /><br /> BizTalk Server 使用訊息類型為訊息與其 XML 結構描述建立關聯。 訊息類型是藉由串連結構描述命名空間與結構描述根節點所構成：http://mynamespace#rootnode。 **注意：**其訊息類型決定之前失敗，並沒有這個屬性的訊息設定。|  
|ReceivePortName|System.String|**[已升級]** ：若失敗發生在輸入處理期間 (在接收埠)<br /><br /> **[未升級]** ：若失敗發生在傳送埠。|失敗發生所在的接收埠名稱。|  
|[InboundTransportLocation]|System.String|**[已升級]** ：若失敗發生在輸入處理期間 (在接收埠)<br /><br /> **[未升級]** ：若失敗發生在傳送埠。|失敗發生所在的接收位置 URI。|  
|SendPortName|System.String|**[已升級]** ：若失敗發生在輸出處理期間 (在傳送埠)<br /><br /> **[未升級]** ：若失敗發生在接收埠。|失敗發生所在的傳送埠名稱。|  
|OutboundTransportLocation|System.String|**[已升級]** ：若失敗發生在輸出處理期間 (在傳送埠)<br /><br /> **[未升級]** ：若失敗發生在接收埠。|失敗發生所在的傳送位置 URI。|  
|ErrorType|System.String|是|指示錯誤包含的訊息類型。 此屬性永遠包含 **FailedMessage**這個值，表示錯誤包含原始失敗訊息。|  
|RoutingFailureReportID|System.String|是|此屬性提供 BizTalk Server 在發生路由失敗時所產生的路由失敗報告識別碼。 路由失敗報告是 BizTalk Server 產生並擱置的特殊訊息。 此訊息沒有內文，但是有失敗訊息的內容。 錯誤處理協調流程或傳送埠可以使用此識別碼查詢 MessageBox 資料庫並處理路由失敗報告。 例如，協調流程可能需要在取得失敗訊息之後終止路由失敗報告。|  
  
## <a name="handling-error-messages"></a>處理錯誤訊息  
 錯誤處理是由協調流程或傳送埠訂閱所指定，它們的篩選條件符合已經升級為錯誤訊息之訊息內容的屬性。  
  
## <a name="security-implications"></a>安全性影響  
 與原始訊息關聯的身分 (由接收管線的解析合作對象階段決定的初始身分或最終身分) 會指派給錯誤訊息。  
  
 限制訊息傳遞給授權的訂閱連接埠與協調流程之安全性機制，也適用於錯誤訊息。  
  
 訂閱錯誤訊息但未以適當解密憑證設定的傳送埠，不會收到因下列原因而產生的錯誤訊息：在原始訊息進入 BizTalk Server 所透過的接收管線之解密階段或該階段之前發生傳訊失敗。 相反的，失敗訊息會放置在已擱置佇列中。  
  
## <a name="adapter-messaging-failure"></a>配接器傳訊失敗  
 若配接器擱置訊息，則會發佈錯誤訊息。 若訊息未擱置，則不會產生錯誤訊息。  
  
## <a name="transactional-receive-pipelines"></a>交易式接收管線  
 若交易式接收管線擲回例外狀況 (指定應中止該交易)，則會中止交易，並發佈錯誤訊息。  
  
 若交易式接收管線明確地擱置訊息 (指定 MessageDestination = SuspendQueue)，則允許目前的交易繼續進行 (且可以將它認可，除非後續階段指定將它中止)，並發佈結果錯誤訊息。  
  
## <a name="solicit-response-send-ports"></a>請求-回應傳送埠  
 當協調流程傳送的要求訊息傳輸失敗或是此要求訊息的回應輸入處理失敗時，不論失敗訊息是否已路由，協調流程都會收到例外狀況。  
  
 在請求-回應傳送埠已連接至要求-回應接收埠的情況下，不論失敗訊息是否已路由，接收埠都會收到回應訊息 (若傳送成功) 或是收到 NACK (若傳輸失敗)。  
  
## <a name="one-way-send-ports"></a>單向傳送埠  
 當協調流程透過為傳遞通知設定的傳送埠傳送訊息時，不論錯誤訊息是否已路由，協調流程都會收到傳遞通知。 換句話說，即使連接埠在處理期間發生傳訊失敗，傳送埠還是會為協調流程產生傳遞通知。 通知會確認已傳遞至連接埠，但不會指出是否已透過連接埠成功處理。  
  
## <a name="resuming-suspended-messages"></a>繼續擱置的訊息  
 若輸入處理失敗 (也就是說，從接收配接器 (包含) 開始處理直到發佈 (但不包含發佈) 至 MessageBox) 且未處理其失敗的大部分訊息，會擱置為可繼續。 此例外狀況是來自雙向接收埠的要求訊息已擱置為不可繼續。  
  
 訊息通常以原始形式 (如同在管線處理之前的形式) 擱置，但有兩個例外狀況：  
  
-   **由管線元件擱置的訊息。** BizTalk Server 會以提供訊息給失敗管線元件時的相同形式來擱置這種類型的訊息。 繼續訊息時，它會從相同管線的開頭進行管線處理。 這表示在原始失敗發生階段之前的管線階段中之管線元件，必須準備以不同於它在先前處理該訊息之原始形式的形式來處理「相同」訊息。  
  
-   **從 可復原的訊息交換反組譯碼中之後路由失敗。** BizTalk Server 會以發佈訊息的相同形式來擱置這種類型的訊息。 這是訊息在管線執行 **之後** 的形式。 繼續訊息時，它會略過管線處理並直接發佈到 MessageBox 資料庫。  
  
## <a name="scenarios-leading-to-suspended-non-resumable-messages"></a>產生已擱置 (不可繼續) 訊息的案例  
 雖然訊息比較常擱置為可繼續，但仍有一些會造成不可繼續訊息的案例：  
  
-   在「排序的傳遞」傳送埠已啟用在失敗時繼續的情況下，如果管線、對應或傳輸中有失敗。  
  
-   在「排序的傳遞」接收埠中，如果配接器設為在失敗時不可繼續且擱置訊息。 例如，設定「失敗時」的 MSMQ 配接器設為「擱置 (不可繼續)」或 MQSeries 配接器已啟用「以不可繼續擱置」，失敗的訊息就會擱置為不可繼續。  
  
-   在雙向接收埠中，如果回應訊息在管線、對應或傳輸中失敗。  
  
-   在雙向接收埠中，如果接收訊息在管線、對應或傳輸中失敗。 個別的配接器行為可能有所不同。 例如，依預設值，HTTP 配接器不會擱置訊息，但可經由設定這樣做。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤處理](../core/error-handling.md)   
 [使用通知](../core/using-acknowledgments.md)   
 [訊息的排序傳遞](../core/ordered-delivery-of-messages.md)