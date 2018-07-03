---
title: 對 sap 的 Trfc 的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b99822d838f0681cf9a6ce336ed1a23f4088c659
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996135"
---
# <a name="operations-on-trfcs-in-sap"></a>對 sap 的 Trfc 的作業
交易式 Rfc (Trfc) 是工作的一個邏輯單位 (LUW) 的一部分叫用 Rfc。 在 SAP 系統上，LUW 包含所有完成的商務或程式設計工作所需的步驟。 TRFC 代表一種叫用 RFC;它不是唯一的 SAP 成品。  
  
 您可以使用[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]作為 tRFC 用戶端和 tRFC 伺服器。  
  
-   **TRFC 用戶端為**，配接器可讓您的應用程式叫用單一的 RFC LUW 上 SAP 系統中。 這可確保一次只執行 RFC。 它並不表示交易式的行為。  
  
-   **為 tRFC 伺服器**，配接器可讓您接收 LUW 內的多個 Rfc。 配接器支援交易的內容; 中的輸入的 tRFC 呼叫這是認可，並且支援向前復原後的行為。  
  
## <a name="trfc-operations"></a>tRFC 作業  
 TRFC 隱含的方式叫用 RFC;它不是個別的 SAP 成品。 （為其配接器可以擷取中繼資料） 的 SAP 系統上的每個 RFC 也因此，顯示為的 tRFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 Trfc 依 RFC 名稱顯示為的 TRFC 中繼資料類別目錄節點下的讀取作業。 (您可以瀏覽或搜尋在 Trfc **TRFC**當您使用的節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。)  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] Trfc 上支援下列：  
  
-   匯入參數  
  
-   變更的參數 （支援變更參數的輸入的端）  
  
> [!NOTE]
>  Trfc 會以非同步方式執行，因此它們會不傳回任何輸出值 （匯出或變更參數）。  
  
 TRFC 作業的配接器，會顯示 GUID 參數。 此 GUID 被對應到 SAP 交易識別碼 (TID) tRFC 與相關聯的配接器。 您可以使用此 GUID 參數：  
  
- 確認 tRFC tRFC 用戶端呼叫中的 SAP 系統上。 您可以叫用 RfcConfirmTransId 作業。 這是由配接器必須確認 TID SAP 系統上的顯示特殊作業。  
  
- 取得實際的 SAP TID tRFC tRFC 用戶端和 tRFC 伺服器案例中的配接器的使用。 您可以叫用 SAP 公用程式方法，ConvertGuidToTid 即可。  
  
  如需有關這些作業的詳細資訊，請參閱 <<c0> [ 特殊作業](../../adapters-and-accelerators/adapter-sap/special-operations.md)。 如需有關用於 Trfc 配接器的 SOAP 動作與訊息結構的詳細資訊，請參閱[tRFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md)。  
  
