---
title: "在 SAP Idoc 的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDOC, operations to receive an
- IDOCs
- IDOCs, operations on
- tRFC server
- IDOC, operations to send an
- RFC server
ms.assetid: 6abcc646-c7a3-48cf-a09e-01f516dcef97
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6a70e6bc4062a6c2865c9adb8f76d68a078e965
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-idocs-in-sap"></a>在 SAP Idoc 的作業
Idoc 是 SAP 支援以非同步方式進行通訊與 SAP 和非 SAP 系統的標準化的 EDI 類似文件。 Idoc 是用來傳送和接收"business"文件，例如銷售訂單，與交易夥伴的 SAP 系統或外部程式。  
  
 雖然 SAP 系統支援傳送和接收 Idoc 的連接埠類型的數字 (例如檔案連接埠，CPIC 連接埠)，則[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援傳送及接收 Idoc 透過 tRFC 連接埠。  
  
## <a name="operations-to-send-an-idoc"></a>傳送 IDOC 的作業  
 所有 SAP IDOC 呼叫會在內部都視為 tRFC 呼叫中的配接器做為 tRFC 用戶端，並呼叫中傳送 IDOC 到 SAP RFC。 如同其他任何 tRFC 用戶端呼叫，配接器用戶端會選擇性地將 GUID 傳遞至接著將它與交易識別碼 (TID)，它會在 SAP 系統上呼叫關聯的配接器。 （如果配接器用戶端未通過 GUID，配接器會產生其專屬 GUID。）GUID 會傳回到配接器中的用戶端的回應訊息。 配接器用戶端可以確認 TID SAP 系統上的使用此 GUID。 實際的叫用特殊的靜態方法，在 SAP 繫結也可以取得 tRFC 呼叫配接器使用的 SAP TID **ConvertGuidToTid**。 具有實際 TID 可能適用於 SAP 系統上的問題進行疑難排解。  
  
 呼叫之後傳送 IDOC 完成時，必須確認 TID SAP 系統上。 這可讓其資料庫中刪除 TID SAP 系統。 配接器用戶端可以確認 TID SAP 系統上。  
  
-   明確地藉由叫用**RfcConfirmTransID**介面卡上的作業。 這項作業會採用 GUID （上述的回應訊息中傳回），並造成配接器必須確認在 SAP 系統上相關聯的 TID。  
  
-   以隱含方式，是藉由設定**AutoConfirmSentIdocs**繫結屬性。 如果這個繫結屬性為 true，配接器會自動認可 TID 之後傳送 IDOC 到 SAP 系統。 請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)如需詳細資訊。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]用來傳送 IDOC 的下列 Rfc:  
  
-   INBOUND_IDOC_PROCESS。 使用此函式模組的 SAP 4.0 之前的版本。  
  
-   IDOC_INBOUND_ASYNCHRONOUS。 此函式的模組是用 SAP 版本 4.0 及更新版本。  
  
### <a name="sending-idocs-with-segment-data-across-multiple-lines"></a>傳送 Idoc 的區段資料跨多行  
 Idoc 被 constituted 的區段。 在 IDOC 一般檔案中的每個區段項目包含 （包含 DOCNUM 欄位） 的區段標頭資訊以及區段資料。 在某些 Idoc，區段資料可以分成多行。 例如：  
  
```  
Segment header (DOCNUM is one of the fields here)  |  Segment data  
Segment header (DOCNUM is one of the fields here)  |  Segment data  
Segment data wrapped from the previous line  
Segment header (DOCNUM is one of the fields here)  |  Segment data  
```  
  
 WCF 架構[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援傳送這類 Idoc 到 SAP 系統。 若要支援傳送這類的 Idoc，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]決定每個區段的資料是否接續前一個，或是否為新的分割資料。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]剖析每個區段標頭，並尋找 DOCNUM 欄位決定這。 如果區段資料會分成兩行，第二行沒有區段標頭，因此[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]找不到 DOCNUM 欄位。 因此，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可以判斷它是持續的前一個區段的資料。  
  
 如上所示，IDOC 的表示法，例如在[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]找不到任何 DOCNUM 欄位 」`Segment data wrapped from the previous line`"，而且可以決定這條線是持續的前一個區段的資料。 請考慮 IDOC 的大小一般檔案的實際執行環境中，執行這類檢查針對每個區段的資料可能會導致處理時間增加。  
  
