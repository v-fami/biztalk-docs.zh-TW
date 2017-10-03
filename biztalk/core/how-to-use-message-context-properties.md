---
title: "如何使用訊息內容屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, building
- building, insufficient configuration
ms.assetid: 6ca95017-74e0-42d7-befa-93e0c1e1ecd1
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f5e222567c60596f572412bdcae9aadf6025ee0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-message-context-properties"></a>如何使用訊息內容屬性
系統屬性大多數都是由「BizTalk 傳訊引擎」及其元件在內部使用。 一般而言，不建議變更引擎所設定的屬性值，因為這可能會影響引擎的執行邏輯。 但是，您仍然可以變更許多屬性。  
  
 下表包含「傳訊引擎」可升級的訊息內容屬性清單。 您可以使用這些屬性來建立篩選條件運算式傳送埠和協調流程中 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 例如，  
  
```  
PortName = MyMessage(BTS.ReceivePortName);  
MyFileName = MyMessage(BTS.ReceivedFileName);  
MySubject= MyMessage(POP3.Subject);  
```  
  
 另一份表格列出可能會在某些無法升級之 BizTalk 應用程式中使用的其他屬性。  
  
|屬性|升級的時機和位置|類型|Description|  
|--------------|-----------------------------------|----------|-----------------|  
|BTS.AckFailureCategory|在發佈通知訊息至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:int|識別**ErrorCategory**，可讓和暫止的原因。|  
|BTS.AckFailureCode|在發佈通知訊息至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:string|識別**ErrorCode**，可讓和暫止的原因。|  
|BTS.AckID|在發佈通知訊息至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:string|識別**MessageID**原始訊息。|  
|BTS.AckInboundTransportLocation|在發佈通知訊息至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:string|識別**InboundTransportLocation**原始訊息。|  
|BTS.AckOutboundTransportLocation|在發佈通知訊息至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:string|識別**OutboundTransportLocation**原始訊息。|  
|BTS.AckOwnerID|在發佈通知訊息至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:string|識別原始訊息的執行個體識別碼。|  
|BTS.AckReceivePortID|在發佈通知訊息至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:string|識別**ReceivePortID**原始訊息。|  
|BTS.AckReceivePortName|針對通知訊息，「傳訊引擎」會升級此屬性。|xs:string|識別**ReceivePortName**原始訊息。|  
|BTS.AckSendPortID|在發佈通知訊息至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:string|識別**SendPortID**原始訊息。|  
|BTS.AckSendPortName|在發佈通知訊息至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:string|識別**SendPortName**原始訊息。|  
|BTS.AckType|在發佈通知訊息至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:string|允許協調流程監控通知和非通知。 值 ACK 表示通知，值 NACK 表示負值通知。|  
|BTS.ActionOnFailure|在呼叫 IBTTTransportBatch::SubmitMessage() API 以提交訊息至 BizTalk 之前，配接器會設定此屬性。|xs:int|在接收管線失敗時，控制傳訊引擎的行為。 通常傳訊引擎會擱置失敗的訊息，但特定配接器 (如 HTTP) 會向用戶端回報失敗，而不會在接收管線失敗時擱置訊息。<br /><br /> 有效值：<br /><br /> -預設值。 如果屬性不存在，傳訊引擎會自動嘗試擱置訊息。<br />-   0. 表示傳訊引擎不應自動擱置引擎。<br /><br /> 保留其他值供以後使用。|  
|BTS.CorrelationToken|如果在訊息內容上設定這個屬性，「傳訊引擎」就會將它升級。 當要求-回應配接器或協調流程提交要求訊息至 MessageBox 資料庫時，會在內容上隱含設定這個屬性。|xs:string|啟用回應至要求-回應埠的路由。|  
|BTS.EpmRRCorrelationToken|在要求-回應訊息執行時，「傳訊引擎」會升級此屬性。 在訊息提交至 MessageBox 資料庫之前，會升級此屬性。|xs:int|「傳訊引擎」在內部使用此屬性。 指定要求回應訊息資料流的伺服器名稱、程序識別碼和唯一 GUID。|  
|BTS.InboundTransportLocation|從接收配接器接收訊息之後，並且在發佈至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:string|指定處理常式收到此訊息的所在位置 (URI)。|  
|BTS.InboundTransportType|從接收配接器接收訊息之後，並且在發佈至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:string|指定收到此訊息並提交至伺服器的配接器類型： 檔案、 HTTP 等等。|  
|BTS.InterchangeSequenceNumber|從接收配接器接收訊息之後，並且在發佈至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:int|表示交換中文件的序號。 如果文件不解譯為個別文件的一部分，這個值會是交換的 1。 屬性可以讀取在協調流程時，傳送管線和傳送配接器。|  
|BTS.IsDynamicSend|此屬性可以在訊息內容上設定。 它將不會升級，而且只適用於傳送作業。|xs:boolean|當傳送作業在動態傳送埠上執行時，此屬性會以 true 的值由傳訊引擎寫入訊息內容。 如果您想要在傳送管線中以動態方式設定靜態傳送埠的屬性，就必須將此值設定為 true。|  
|BTS.MessageDestination|當解譯器管線元件從 GetNext() 傳回訊息時，它會在接收管線中設定此屬性。|xs:string|主要用來支援解譯器的「可復原交換處理」，這個屬性會控制訊息應發佈至 MessageBox 還是擱置於擱置序列中。 如果管線在交換中遇到損壞的訊息，而要擱置訊息並繼續處理，它可以設定 MessageDestination = SuspendQueue，並在引擎呼叫解譯器上的 GetNext() 時傳回訊息。<br /><br /> 有效值：<br /><br /> -預設值。 如果屬性不存在，就會將訊息視為正常並發佈至 MessageBox。<br />-SuspendQueue。 指示傳訊引擎擱置訊息。 **注意：**後管線/對應訊息而不是配接器 （即 wire 訊息） 提交訊息，將會擱置的訊息。|  
|BTS.MessageType|在訊息剖析期間，解譯器管線元件會升級此屬性。|xs:string|指定訊息的類型。 訊息類型定義為文件結構描述命名空間與文件根節點的串連： http://\<*MyNamespace*>#\<*MyRoot*>。|  
|BTS.OutboundTransportLocation|如果在訊息內容上設定這個屬性，「傳訊引擎」就會將它升級。 當協調流程將訊息傳送至傳送埠時，會在訊息內容上隱含設定這個屬性。 這個屬性也可以在協調流程或管線中明確設定。|xs:string|指定傳送訊息的目的地位置 URI。 URI 可以包含配接器前置詞，例如**http://**。 「傳訊引擎」會使用配接器前置詞，決定要在傳送訊息時使用的配接器類型。 如果這兩個配接器前置詞和**BTS。OutboundTransportType**屬性已設定，將配接器類型從**BTS。OutboundTransportType**優先順序一定高於從前置詞判定的配接器類型。<br /><br /> 有效值：<br /><br /> BizTalk 訊息佇列： **DIRECT =**，**私人 =**，和**公用 =**<br /><br /> 檔案： **file://**<br /><br /> FTP: **FTP: / /**<br /><br /> HTTP: **http://**和**https://**<br /><br /> SMTP: **mailto:**<br /><br /> SOAP: **SOAP: / /**<br /><br /> SQL: **SQL: / /**|  
|BTS.OutboundTransportType|如果在訊息內容上設定這個屬性，「傳訊引擎」就會將它升級。 當協調流程將訊息傳送至傳送埠時，會在內容上隱含設定這個屬性。 這個屬性也可以在協調流程或管線中明確設定。|xs:string|指定用來傳送訊息的配接器類型。 可用的配接器類型為**檔案**， **FTP**， **HTTP**， **SMTP**， **SOAP**，和**SQL**。<br /><br /> 這個屬性的值和位址中指定的配接器前置詞都不區分大小寫。|  
|BTS.PropertiesToUpdate|需要保留正在重新提交或擱置之失敗訊息的一些屬性值時，配接器會設定這個屬性。<br /><br /> 這表示，在重新提交或繼續訊息時，訊息會在內容設定指定的屬性。|xs:string|包含表示屬性名稱、命名空間和值之項目的 XML 字串。|  
|BTS.ReceivePortID|從接收配接器接收訊息之後，並且在發佈至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:int|識別收到此訊息的接收埠。|  
|BTS.ReceivePortName|從接收配接器接收訊息之後，並且在發佈至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:string|收到此訊息之接收埠的易記名稱。|  
|BTS.RouteDirectToTP|針對回送或要求-回應執行的訊息，「傳訊引擎」會升級此屬性。 在訊息提交至 MessageBox 資料庫之前，會升級此屬性。|xs:boolean|「傳訊引擎」會在內部使用此屬性，以啟用回送和要求-回應的實例。|  
|BTS.SPGroupID|從協調流程將訊息傳送至傳送埠時，「傳訊引擎」會升級此屬性。|xs:string|指定傳送埠群組的識別碼。|  
|BTS.SPID|從協調流程將訊息傳送至傳送埠時，「傳訊引擎」會升級此屬性。|xs:string|指定傳送埠的識別碼。|  
|BTS.SPName|從請求-回應傳送埠發佈回應訊息時，由傳訊引擎升級。|xs:string|用於訂閱從請求-回應傳送埠的回應訊息。 值為傳送埠的名稱。|  
|BTS.SPTransportBackupID|從協調流程將訊息傳送至傳送埠時，「傳訊引擎」會升級此屬性。|xs:string|指定傳送埠中備份配接器的識別碼。|  
|BTS.SPTransportID|從協調流程將訊息傳送至傳送埠時，「傳訊引擎」會升級此屬性。|xs:string|指定傳送埠中主要配接器的識別碼。|  
|BTS.SuspendAsNonResumable|在呼叫 SubmitMessage() 之前，配接器會設定這個屬性；或在將訊息傳送至傳送埠之前，會在協調流程中設定這個屬性。 **注意：** submitrequestmessage （） 將會忽略此屬性; 雙向訊息永遠擱置為不可繼續。|xs:boolean|控制「訊息引擎」在訊息失敗時是否應該擱置訊息為不可繼續。 通常訊息會擱置為可繼續，但有時候這並不適當，例如，對排序的傳送或接收埠，繼續訊息會中斷訊息順序。<br /><br /> 有效值：<br /><br /> -為 false。 訊息擱置為可繼續 (這是預設值)。<br />-為 true。 訊息擱置為不可繼續。|  
|BTS.SuspendMessageOnRoutingFailure|從接收配接器接收訊息之後，並且在發佈至 MessageBox 資料庫之前，「傳訊引擎」會升級此屬性。|xs:boolean|指定內送訊息發生路由失敗時的行為。<br /><br /> 有效值：<br /><br /> -Default / False。 如果此屬性不存在或設為 False，引擎會在發生路由失敗時向配接器通知錯誤。<br />-為 true。 在發生路由失敗時，路由引擎會自動擱置訊息。 **注意：**後管線/對應訊息而不是配接器 （即 wire 訊息） 提交訊息，將會擱置的訊息。|  
  
 這個命名空間中有些其他屬性所含的資訊，對某些 BizTalk 應用程式可能會有幫助。  
  