## <a name="invoking-transactional-rfcs-in-an-sap-system"></a>叫用交易式的 Rfc，SAP 系統中  
 通常，將 Trfc 用來執行單一的 LUW; 內的一或多個 RFC 呼叫不過，由於 SAP RFC SDK 的限制[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援單一一個 tRFC 每 LUW。 基於這個理由，配接器會建立每個 tRFC 的 LUW (SAP TID)。 這類用戶端，SAP 會定義一個機制來保證會 「 單次 」 執行 RFC LUW，並不表示認可及回復交易。  
  
 下列步驟概述的工作執行的 RFC 用戶端呼叫使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 其中某些步驟由配接器用戶端，部分由配接器。  
  
1. 配接器用戶端會傳送一個 tRFC 作業的要求訊息。 配接器用戶端可以選擇性地提供此訊息中的 GUID。  
  
2. [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]接收要求訊息，並使用從 SAP 系統中取得的交易識別碼 (TID) 的 RFC SDK。 如果要求訊息包含 GUID，配接器會將此 GUID 對應到 SAP TID;配接器，否則為建立新的 GUID，並將它對應至 SAP TID  
  
3. 配接器會使用 TID，進行 tRFC 呼叫到 SAP 伺服器。 TID 的狀態會標示為**已完成**SAP 系統上。  
  
4. 配接器傳回至回應訊息的配接器用戶端的 GUID （也就對應至 TID）。  
  
5. 配接器用戶端叫用 RfcConfirmTransID 作業介面卡上的與前一個步驟中所傳回的 GUID。  
  
6. 配接器 RfcConfirmTransID 要求訊息中會使用 GUID 來識別 SAP TID，並確認 SAP 系統上的 tRFC 呼叫。 這會導致 SAP 伺服器，從其資料庫中刪除的 TID 項目。  
  
> [!NOTE]
>  tRFC 用戶端呼叫不會傳回匯出或變更參數。  
  
 如需詳細資訊：  
  
-   叫用 tRFC，使用 BizTalk Server，請參閱[叫用 Trfc SAP 使用 BizTalk Server 中的](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md)。  
  
-   叫用 tRFC，使用 WCF 服務模型，請參閱[叫用中使用 WCF 服務模型的 SAP 的 Trfc](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md)。  
  
-   訊息結構和叫用 tRFC 的 SOAP 動作，請參閱[tRFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md)。  
  
## <a name="receiving-inbound-transactional-rfc-calls-from-an-sap-system"></a>從 SAP 系統的接收傳入異動的 RFC 呼叫  
 您可以從 SAP 接收 Trfc 為 tRFC 伺服器使用配接器。 為 tRFC 伺服器，當配接器接收的 tRFC，它會叫用對應的 tRFC 作業，在您的應用程式。 它會充當 tRFC 伺服器時，配接器支援下列功能：  
  
- LUW （由 SAP TID 識別） 可以包含多個 Trfc （RFC 呼叫）。  
  
- 配接器會建立每個 SAP TID 認可的交易。 應用程式程式碼可以在這個交易中編列。  
  
- 支援認可和回復。  
  
  本節的其餘部分會提供有關使用配接器做為 tRFC 伺服器的一般資訊。 如需更特定的資訊：  
  
- 接收輸入的 tRFC 呼叫使用 BizTalk Server，請參閱 <<c0> [ 接收輸入的 tRFC 呼叫從使用 BizTalk Server 的 SAP](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-from-sap-using-biztalk-server.md)。  
  
- 接收輸入的 tRFC 呼叫使用 WCF 服務模型，請參閱 <<c0> [ 接收輸入的 tRFC 呼叫中使用 WCF 服務模型的 SAP](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model.md)。  
  
### <a name="the-tid-database"></a>TID 資料庫  
 當它作為 tRFC 伺服器時，配接器使用 SQL Server 資料庫 — TID 資料庫，來管理交易從 SAP 系統它接收的識別碼。 比方說，它會使用 TID 資料庫來協助管理從 commit、 rollback SAP 系統的呼叫，以及確認 TID。 配接器也會儲存的 GUID，它會建立並關聯 TID 資料庫中每個 SAP TID。  
  
### <a name="prerequisites"></a>必要條件  
 做為 tRFC 伺服器讓配接器，您必須確定在下列條件成立：  
  
- 必須宣告 RFC，SAP 系統上。 這是讓配接器可以擷取描述從 SAP 系統的 RFC 的中繼資料。 RFC 實際上是在您的應用程式中實作。  
  
- 配接器必須向 SAP 閘道上的 RFC 目的地。 註冊為基礎的邏輯名稱，叫做程式 id。 提供連線至指定的程式識別碼 URI 參數 SAP 閘道，以及此註冊的 SAP 伺服器。  
  
- TID 資料庫必須建立 SQL Server 中。 若要這樣做，您必須執行安裝程式已安裝的 SQL 指令碼。 SQL 指令碼通常會安裝在\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[安裝 BizTalk Adapter Pack](http://msdn.microsoft.com/library/2ae27db5-b11b-42c3-a568-e2331badf80e)。  
  
- **TidDatabaseConnectionString**繫結屬性必須設為 TID 資料庫的 SQL 資料庫連接字串。 如需詳細資訊**TidDatabaseConnectionString**繫結屬性，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
> [!NOTE]
>  設定**TidDatabaseConnectionString**屬性繫結會設定要做為 tRFC 伺服器，而不是 RFC 伺服器的配接器。 如果**TidDatabaseConnectionString**屬性繫結設定，且您的連線 URI 中指定的 RFC 目的地，配接器可做為來自 RFC 目的地的傳入呼叫的 tRFC 伺服器。 如果未設定這個繫結屬性，配接器可做為 RFC 伺服器中。  
  
### <a name="how-the-adapter-processes-inbound-trfcs"></a>如何配接器處理程序輸入的 Trfc  
 下列步驟概述的工作由 RFC 用戶端呼叫使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 其中某些步驟由配接器用戶端，部分由配接器。  
  
1.  SAP 系統呼叫到配接器能 TID 是否已在使用中。 配接器傳回 SAP 系統的適當回應。 如果是新的 TID，配接器會建立認可的交易。 要在交易的方式保存 TID 資料庫 TID，SAP 程式執行的認可 (COMMIT WORK) 時，使用此交易。 它也會公開給應用程式程式碼會處理輸入的 Trfc。 此外，配接器會建立一個會將 SAP TID 和關聯的 GUID。  
  
2.  SAP 系統會傳送至配接器的一或多個交易式的 Rfc。 針對每個 tRFC，配接器叫用您的應用程式的適當 tRFC 作業。 配接器會在您的應用程式，每個作業的步驟 1 中建立的異動流動。 配接器會將作業要求訊息中的步驟 1 中建立的 GUID。  
  
3.  SAP 系統認可 LUW (COMMIT WORK)。 配接器會嘗試認可交易 （在步驟 1 中建立） 的 SAP TID 與相關聯。  
  
    1.  如果交易中止 （由您的應用程式） 期間呼叫在步驟 2，則配接器嘗試認可交易時發生錯誤。 Sap 會傳回錯誤。 移至步驟 4。  
  
    2.  如果認可成功，TID 現在是 TID 資料庫中。 移至步驟 5。  
  
4.  如果錯誤發生在步驟 3，或如果 SAP 回復 LUW (RESTART_OF_BACKGROUNDTASK) 而不是認可，配接器會回復交易。 在此情況下 TID 資料庫永遠不會保存 TID。  
  
5.  SAP 系統確認 TID。 配接器會將 TID 移除 TID 資料庫 （假設步驟已順利完成的 3 和 TID 存在於 TID 資料庫。  
  
> [!NOTE]
>  如果嘗試連線到 TID 資料庫 tRFC 伺服器作業期間發生錯誤，錯誤代碼，表示來自 SAP 的連入呼叫而未處理[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會傳回到 SAP。  
  
### <a name="receiving-idocs-as-a-trfc-server"></a>為 tRFC 伺服器接收 Idoc  
 您使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]為 RFC 伺服器或從 SAP 系統接收 Idoc 的 tRFC 伺服器。 在任一情況下，您必須設定**ReceiveIdocFormat**繫結屬性，以指定在其中配接器應該將 IDOC 資料發出到您的應用程式的格式。 如需有關如何使用配接器接收 idoc 用的詳細資訊，請參閱[對 sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。 如需詳細資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結屬性，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
## <a name="special-trfc-operations"></a>特殊的 tRFC 作業  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也可以執行 SAP 系統上的某些特殊的 tRFC 作業。 這類的一項作業是 RfcConfirmTransID。  
  
- **RfcConfirmTransID。** 您在上叫用這項作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]確認對 SAP 伺服器的 tRFC 呼叫。 在配接器來傳送 Idoc 至 SAP 伺服器的 tRFC 的情況下，可能需要 RfcConfirmTransID。 此作業，會位於**TRFC**時使用的節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
  如需有關的訊息結構和 RfcConfirmTransID 作業的 SOAP 動作的詳細資訊，請參閱[tRFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [連接到 SAP 系統使用配接器](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)