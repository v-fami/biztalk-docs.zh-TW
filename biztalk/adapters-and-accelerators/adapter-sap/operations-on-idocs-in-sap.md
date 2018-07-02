---
title: 對 sap Idoc 的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDOC, operations to receive an
- IDOCs
- IDOCs, operations on
- tRFC server
- IDOC, operations to send an
- RFC server
ms.assetid: 6abcc646-c7a3-48cf-a09e-01f516dcef97
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9c3bbf45074024b8745b845b3f9ca85f5ff814e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972223"
---
# <a name="operations-on-idocs-in-sap"></a>對 sap Idoc 的作業
IDOCs 會是 SAP 支援用來以非同步方式與 SAP 和非 SAP 系統通訊的標準化的類似 EDI 的文件。 Idoc 用來傳送及接收"business"文件，例如銷售訂單，或從交易夥伴的 SAP 系統或外部程式。  
  
 雖然 SAP 系統支援多種來傳送和接收 Idoc 的連接埠類型 (例如檔案的連接埠，CPIC 連接埠)、[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援傳送及接收 Idoc 透過一個 tRFC 連接埠。  
  
## <a name="operations-to-send-an-idoc"></a>傳送 IDOC 的作業  
 所有 SAP IDOC 呼叫會在內部都視為 tRFC 呼叫中的配接器做為 tRFC 用戶端，並呼叫 RFC，SAP 傳送 IDOC 中。 就像任何 tRFC 用戶端呼叫，配接器用戶端會選擇性地將 GUID 傳遞至配接器，接著將它與交易識別碼 (TID)，它會在 SAP 系統上呼叫相關聯。 （如果配接器用戶端未通過 GUID，配接器會產生其專屬 GUID。）GUID 會傳回至回應訊息的配接器用戶端。 若要確認 TID SAP 系統上的，配接器用戶端可以使用此 GUID。 實際的叫用特殊的靜態方法，在 SAP 繫結中，也可以取得 tRFC 呼叫配接器使用的 SAP TID **ConvertGuidToTid**。 具有實際的 TID 可能很有用的 SAP 系統上的問題進行疑難排解。  
  
 傳送 IDOC 完成呼叫之後，必須在 SAP 系統上確認 TID。 這可讓 SAP 系統從其資料庫中刪除 TID。 配接器用戶端可以確認 TID SAP 系統上。  
  
- 明確地藉由叫用**RfcConfirmTransID**介面卡上的作業。 這項作業會使 （上述的回應訊息中傳回） 的 GUID，而造成配接器必須確認 SAP 系統上相關聯的 TID。  
  
- 以隱含的方式，是藉由設定**AutoConfirmSentIdocs**繫結屬性。 如果這個繫結屬性為 true，配接器將會自動認可 TID 之後傳送 IDOC 至 SAP 系統。 請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)如需詳細資訊。  
  
  [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會使用下列 Rfc 傳送 IDOC:  
  
- INBOUND_IDOC_PROCESS。 使用此函式模組的 SAP 版本 4.0 之前。  
  
- IDOC_INBOUND_ASYNCHRONOUS。 此函式模組是用 SAP 版本 4.0 及更新版本。  
  
### <a name="sending-idocs-with-segment-data-across-multiple-lines"></a>傳送 Idoc 的區段資料跨多行  
 IDOCs 會構成的區段。 在 IDOC 一般檔案中的每個區段項目包含的區段標頭資訊 （包含 DOCNUM 欄位） 及分割資料。 在某些 Idoc，區段資料可以分成多行。 例如：  
  
```  
Segment header (DOCNUM is one of the fields here)  |  Segment data  
Segment header (DOCNUM is one of the fields here)  |  Segment data  
Segment data wrapped from the previous line  
Segment header (DOCNUM is one of the fields here)  |  Segment data  
```  
  
 以 WCF 為基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援傳送這類的 Idoc 至 SAP 系統。 若要支援傳送這類的 Idoc，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]決定每個區段的資料是否將延續前一個位置，或是否為新的分割資料。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]剖析每個區段標頭，並尋找 DOCNUM 欄位決定這。 如果區段資料分成兩行，第二行沒有區段標頭，因此[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]找不到 DOCNUM 欄位。 因此，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可以判斷它是將延續先前的區段資料。  
  
 例如，在如上所示，IDOC 的表示法[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]找不到任何 DOCNUM 欄位中的 」`Segment data wrapped from the previous line`"，而且能夠決定這條線是將延續先前的區段資料。 考量大小的 IDOC 一般檔案在生產環境中，執行這類檢查每個區段的資料可能會導致增加處理時間。  
  