> [!NOTE]
>  配接器會使用 DOCNUM 欄位，而不是歸位字元傳回換行字元 (CRLF) 來識別和擷取每個區段記錄從 IDOC 資料。 如果 DOCNUM 記錄中的欄位控制項和資料都是無效或部分空白，配接器無法剖析 IDOC。 因此，SAP 系統不會傳送 IDOC。  
  
### <a name="operations-to-send-an-idoc"></a>傳送 IDOC 的作業  
 傳送 Idoc 到 SAP 系統支援下列作業：  
  
-   **傳送**。 您可以使用這項作業傳送 IDOC 至 SAP 系統，使用強型別結構描述。 這項作業的結構描述會公開控制項記錄欄位和資料記錄欄位，包括區段標頭和區段欄位。 傳送作業是 IDocType + CimType + ReleaseNumber + 版本的特定組合。  
  
     這項作業會顯示每個 idoc，並適用於特定的 IDOC 節點中[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
    > [!NOTE]
    >  若要能夠順利執行**傳送**作業，您必須在 SAP 系統相關的授權。 如需詳細資訊，  
  
-   **SendIdoc**。 您可以使用這項作業傳送 IDOC 至 SAP 系統使用弱式型別的結構描述。 這項作業的結構描述會公開為單一字串欄位所組成的控制記錄和資料記錄的 Idoc。 SendIdoc 作業會做為參數的 IDOC 字串和 GUID。  
  
     這是單一作業中顯示所有 SAP 系統所公開的 Idoc，適用於根**IDOC**節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
 如需詳細資訊：  
  
-   傳送 IDOC 到 SAP 系統使用 BizTalk Server，請參閱[傳送 Idoc 到 SAP 使用 BizTalk server](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-biztalk-server.md)。  
  
-   傳送 IDOC 到 SAP 系統使用 WCF 服務模型，請參閱[傳送 Idoc 到 SAP 使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-the-wcf-service-model.md)。  
  
-   訊息結構和傳送 IDOC 的 SOAP 動作，請參閱[IDOC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)。  
  
## <a name="operations-to-receive-an-idoc"></a>接收 IDOC 的作業  
 若要接收 IDOC，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]行為會視做為 tRFC 伺服器或 RFC 伺服器：  
  
-   配接器做為 tRFC 伺服器時，繫結屬性的行為**TidDatabaseConnectionString**必須設為您的電腦上的 TID 資料庫的連接字串。 TRFC 伺服器案例，此配接器會接受 tRFC 用戶端呼叫從 SAP 系統接收 IDOC。  
  
-   配接器的行為與 RFC 伺服器， **TidDatabaseConnectionString**應為 null （預設值）。 如需 RFC 伺服器案例中，此配接器會接受的 RFC 用戶端呼叫從 SAP 系統接收 IDOC。  
  
 下列 Rfc 用來傳送和接收的 Idoc。當傳送 Idoc，配接器會使用這些 Rfc，而 SAP 系統接收 IDOC 時, 使用它們。  
  
-   INBOUND_IDOC_PROCESS。 使用此函式模組的 SAP 4.0 之前的版本。  
  
-   IDOC_INBOUND_ASYNCHRONOUS。 此函式的模組是用 SAP 版本 4.0 及更新版本。  
  
 從 SAP 系統接收 Idoc 支援下列作業：  
  
