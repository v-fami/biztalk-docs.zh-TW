---
title: 對 sap Rfc 的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, operations on RFCs
- adapters, operations on IDOCs
- RFC, receiving inbound RFC calls from an SAP system
- RFCs, invoking RFCs on an SAP system
- adapters, operations on BAPIs
- RFC client
- adapters, operations on tRFCs
- RFC server
ms.assetid: ca1b7b00-a9cf-41bc-b87c-2e7ce8cff65c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8219a063fed2c940cfcd2658937fde0686542d1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015357"
---
# <a name="operations-on-rfcs-in-sap"></a>對 sap Rfc 的作業
您可以使用[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]作為 RFC 用戶端和 RFC 伺服器。 在 RFC 用戶端的情況下，您的應用程式上叫用 Rfc SAP 系統上叫用 RFC 作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 在 RFC 伺服器案例中將 SAP 系統上叫用 Rfc [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，後者，接著叫用 RFC 做為您的應用程式上的作業。  
  
## <a name="rfc-operations"></a>RFC 作業  
 Rfc 依名稱顯示為 RFC 的中繼資料類別目錄節點下的讀取作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 (您可以瀏覽或搜尋在 Rfc **RFC**當您使用的節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。)  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可能會出現只在它可以為其擷取中繼資料從 SAP 系統的 Rfc。 配接器會使用 RFC SDK，來擷取此中繼資料，因此它無法呈現包含與 RFC SDK 不支援的資料型別參數的 Rfc。 例如，配接器無法呈現包含 ITAB II 類型結構或資料表的 Rfc。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援下列 Rfc 上：  
  
- 匯入參數  
  
- 匯出參數  
  
- 變更參數  
  
  如需有關用於 Rfc，配接器的 SOAP 動作與訊息結構的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。  
  
## <a name="invoking-rfcs-on-an-sap-system"></a>SAP 系統上叫用 Rfc  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] Rfc 會呈現為個別的作業，對 SAP 系統的 RFC 的名稱。 要叫用 RFC，SAP 系統上，您叫用適當命名的 RFC 作業的介面卡上。  
  
 如需詳細資訊：  
  
-   叫用 RFC 使用 BizTalk Server，請參閱[使用 BizTalk server 的叫用 Rfc](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)。  
  
-   叫用 RFC 使用 WCF 服務模型，請參閱[叫用 Rfc，SAP 使用 WCF 服務模型中](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md)。  
  
-   叫用 RFC 使用 WCF 通道模型，請參閱[SAP 系統所使用 WCF 通道模型上的 叫用作業](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)。  
  
## <a name="receiving-inbound-rfc-calls-from-an-sap-system"></a>從 SAP 系統的接收輸入的 RFC 呼叫  
 可以做為用戶端，並叫用函式模組外部的 RFC 伺服器上的 sap。 這項功能可讓：  
  
- 外部系統推播通知，而不需要外部系統不必持續輪詢藉由呼叫 Rfc 通知 SAP 的 SAP。  
  
- 外部 SAP 系統的商務邏輯的實作。 SAP 系統就可以在 RFC 伺服器呼叫外部程式。  
  
  [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可以做為從 SAP 系統接收這類輸入的 RFC 呼叫 RFC 伺服器。 當配接器會從 SAP 接收的 RFC 呼叫時，它會叫用該 RFC 作業，在您的應用程式。  
  
  若要執行 RFC 伺服器配接器：  
  
- 必須宣告 RFC，SAP 系統上。 這是讓配接器可以擷取描述從 SAP 系統的 RFC 的中繼資料。 RFC 實際上是在您的應用程式中實作。  
  
- 配接器必須向 SAP 閘道上的 RFC 目的地。 註冊為基礎的邏輯名稱，叫做程式 id。 您提供連線至指定的程式識別碼，而 SAP 閘道和 SAP 此註冊的伺服器的 URI 中的參數。  
  
  下列範例顯示叫用程式 ID、 MYDEST 透過 RFC 所需的 ABAP 程式碼。  
  
```  
CALL FUNCTION ‘ABC’ DESTINATION ‘MYDEST’  
```  
  
 如需詳細資訊：  
  
-   接收 RFC 伺服器呼叫使用 BizTalk Server，請參閱[接收輸入 RFC 呼叫所使用的 BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md)。  
  
-   接收 RFC 伺服器呼叫使用 WCF 服務模型，請參閱[接收輸入 RFC 呼叫中使用 WCF 服務模型的 SAP](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md)。  
  
-   接收 RFC 伺服器呼叫使用 WCF 通道模型，請參閱[接收輸入作業使用 WCF 通道模型的 SAP 系統從](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)。  
  
## <a name="special-rfc-operations"></a>特殊的 RFC 作業  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也可以執行某些特殊的 RFC 作業上的 SAP 系統。 這類的一項作業是 RfcGetAttributes。  
  
- **RfcGetAttributes**。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用這項作業，以取得資訊系統識別碼、 夥伴的字碼頁，等語言的 RFC 連線參數。 這項作業，會位於**RFC**時使用的節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
  如需有關訊息結構和叫用 RfcGetAttributes 作業上的 SAP 系統的 SOAP 動作的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)