---
title: "作業中 SAP Rfc |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd4ebbb33e9f9791589a3ef271412c8ae20090f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-rfcs-in-sap"></a>作業中 SAP Rfc
您可以使用[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]同時 RFC 用戶端和 RFC 伺服器。 在 RFC 用戶端的情況下，您的應用程式的叫用 Rfc SAP 系統上叫用 RFC 作業上[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 在 RFC 伺服器案例中的 SAP 系統會叫用 Rfc 上[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，，接著，會叫用 RFC 成為您的應用程式的作業。  
  
## <a name="rfc-operations"></a>RFC 作業  
 Rfc 依名稱顯示為 RFC 的中繼資料類別目錄的節點下的讀取作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 (您可以瀏覽或搜尋在 Rfc **RFC**節點，當您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。)  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可以介面只在它可以為其擷取中繼資料從 SAP 系統的 Rfc。 配接器使用 RFC SDK 擷取此中繼資料，因此它無法介面包含由 RFC SDK 不支援的資料型別參數的 Rfc。 例如，配接器無法介面包含 ITAB II 類型結構或資料表的 Rfc。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援下列 Rfc 上：  
  
-   匯入參數  
  
-   匯出參數  
  
-   變更參數  
  
 如需 rfc 配接器使用的 SOAP 動作與訊息結構的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。  
  
## <a name="invoking-rfcs-on-an-sap-system"></a>SAP 系統上叫用的 Rfc  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] Rfc 呈現為個別的作業在 SAP 系統上進行 RFC 的名稱。 要叫用的 RFC，SAP 系統上，您將叫用配接器的適當具名的 RFC 作業。  
  
 如需詳細資訊：  
  
-   叫用 RFC 使用 BizTalk Server，請參閱[使用 BizTalk server 叫用的 Rfc](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)。  
  
-   叫用 RFC 使用 WCF 服務模型，請參閱[SAP 使用 WCF 服務模型中的 叫用 Rfc](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md)。  
  
-   叫用 RFC 使用 WCF 通道模型，請參閱[SAP 系統所使用 WCF 通道模型上的叫用作業](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)。  
  
## <a name="receiving-inbound-rfc-calls-from-an-sap-system"></a>從 SAP 系統接收輸入的 RFC 呼叫  
 很可能適用於 SAP 做為用戶端，並叫用外部 RFC 伺服器上的函式模組。 這項功能可讓：  
  
-   SAP 到外部系統推播通知，而不需要藉由呼叫 Rfc 持續輪詢通知的 SAP 外部系統。  
  
-   SAP 系統之外的商務邏輯的實作。 SAP 系統就可以在 RFC 伺服器呼叫外部程式。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可以做為 RFC 伺服器從 SAP 系統接收這類輸入的 RFC 呼叫。 當配接器會從 SAP 接收 RFC 呼叫時，它會叫用該 RFC 作業，在您的應用程式。  
  
 若要執行 RFC 伺服器配接器：  
  
-   必須宣告 RFC，SAP 系統上。 這是讓配接器可以擷取描述從 SAP 系統的 RFC 的中繼資料。 RFC 實際上是在您的應用程式中實作的。  
  
-   配接器必須向 SAP 閘道上的 RFC 目的地。 註冊為基礎的邏輯名稱呼叫的程式識別碼。 您提供的連線 URI 指定的程式識別碼，SAP 閘道和 SAP 此註冊的伺服器中的參數。  
  
 下列範例顯示叫用程式 ID，MYDEST 透過 RFC 所需的 ABAP 程式碼。  
  
```  
CALL FUNCTION ‘ABC’ DESTINATION ‘MYDEST’  
```  
  
 如需詳細資訊：  
  
-   接收 RFC 伺服器呼叫使用 BizTalk Server，請參閱[接收輸入 RFC 呼叫使用 BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md)。  
  
-   接收 RFC 伺服器呼叫使用 WCF 服務模型，請參閱[接收輸入 RFC 呼叫中使用 WCF 服務模型的 SAP](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md)。  
  
-   接收 RFC 伺服器呼叫使用 WCF 通道模型，請參閱[接收輸入作業使用的 WCF 通道模型的 SAP 系統從](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)。  
  
## <a name="special-rfc-operations"></a>特殊 RFC 作業  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也可以執行 SAP 系統上的某些特殊 RFC 作業。 一個這類作業是 RfcGetAttributes。  
  
-   **RfcGetAttributes**。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會使用這項作業取得 RFC 連線參數，例如系統識別碼、 夥伴的字碼頁和語言的相關資訊。 這項作業時才可使用**RFC**節點時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
 如需訊息結構和叫用 RfcGetAttributes 作業 SAP 系統上的 SOAP 動作的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)