|屬性|升級的時機和位置|類型|Description|  
|--------------|-----------------------------------|----------|-----------------|  
|BTS.AckDescription|在發佈通知訊息至 MessageBox 資料庫之前，「傳訊引擎」會設定此屬性。|xs:string|識別**ErrorDescription**，可讓和暫止的原因。|  
|BTS.EncryptionCert|無法升級。|xs:int|識別對應至加密憑證的指紋。 在協調流程中，或在管線內 MIME/SMIME 編碼器管線元件之前的自訂管線元件中，設定這個屬性，以便在接收已簽章和已加密訊息的要求-回應連接埠上執行回應加密。|  
|BTS.InterchangeID|針對到達伺服器的每個訊息，「傳訊引擎」會設定此屬性。|xs:string|定義用來群組相同的交換訊息所產生的文件的唯一識別碼。|  
|BTS.Loopback|在提交回送執行的要求訊息時，配接器會設定此屬性。|xs:boolean|定義是否應提交訊息至伺服器以執行回送作業。 在回送執行程序中，要求訊息會發佈至 MessageBox 資料庫中，並在其中當做回應直接傳送至接收配接器。|  
|BTS.SignatureCertificate|在提交訊息至伺服器時，有些配接器會設定此屬性。 「合作對象解析」管線元件會使用這個屬性。|xs:string|識別簽章憑證的指紋，此簽章憑證已用於簽署 BizTalk Server 收到的訊息。|  
|BTS.SourcePartyID|在識別內送訊息的合作對象之後，「合作對象解析」管線元件會設定此屬性。|xs:string|BizTalk 合作對象的識別碼。|  
|BTS.SSOTicket|如果接收配接器支援這個屬性，則會在發佈訊息至伺服器時設定它。|xs:string|票證包含目前使用者的加密網域和使用者名稱，以及票證到期時間。 已啟用 SSO 的配接器向目的地端點驗證時，會使用此票證取得使用者認證。|  
|BTS.WindowsUser|在提交訊息至伺服器時，有些配接器會設定此屬性。 「合作對象解析」管線元件會使用這個屬性。|xs:string|指定訊息以此使用者帳戶提交至伺服器。|  
  
 如需與管線元件和配接器相關聯之屬性和屬性結構描述的詳細資訊，請參閱下列主題：  
  
