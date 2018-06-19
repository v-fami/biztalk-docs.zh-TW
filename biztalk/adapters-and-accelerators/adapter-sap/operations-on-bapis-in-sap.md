---
title: SAP 中的 Bapi 的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAPI, operations
- BAPIs, operations on
- Business Application Programming Interface
- BAPIs
- BAPI, transactions
- BAPI transactions, limitations on
ms.assetid: 6be26641-e8d3-4e11-8d82-4fdb13076580
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b8504dd05c671307085d621c474969a70026d2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217902"
---
# <a name="operations-on-bapis-in-sap"></a>SAP 中的 Bapi 的作業
商務應用程式發展介面 (BAPI) 是一種方法可以由外部處理序呼叫的 SAP 商務物件。 Bapi 是交易式 SAP 系統上。  
  
 [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] BAPI 呼叫的輸出方向的支援。 它會呈現 Bapi 兩種方式：  
  
-   **以 RFC**。 您可以叫用 BAPI 直接叫用適當的 RFC。  
  
-   **為商務物件方法**。 配接器呈現為商務物件的方法以便於協助您擷取中繼資料，當您使用 Bapi[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。  
  
> [!IMPORTANT]
>  您可以叫用介面卡上的 BAPI 為 RFC 或商務物件方法;但是，不論您如何叫用的介面卡上 BAPI，它一定會叫用在 SAP BAPI 透過 RFC 介面。  
  
 配接器支援 BAPI 交易。 SAP 的 BAPI 交易模型可讓使用者將數個 Bapi 結合成一個工作 (LUW) 邏輯單元。 SAP luw 會包含所有交易，包括更新資料庫中所需的步驟。  
  
 本節中的主題將說明如何 Bapi 當成商務物件和配接器支援 BAPI 交易 (LUWs) 的方式。  
 
  
## <a name="bapi-operations-as-business-object-methods"></a>BAPI 作業 （做為商務物件方法）  
 因為商務物件方法，以便於協助您擷取中繼資料，當您使用配接器提供諸如 Bapi[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 配接器永遠會 Bapi 使用 RFC 介面的 SAP 系統上叫用。  
  
 配接器會呈現為適當的商務物件下輸出作業的作業，在依名稱的 Bapi。 商務物件會收集由配接器的 BAPI 類別目錄節點之下的功能群組。 (您可以瀏覽或搜尋商務物件和 Bapi 下的**BAPI**節點，當您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。)  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] Bapi 上支援下列：  
  
-   匯入參數  
  
-   匯出參數  
  
-   變更參數  
  
-   資料表參數  
  
 如需用於 Bapi 當成商務物件方法的 SOAP 動作與訊息結構的詳細資訊，請參閱[BAPI 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-bapi-operations.md)。  
  
## <a name="bapi-transactions"></a>BAPI 交易  
 當您叫用 BAPI 時，它一律是 LUW SAP 系統的一部分。 是否為 RFC 或商務物件的方法叫用 BAPI 也是如此。 RFC SDK 會將所有 Bapi 透過相同的 SAP 連線相同 LUW 的一部分傳送。 呼叫之後認可，或在連接上回復交易，透過連線傳送的下一個 BAPI 開始新 LUW。  
  
 您可以呼叫 BAPI_TRANSACTION_COMMIT 或 BAPI_TRANSACTION_ROLLBACK 認可或回復交易。 配接器會提供諸如這些兩個 Bapi:  
  
-   在做為 RFC 作業的基礎節點。  
  
-   在每個商務物件。  
  
 您可以控制在交易中的 Bapi 確保，所有傳送相同的 SAP 連線 （包括在呼叫認可或回復交易）。 您可以執行這個動作：  
  
-   使用 BizTalk 解決方案**ConnectionState**訊息內容屬性，以確保在交易中的 Bapi 使用相同連線傳送。 這個屬性會顯示由配接器，並提供您使用明確控制用來傳送訊息，BizTalk 協調流程中的連接。  
  
     針對執行使用 BizTalk Server 的 BAPI 交易[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援下列的訊息內容屬性。  
  
    |欄位|Description|  
    |-----------|-----------------|  
    |OPEN|開啟交易的新通道。|  
    |重複使用|重複使用現有交易的通道。|  
    |CLOSE|認可交易，並關閉現有的通道。|  
    |中止|中止交易，並關閉現有的通道。|  
  
     如需詳細資訊，請參閱[執行 SAP 使用 BizTalk Server 中的 BAPI 交易](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md)。  
  
    > [!NOTE]
    >  請確定您設定**EnableBizTalkCompatibilityMode**執行交易使用 BizTalk Server 時，繫結屬性。  
  
-   方法是確保在交易中的 Bapi 使用相同的 WCF 用戶端傳送的 WCF 服務模型方案。 如需詳細資訊，請參閱[SAP 使用 WCF 服務模型中的 叫用 Bapi](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md)。  
  
-   WCF 通道模型方案確保透過相同的 WCF 通道所傳送的交易中的 Bapi。 如需詳細資訊，請參閱[開發應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)。  
  
### <a name="limitations-on-bapi-transactions"></a>BAPI 交易的限制  
 BAPI 交易上套用下列限制：  
  
-   您不可能在一個 LUW 中的相同執行個體上進行兩個寫入存取。 例如，您無法建立訂單，並在相同交易中更新它。  
  
-   當執行交易使用的 BAPI [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，必須透過傳送埠的單一主控件執行個體傳送的所有訊息。  
  
-   如果執行個體是建立、 更新或刪除使用 BAPI 的寫入，BAPI 的讀取寫入 BAPI 認可之前無法檢視最新的資料。  
  
-   外部用戶端叫用 LUW 應該相同的 SAP 連接上呼叫 luw 會包含所有 Bapi。  
  
> [!IMPORTANT]
>  屬於發行 3.1 的 Bapi 呼叫 COMMIT WORK 其實作的一部分。 這表示，（因為它們將會認可交易），這些 Bapi 不可以包含其他 LUW 中的 Bapi。 如需詳細資訊，請參閱 SAP 文件集。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)