> [!NOTE]
>  IDOC 資料中，配接器會使用 DOCNUM 欄位，而不是歸位字元傳回換行字元 (CRLF) 來識別和擷取區段中的每筆記錄。 如果 DOCNUM 記錄中的欄位控制項和資料都是無效或部分空白，配接器無法剖析 IDOC。 因此，不會繼續 IDOC 到 SAP 系統。  
  
### <a name="operations-to-send-an-idoc"></a>傳送 IDOC 的作業  
 傳送 Idoc 到 SAP 系統支援下列作業：  
  
- **傳送**。 您可以使用這項作業來傳送 IDOC 至 SAP 系統，請使用強型別結構描述。 這項作業的結構描述會公開控制記錄的欄位和資料記錄欄位，包括區段標頭和區段的欄位。 傳送作業是 IDocType + CimType + ReleaseNumber + 版本的特定組合。  
  
   這項作業會顯示每個 idoc，並且可在特定的 IDOC 節點下[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
  > [!NOTE]
  >  若要能夠成功執行**傳送**作業中，您必須在 SAP 系統中的相關的授權。 如需詳細資訊，  
  
- **SendIdoc**。 您可以使用這項作業來傳送 IDOC 至 SAP 系統，請使用弱型別結構描述。 這項作業的結構描述會公開為單一字串欄位所組成的控制記錄和資料記錄的 Idoc。 SendIdoc 作業將會做為參數的 IDOC 字串和 GUID。  
  
   這是呈現 SAP 系統所公開的所有 Idoc 的單一作業，並位在根目錄**IDOC**中的節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
  如需詳細資訊：  
  
- 傳送 IDOC 至 SAP 系統，請使用 BizTalk Server，請參閱[傳送的 Idoc 至 SAP 使用 BizTalk server](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-biztalk-server.md)。  
  
- 傳送 IDOC 到 SAP 系統使用 WCF 服務模型，請參閱[傳送的 Idoc 至 SAP 使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-the-wcf-service-model.md)。  
  
- 訊息結構和 SOAP 動作，以便傳送 IDOC，請參閱[IDOC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)。  
  
## <a name="operations-to-receive-an-idoc"></a>接收 IDOC 的作業  
 若要接收 IDOC， [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] tRFC 伺服器或 RFC 伺服器可以運作：  
  
- 做為 tRFC 伺服器時，繫結屬性，配接器**TidDatabaseConnectionString**必須設為您的電腦上的 TID 資料庫的連接字串。 TRFC 伺服器案例中，此配接器會接受 tRFC 用戶端呼叫從 SAP 系統接收 IDOC。  
  
- 行為與 RFC 伺服器中，配接器**TidDatabaseConnectionString**應為 null （預設值）。 RFC 伺服器案例中，此配接器會接受從 SAP 系統接收 IDOC 的 RFC 用戶端呼叫。  
  
  下列 Rfc 用來傳送和接收 Idoc;當傳送 Idoc，配接器會使用這些 Rfc，而 SAP 系統接收 IDOC 時, 使用它們。  
  
- INBOUND_IDOC_PROCESS。 使用此函式模組的 SAP 版本 4.0 之前。  
  
- IDOC_INBOUND_ASYNCHRONOUS。 此函式模組是用 SAP 版本 4.0 及更新版本。  
  
  從 SAP 系統接收 Idoc 支援下列作業：  
  
- **接收**。 您可以使用此作業，從使用強型別結構描述的 SAP 系統接收 IDOC。 這項作業的結構描述會公開控制記錄的欄位和資料記錄的欄位，包括區段標頭和區段的欄位。  
  
   這項作業會顯示每個 idoc，並且可在特定的 IDOC 節點下[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
  > [!NOTE]
  >  若要能夠成功執行**接收**作業中，您必須在 SAP 系統中的相關的授權。 如需詳細資訊，  
  
  > [!NOTE]
  >  使用**接收**作業中，您也可以接收多個 Idoc。  
  
- **ReceiveIdoc**。 您可以使用此作業，從使用弱型別結構描述的 SAP 系統接收 IDOC。 這項作業的結構描述會公開為單一字串欄位，其中包含控制記錄和資料記錄的 Idoc。 這項作業下的 XML 訊息中的字串形式接收 Idoc \<idocData\>標記。  
  
   這是呈現 SAP 系統所公開的所有 Idoc 的單一作業，並位在根目錄**IDOC**中的節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
  接收 Idoc，時會[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援不同的訊息格式，可以指定為繫結屬性的值， **ReceiveIDocFormat**由[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
- 如果設定為 「 類型 」，XML 結構描述強型別所接收的 IDOC。 （從其接收作業可看到此訊息的結構描述。 請注意，結構描述不同的 Idoc 的不同）。 這會產生 XML IDOC。  
  
- 如果設定為"String"，內送的 IDOC 資料會傳回為字串值。 （從 ReceiveIdoc 作業可以看到此訊息的結構描述。） 這會產生的 XML 訊息\<idocData\>標記。  
  
- 如果設為 「 Rfc 」，將訊息結構描述符合 RFC 作業 IDOC_INBOUND_ASYNCHRONOUS 或 INBOUND_IDOC_PROCESS，根據內送的 IDOC 版本的 RFC （或 tRFC） 結構描述。 如果您指定這個繫結屬性，您應該使用 IDOC_INBOUND_ASYNCHRONOUS 或 INBOUND_IDOC_PROCESS RFC 接收 IDOC。 在前兩個選項中，配接器會在內部使用這個 RFC。 此選項時，在您明確地使用這個 RFC 接收 IDOC。  
  
  您用來接收 IDOC 的作業必須符合配接器所發出的 IDOC 資料的格式。 下表提供不同的組合，在其中您可以從 SAP 接收 IDOC 的摘要。  
  
|若要接收的 IDOC 使用|設定繫結屬性 ReceiveIDOCFormat 至|  
|------------------------------|---------------------------------------------------|  
|**接收**作業|具型別|  
|**ReciveIdoc**作業|String|  
|IDOC_INBOUND_ASYNCHRONOUS RFC|Rfc|  
|INBOUND_IDOC_PROCESS RFC|Rfc|  
  
 另一個繫結屬性**PadReceivedIdocsWithSpaces**填補空格與接收的 IDOC 的選擇性欄位時收到預期的格式為"String"。 這可讓使用舊版的配接器接收的 IDOC 資料格式與相容性。  
  
 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
 如需詳細資訊：  
  
-   接收 IDOC，從 SAP 系統，請使用 BizTalk Server 中，請參閱[SAP 使用 BizTalk server 從接收的 Idoc](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md)。  
  
-   從交易內容，使用 BizTalk Server 中的 SAP 系統接收 IDOC，請參閱[接收的 Idoc，從交易內容所使用的 BizTalk Server 中的 SAP](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server.md)。  
  
-   訊息結構和 SOAP 動作，以便接收 IDOC，請參閱[IDOC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)。  
  
##  <a name="BKMK_Authorize"></a> SAP 授權用於傳送或接收作業  
 當您使用**傳送**或是**接收**作業來傳送或接收 Idoc 使用強型別結構描述，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]內部叫用 IDOCTYPE_READ_COMPLETE RFC，若要擷取的中繼資料IDOC。 叫用這個 RFC 需要在 SAP 中的下列授權：  
  
```  
Authorisation object S_IDOCDEFT, Fields:  
EDI_TCD, value 'WE30'  
ACTVT, value - 03 (display)  
EDI_DOC, value  *  
EDI_CIM, value *  
```  
  
 您可以使用 SU01 交易在 SAP 中，以新增授權的物件。 如需有關交易的詳細資訊，請連絡您的 SAP 系統管理員，或請參閱 SAP 文件。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)