-   [File 配接器屬性結構描述和屬性](../core/file-adapter-property-schema-and-properties.md)
  
-   [FTP 配接器屬性結構描述和屬性](../core/ftp-adapter-property-schema-and-properties.md)  
  
-   [HTTP 配接器屬性結構描述和屬性](../core/http-adapter-property-schema-and-properties.md)  
  
-   [MSMQ 配接器屬性結構描述和屬性](../core/msmq-adapter-property-schema-and-properties.md)  
  
-   [SMTP 配接器屬性結構描述和屬性](../core/smtp-adapter-property-schema-and-properties.md)  
  
-   [SOAP 配接器屬性結構描述和屬性](../core/soap-adapter-property-schema-and-properties.md)  
  
-   [BizTalk Framework 結構描述和屬性](../core/biztalk-framework-schema-and-properties.md)  
  
-   [MQSeries 配接器屬性](../core/mqseries-adapter-properties.md)  
  
-   [POP3 配接器屬性結構描述和屬性](../core/pop3-adapter-property-schema-and-properties.md)  
  
-   [Windows SharePoint Services 配接器屬性參考](../core/windows-sharepoint-services-adapter-properties-reference.md)  
  
-   [MIME/SMIME 屬性結構描述和屬性](../core/mime-smime-property-schema-and-properties.md)  
  
-   [XML 和一般檔案屬性結構描述與屬性](../core/xml-and-flat-file-property-schema-and-properties.md)  
  
## <a name="see-also"></a>另請參閱  
 [關於 BizTalk 訊息內容屬性](../core/about-biztalk-message-context-properties.md)   
 [如何使用運算式來將值指派給動態連接埠](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md)