-   **接收**。 使用這項作業，從使用強型別結構描述的 SAP 系統接收 IDOC。 這項作業的結構描述會公開控制項記錄欄位和資料包括區段標頭和區段欄位的記錄欄位。  
  
     這項作業會顯示每個 idoc，並適用於特定的 IDOC 節點中[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
    > [!NOTE]
    >  若要能夠順利執行**接收**作業，您必須在 SAP 系統相關的授權。 如需詳細資訊，  
  
    > [!NOTE]
    >  使用**接收**作業，您也可以接收多個 Idoc。  
  
-   **ReceiveIdoc**。 使用這項作業，從使用弱式型別的結構描述的 SAP 系統接收 IDOC。 這項作業的結構描述會公開為控制記錄和資料記錄所組成的單一字串欄位的 Idoc。 這項作業在 XML 訊息以字串形式接收 Idoc \<idocData > 標記。  
  
     這是單一作業中顯示所有 SAP 系統所公開的 Idoc，適用於根**IDOC**節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
 當接收 Idoc，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援不同的訊息格式，可以指定為繫結屬性的值， **ReceiveIDocFormat**所公開[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
-   如果設定為 「 類型 」，XML 結構描述強型別所接收的 IDOC。 （從其接收作業可看到此訊息的結構描述。 請注意，在結構描述不同的 Idoc 的不同）。 這會產生 XML IDOC。  
  
-   如果設定為 「 字串 」，內送的 IDOC 資料會傳回為字串值。 （從 ReceiveIdoc 作業可以看到此訊息的結構描述。） 這會產生的 XML 訊息\<idocData > 標記。  
  
-   如果設定為"Rfc"，訊息結構描述符合 RFC 作業 IDOC_INBOUND_ASYNCHRONOUS 或 INBOUND_IDOC_PROCESS，根據連入的 IDOC 版本的 RFC （或 tRFC） 結構描述。 如果您指定這個繫結屬性，您應該使用 IDOC_INBOUND_ASYNCHRONOUS 或 INBOUND_IDOC_PROCESS RFC 接收 IDOC。 在前兩個選項中，配接器在內部使用這個 RFC。 此選項，在您明確地使用這個 RFC 接收 IDOC。  
  
 您用來接收 IDOC 的作業必須符合配接器所發出的 IDOC 資料的格式。 下表提供不同的組合，您可以從 SAP 接收 IDOC 的摘要。  
  
|若要接收的 IDOC 使用|設定繫結屬性 ReceiveIDOCFormat 至|  
|------------------------------|---------------------------------------------------|  
|**接收**作業|具型別|  
|**ReciveIdoc**作業|字串|  
|IDOC_INBOUND_ASYNCHRONOUS RFC|Rfc|  
|INBOUND_IDOC_PROCESS RFC|Rfc|  
  
 另一個繫結屬性**PadReceivedIdocsWithSpaces**進行接收的 IDOC，以空格填補的選擇性欄位時收到的預期格式為"String"。 這可讓與使用舊版的配接器接收的 IDOC 資料格式相容性。  
  
 如需繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
 如需詳細資訊：  
  
-   從使用 BizTalk Server 的 SAP 系統接收 IDOC 看到[從 SAP 使用 BizTalk Server 所接收的 Idoc](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md)。  
  
-   從交易內容，使用 BizTalk Server 中的 SAP 系統接收 IDOC，請參閱[從交易內容所使用的 BizTalk Server 中的 SAP 接收的 Idoc](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server.md)。  
  
-   訊息結構和用於接收 IDOC 的 SOAP 動作，請參閱[IDOC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)。  
  
##  <a name="BKMK_Authorize"></a>SAP 授權使用傳送或接收作業  
 當您使用**傳送**或**接收**傳送或接收 Idoc 使用強型別結構描述作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]內部叫用 IDOCTYPE_READ_COMPLETE RFC 來擷取中繼資料IDOC。 叫用這個 RFC 需要在 SAP 中的下列授權：  
  
```  
Authorisation object S_IDOCDEFT, Fields:  
EDI_TCD, value 'WE30'  
ACTVT, value - 03 (display)  
EDI_DOC, value  *  
EDI_CIM, value *  
```  
  
 您可以使用 sap SU01 交易，以新增授權的物件。 如需有關交易的詳細資訊，請連絡您的 SAP 系統管理員，或請參閱 SAP 文件。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)