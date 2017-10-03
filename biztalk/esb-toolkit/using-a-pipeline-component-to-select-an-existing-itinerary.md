---
title: "使用管線元件，選取現有的行程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b93c5cb6-071f-485d-b0bb-22f95bafa3d0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a733da2348de13120ce37a205b77d2e8194c7790
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-pipeline-component-to-select-an-existing-itinerary"></a>選取現有的行程中使用的管線元件
## <a name="esb-itinerary-selector-pipeline-component"></a>ESB 路線的選取器管線元件  
 使用泛型路線上-坡道提升提交的訊息會送出沒有路線的標頭。 若要解決適當的路線，並將它附加到內送訊息，在遞增必須提供一套機制，可以設定為從中央儲存機制存取行程。  
  
 ESB 行程選取器管線元件會使用解析程式連接字串，搭配特殊的解析程式，若要解決伺服器端路線 （依預設，SQL Server） 儲存在中央儲存機制中的內容。  
  
 名稱和版本 （如 SOAP 標頭中所表示），用戶端要求路線 ESB 行程選取器管線元件中 WCF 上-坡道提升路線靜態解析程式搭配使用時，會從訊息內容和用來選取適當的路線。  
  
 根據預設，ESB 行程選取器管線元件會位於下列管線：  
  
-   ItinerarySelectReceive  
  
-   ItinerarySelectReceivePassthrough  
  
-   ItinerarySelectReceiveXml  
  
-   ItinerarySelectSendReceive  
  
 下列章節說明每個元件所執行的步驟。  
  
## <a name="esb-itinerary-selector-pipeline-component-processing-steps"></a>ESB 路線的選取器管線元件處理步驟  
 ESB 行程選取器管線元件會執行下列步驟：  
  
-   正在提交的合作對象送出訊息，以進行處理。 路線選取器元件會使用解析程式指定為屬性設定的連接字串，由開發人員，判斷並從路線的存放區，並根據訊息內容或內容中選取適當的路線。  
  
-   它會驗證路線，並設定特定的屬性，以設定預設值，如果它們是在路線; null例如：  
  
    -   如果服務計數小於 1，元件就會擲回例外狀況。  
  
    -   元件會設定服務計數，識別項使用的值的路線根屬性 (**Uuid**)、 開始時間 (**BeginTime**)，以及是否這是單向或雙向的要求 (**IsRequestResponse**)。  
  
    -   元件會驗證服務、 設定的識別碼，設定目前的服務執行個體 （接下來處理服務），和會驗證任何相關聯的解析程式。  
  
    -   元件會設定 Microsoft BizTalk Server 區段的路線，使用下列屬性：  
  
        -   **correlationToken**  
  
        -   **reqRespTransmitPipelineID**  
  
        -   **interchangeId**  
  
        -   **receiveInstanceId**  
  
        -   **epmRRCorrelationToken**  
  
    -   元件會使用系統 Properties.xsd 結構描述中定義的屬性如下表所示的 BizTalk 訊息內容屬性寫入已修改的路線。  
  
        |屬性|  
        |----------------|  
        |**名稱 = ItineraryHeader**|  
        |**命名空間 = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties**|  
  
    -   元件會升級使用系統 Properties.xsd 結構描述中定義的值如下表所示的四個 BizTalk 內容屬性。  
  
        |屬性|值|  
        |--------------|-----------|  
        |**ServiceName**|目前行程中定義的服務執行個體的名稱。|  
        |**ServiceType**|設定為 **協調流程**或**傳訊**。|  
        |**IsRequestResponse**|設定為  **True**或**False**。|  
        |**ServiceState**|設定為**暫止**。|  
  
## <a name="esb-dispatcher-pipeline-component-process-steps"></a>ESB 發送器管線元件處理步驟  
 ESB 發送器管線元件會執行下列步驟：  
  
-   它會管理任何類型的路線的步驟執行**傳訊**，並往前移路線。 ESB 發送器元件是位置感知和執行在訊息處理循環，這可能會根據其位置的邏輯**接收輸入**，**傳送傳輸**，**傳送輸入**，或**接收輸出**。 ESB 發送器管線元件會叫用路線 ESB Esb.config 檔案中指定訊息服務。 根據預設，此路由和轉換元件的組態屬性與相關聯的下列服務：  
  
    -   **Microsoft.Practices.ESB.Services.Transform**。 此服務會執行對傳入訊息的裝載 BizTalk 對應。 服務驗證的轉換需求，並更新 BizTalk 內容屬性包含文件規格名稱和訊息類型。 ESB 發送器會執行這項服務，才出現在 ESB 發送器管線元件的對應屬性，這會是轉換服務的名稱。  
  
    -   **Microsoft.Practices.ESB.Services.Routing。** 此服務會解析器和配接器提供者架構設定適當的端點的路由資訊。 ESB 發送器會執行這項服務，才出現在 ESB 發送器管線元件的對應屬性，這會是路由服務的名稱。