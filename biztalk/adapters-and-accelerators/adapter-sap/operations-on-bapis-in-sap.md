---
title: 對 SAP 中的 Bapi 的作業 |Microsoft Docs
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
ms.openlocfilehash: a319626f23b825187d65e01d687be5a1079df53a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993167"
---
# <a name="operations-on-bapis-in-sap"></a>對 SAP 中的 Bapi 的作業
商務應用程式發展介面 (BAPI) 是一種方法可以由外部處理序呼叫的 SAP 商務物件。 Bapi 是 SAP 系統上的交易。  
  
 [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] BAPI 呼叫的輸出方向的支援。 它會呈現 Bapi 有兩種：  
  
- **以 RFC**。 您可以叫用 BAPI 直接叫用適當的 RFC。  
  
- **為商務物件方法**。 配接器為了方便起見，可協助您擷取中繼資料，當您使用商務物件方法呈現 Bapi[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。  
  
> [!IMPORTANT]
>  以 RFC 或商務物件; 方法，您可以叫用的介面卡上的 BAPI但是，不論您如何叫用 BAPI 的介面卡上，它一律會叫用 BAPI SAP 上的透過 RFC 介面。  
  
 配接器支援 BAPI 交易。 SAP 的 BAPI 交易模型可讓使用者結合的工作 (LUW) 的一個邏輯單元的數個的 Bapi。 SAP LUW 包含參與交易，包括更新資料庫的所有步驟。  
  
 在本節中的主題將說明 Bapi 商務物件的呈現方式和配接器如何支援 BAPI 交易 (LUWs)。  
 
  
## <a name="bapi-operations-as-business-object-methods"></a>BAPI 作業 （如商務物件方法）  
 因為商務物件方法，以便於協助您擷取中繼資料，當您使用配接器瀏覽 Bapi[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 配接器一定會使用 RFC 介面的 SAP 系統上的 Bapi。  
  
 配接器會呈現 Bapi 依名稱做為在適當的商務物件的作業輸出的作業。 商務物件會收集由配接器的 BAPI 類別目錄節點下的功能群組。 (您可以瀏覽或搜尋商務物件和之下的 Bapi **BAPI**當您使用的節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。)  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] Bapi 上支援下列：  
  
- 匯入參數  
  
- 匯出參數  
  
- 變更參數  
  
- 資料表參數  
  
  如需有關用來做為商務物件方法的 Bapi 的 SOAP 動作與訊息結構的詳細資訊，請參閱[BAPI 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-bapi-operations.md)。  
  
## <a name="bapi-transactions"></a>BAPI 交易  
 當您叫用 BAPI 時，但它一定是 LUW 上 SAP 系統的一部分。 是否為 RFC 或商務物件的方法叫用 BAPI，也是如此。 RFC SDK 會將所有透過相同的 SAP 連線的相同 LUW 一部分傳送的 Bapi。 呼叫之後認可或復原交易上的連接，透過連線傳送的下一個 BAPI 會開始新 LUW。  
  
 您可以呼叫 BAPI_TRANSACTION_COMMIT 或 BAPI_TRANSACTION_ROLLBACK 認可或回復交易。 配接器會呈現這些兩個 Bapi:  
  
- 在以 RFC 作業的基礎節點。  
  
- 在每個商務物件。  
  
  您可以確保，所有傳送相同的 SAP 連線 （包括認可或回復交易的呼叫），以控制在交易中的 Bapi。 您可以在中來這樣做：  
  
- 使用 BizTalk 解決方案**ConnectionState**訊息內容屬性，以確保在交易中的 Bapi 會傳送使用相同的連線。 這個屬性會顯示由配接器，並提供您明確控制用來傳送訊息，BizTalk 協調流程中的連接。  
  
   執行 BAPI 交易使用 BizTalk Server[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援下列的訊息內容屬性。  
  
  |欄位|描述|  
  |-----------|-----------------|  
  |OPEN|開啟交易的新通道。|  
  |重複使用|重複使用交易的現有通道。|  
  |CLOSE|認可交易，並關閉現有的通道。|  
  |ABORT|中止交易，並關閉現有的通道。|  
  
   如需詳細資訊，請參閱 < [SAP 使用 BizTalk Server 中執行 BAPI 交易](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md)。  
  
  > [!NOTE]
  >  請確定您設定**EnableBizTalkCompatibilityMode**執行使用 BizTalk Server 的交易時，繫結屬性。  
  
- 藉由確保在交易中的 Bapi 使用相同的 WCF 用戶端傳送的 WCF 服務模型方案。 如需詳細資訊，請參閱 < [SAP 使用 WCF 服務模型中的 叫用 Bapi](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md)。  
  
- WCF 通道模型的解決方案藉由確保在交易中的 Bapi 會透過相同的 WCF 通道傳送。 如需詳細資訊，請參閱 <<c0> [ 使用 WCF 通道模型開發應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)。  
  
### <a name="limitations-on-bapi-transactions"></a>BAPI 交易的限制  
 BAPI 交易，適用下列限制：  
  
- 您不可能進行一個 LUW 內相同的執行個體上的兩個的寫入存取。 例如，您無法建立訂單，並在相同交易中更新它。  
  
- 執行 BAPI 交易使用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，必須透過傳送埠的單一主機執行個體傳送的所有訊息。  
  
- 如果執行個體是建立、 更新或刪除使用 BAPI 的寫入，讀取 BAPI 無法檢視最新的資料，直到體會認可寫入 BAPI。  
  
- 外部用戶端叫用 LUW 應該在相同的 SAP 連接上呼叫 LUW 包含的所有 Bapi。  
  
> [!IMPORTANT]
>  屬於版本 3.1 的 Bapi 呼叫 COMMIT WORK，做為其實作的一部分。 這表示，（因為它們將會認可交易），這些 Bapi 不能包含其他 LUW 中的 Bapi。 如需詳細資訊，請參閱 SAP 文件。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)