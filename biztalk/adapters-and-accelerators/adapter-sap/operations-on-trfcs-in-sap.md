---
title: "TRFCs SAP 中的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RFCs, invoking transactional RFCs in an SAP System
- TID database
- transactional RFCs
- tRFCs, receiving inbound iransactional RFC calls from an SAP system
- tRFCs
- GUID parameter
- RFCs, processing inbound
- RfcConfirmTransID
- transaction ID (TID)
- tRFC Operations
- IDOCS, receiving IDOCs as a tRFC server
- adapters, operations on tRFCs
- RFC, invoking an RFC
ms.assetid: d6a5c515-d6aa-4b70-9c23-32d1dd94d473
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e60465716931161e9b9949e16c4630d85c2cfe2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-trfcs-in-sap"></a>TRFCs SAP 中的作業
交易式 Rfc (tRFCs) 是工作的一個邏輯單位 (LUW) 的一部分會叫用的 Rfc。 在 SAP 系統，luw 會包含所有完成的商業或程式設計工作所需的步驟。 TRFC 代表 RFC; 叫用的方法它不是唯一的 SAP 成品。  
  
 您可以使用[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]同時 tRFC 用戶端和 tRFC 伺服器。  
  
-   **做為 tRFC 用戶端**，配接器可讓您的應用程式叫用單一 RFC 中 LUW SAP 系統上。 這可確保一次只執行 RFC。 它不代表交易行為。  
  
-   **做為 tRFC 伺服器**，配接器可讓您接收多個 Rfc LUW 內。 配接器支援在交易內容中，輸入的 tRFC 呼叫這是認可，並且支援向前復原後的行為。  
  
## <a name="trfc-operations"></a>tRFC 作業  
 TRFC 表示 RFC; 叫用的方法它不是個別的 SAP 成品。 每個 RFC，SAP 系統 （其配接器可以擷取中繼資料） 上的也因此，呈現為由 tRFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 tRFCs 依 RFC 名稱顯示為 TRFC 中繼資料類別目錄節點下的讀取作業。 (您可以瀏覽或搜尋下 tRFCs **TRFC**節點，當您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。)  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] TRFCs 上支援下列：  
  
-   匯入參數  
  
-   變更的參數 （支援變更參數的輸入的端）  
  
> [!NOTE]
>  tRFCs 會以非同步方式執行，它們會不傳回任何輸出值 （匯出或變更參數）。  
  
 GUID 參數會顯示一個 tRFC 作業的配接器。 此 GUID 被對應至 SAP 交易識別碼 (TID) tRFC 與相關聯的配接器。 您可以使用此 GUID 參數才能：  
  
-   確認 tRFC tRFC 用戶端呼叫中的 SAP 系統上。 您可以叫用 RfcConfirmTransId 作業。 這是由配接器必須確認 TID SAP 系統上的顯示特殊作業。  
  
-   取得實際用於 tRFC tRFC 用戶端和 tRFC 伺服器案例中的配接器的 SAP TID。 您可以叫用 SAP 公用程式方法，ConvertGuidToTid。  
  
 如需有關這些作業的詳細資訊，請參閱[特殊作業](../../adapters-and-accelerators/adapter-sap/special-operations.md)。 如需有關的訊息結構和 tRFCs 配接器所使用的 SOAP 動作的詳細資訊，請參閱[tRFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md)。  
  
## <a name="invoking-transactional-rfcs-in-an-sap-system"></a>叫用的交易式 Rfc，SAP 系統中  
 一般而言，tRFCs 可用來執行單一的 LUW; 內的一或多個 RFC 呼叫不過，因為限制在 SAP RFC SDK 中，所以[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援單一一個 tRFC 每 LUW。 基於這個理由，配接器建立每個 tRFC 的 LUW (SAP TID)。 這類用戶端，SAP 定義 LUW 機制，保證會以 RFC 的 「 一次性 」 執行和認可和回復交易並不表示。  
  
 下列步驟概述 RFC 用戶端呼叫使用中執行的工作[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 某些步驟會執行配接器用戶端，且部分都是透過配接器。  
  
1.  配接器用戶端會傳送一個 tRFC 作業的要求訊息。 配接器用戶端可以選擇性地提供此訊息的 GUID。  
  
2.  [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]接收要求訊息，並使用來取得從 SAP 系統的交易識別碼 (TID) 的 RFC SDK。 如果要求訊息包含 GUID，配接器會將此 GUID 對應至 SAP TID。否則，配接器建立新的 GUID，並將其對應至 SAP TID  
  
3.  配接器會使用 TID 進行 tRFC 呼叫到 SAP 伺服器。 TID 狀態標示為**已經完成**SAP 系統上。  
  
4.  配接器傳回的 GUID (對應到 TID） 配接器中的用戶端的回應訊息。  
  
5.  配接器用戶端叫用 RfcConfirmTransID 作業介面卡上的與上一個步驟中傳回的 GUID。  
  
6.  配接器會在 RfcConfirmTransID 要求訊息中使用 GUID 來識別 SAP TID，並確認 tRFC 呼叫 SAP 系統上。 這會導致 SAP 伺服器，從其資料庫中刪除 TID 項目。  
  
> [!NOTE]
>  tRFC 用戶端呼叫不會傳回匯出或變更參數。  
  
 如需詳細資訊：  
  
-   叫用 tRFC，使用 BizTalk Server，請參閱[叫用中使用 BizTalk Server 的 SAP tRFCs](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md)。  
  
-   叫用 tRFC，使用 WCF 服務模型，請參閱[叫用中使用 WCF 服務模型的 SAP tRFCs](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md)。  
  
-   訊息結構和叫用 tRFC 的 SOAP 動作，請參閱[tRFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md)。  
  
## <a name="receiving-inbound-transactional-rfc-calls-from-an-sap-system"></a>從 SAP 系統接收傳入異動的 RFC 呼叫  
 您可以從 SAP 接收 tRFCs 為 tRFC 伺服器使用配接器。 為 tRFC 伺服器，當配接器接收 tRFC，它會叫用您的應用程式的對應 tRFC 作業。 它會充當 tRFC 伺服器時，配接器支援下列功能：  
  
-   LUW （以 SAP TID 識別） 可以包含多個 tRFCs （RFC 呼叫）。  
  
-   配接器會為每個 SAP TID 建立可認可的交易。 應用程式程式碼可以在此交易中登記。  
  
-   支援認可和回復。  
  
 此章節的其餘部分提供有關使用配接器做為 tRFC 伺服器的一般資訊。 如需特定的相關資訊：  
  
-   接收輸入的 tRFC 呼叫使用 BizTalk Server，請參閱[接收輸入 tRFC 呼叫從 SAP 使用 BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-from-sap-using-biztalk-server.md)。  
  
-   接收輸入的 tRFC 呼叫使用 WCF 服務模型，請參閱[接收輸入 tRFC 呼叫中使用 WCF 服務模型的 SAP](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model.md)。  
  
### <a name="the-tid-database"></a>TID 資料庫  
 配接器時，它會充當 tRFC 伺服器，使用 SQL Server 資料庫 — TID 資料庫-管理交易收到來自 SAP 系統的識別碼。 比方說，它會使用 TID 資料庫來協助管理從 SAP 系統上，以認可、 復原的呼叫，並確認 TID。 配接器也會儲存它會建立並將每個 TID 資料庫中的 SAP TID 與相關聯的 GUID。  
  
### <a name="prerequisites"></a>必要條件  
 為了執行 tRFC 伺服器配接器，您必須確定在下列條件成立：  
  
-   必須宣告 RFC，SAP 系統上。 這是讓配接器可以擷取描述從 SAP 系統的 RFC 的中繼資料。 RFC 實際上是在您的應用程式中實作的。  
  
-   配接器必須向 SAP 閘道上的 RFC 目的地。 註冊為基礎的邏輯名稱呼叫的程式識別碼。 您提供連線至指定的程式識別碼 URI 中的參數 SAP 閘道，以及此註冊 SAP 伺服器。  
  
-   TID 資料庫必須建立 SQL Server 中。 若要這樣做，您必須執行安裝程式已安裝的 SQL 指令碼。 SQL 指令碼通常會安裝在\<安裝磁碟機 >: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[安裝 BizTalk Adapter Pack](http://msdn.microsoft.com/library/2ae27db5-b11b-42c3-a568-e2331badf80e)。  
  
-   **TidDatabaseConnectionString**繫結屬性必須設定為 TID 資料庫的 SQL 資料庫連接字串。 如需有關**TidDatabaseConnectionString**繫結屬性，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
> [!NOTE]
>  設定**TidDatabaseConnectionString**繫結屬性會設定要做為 tRFC 伺服器，而不是 RFC 伺服器的介面卡。 如果**TidDatabaseConnectionString**內容繫結設定，且您指定連線 URI 中的 RFC 目的地，配接器做為 RFC 目的地的來電的 tRFC 伺服器。 如果未設定這個繫結屬性，配接器會做為 RFC 伺服器。  
  
### <a name="how-the-adapter-processes-inbound-trfcs"></a>如何處理程序的輸入配接器的 tRFCs  
 下列步驟概述的工作都是透過 RFC 用戶端呼叫使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 某些步驟會執行配接器用戶端，且部分都是透過配接器。  
  
1.  SAP 系統呼叫到配接器能 TID 是否已在使用中。 配接器傳回至 SAP 系統的適當回應。 如果是新的 TID，配接器會建立可認可的交易。 此交易用來以交易方式保存 TID 資料庫 TID，SAP 程式執行認可 （認可工作） 時。 它也會顯示處理輸入的 tRFCs 的應用程式程式碼。 此外，配接器會建立它與 SAP TID 產生關聯的 GUID。  
  
2.  SAP 系統會傳送至配接器的一或多個交易式的 Rfc。 針對每個 tRFC，配接器會叫用您的應用程式的適當 tRFC 作業。 配接器會在您的應用程式，每個作業步驟 1 中建立的異動流動。 配接器會傳遞作業的要求訊息中的步驟 1 中建立的 GUID。  
  
3.  SAP 系統就會認可 LUW (COMMIT WORK)。 配接器會嘗試認可交易與 SAP TID （在步驟 1 中建立） 相關聯。  
  
    1.  如果交易已中止 （依您的應用程式），在步驟 2 中呼叫的任何一個期間，會發生錯誤時，配接器嘗試認可交易。 對 SAP 會傳回錯誤。 移至步驟 4。  
  
    2.  如果認可成功，TID 現在是 TID 資料庫中。 移至步驟 5。  
  
4.  如果錯誤發生在步驟 3，或如果 SAP 回復 LUW (RESTART_OF_BACKGROUNDTASK) 而不是認可，配接器會回復交易。 在此情況下 TID 資料庫永遠不會保存 TID。  
  
5.  SAP 系統確認 TID。 配接器會將 TID 移除 TID 資料庫 （假設步驟已順利完成的 3 和 TID 存在於 TID 資料庫。  
  
> [!NOTE]
>  如果嘗試連接到 TID 資料庫 tRFC 伺服器作業期間發生錯誤，指出此問題的錯誤代碼從 SAP 來電未處理[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]傳回給 SAP。  
  
### <a name="receiving-idocs-as-a-trfc-server"></a>做為 tRFC 伺服器接收 Idoc  
 您使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]RFC 伺服器或 tRFC 伺服器從 SAP 系統接收 Idoc。 在任一情況下，您必須設定**ReceiveIdocFormat**內容繫結至指定的格式中的配接器應該將 IDOC 資料發出到您的應用程式。 如需使用配接器接收 Idoc 的詳細資訊，請參閱[sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。 如需有關[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結屬性，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
## <a name="special-trfc-operations"></a>特殊 tRFC 作業  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也可以執行 SAP 系統上的某些特殊 tRFC 作業。 一個這類作業是 RfcConfirmTransID。  
  
-   **RfcConfirmTransID。** 您在上叫用這項作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]確認 tRFC 呼叫對 SAP 伺服器。 配接器用於傳送 Idoc 到 SAP 伺服器作為 tRFC 的案例中，可能需要 RfcConfirmTransID。 此作業時才可使用**TRFC**節點時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
 如需訊息結構和 RfcConfirmTransID 作業的 SOAP 動作的詳細資訊，請參閱[tRFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [連接至 SAP 系統使用配接器](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)