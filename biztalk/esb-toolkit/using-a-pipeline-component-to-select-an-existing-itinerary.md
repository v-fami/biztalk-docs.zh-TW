---
title: 使用管線元件選取現有路線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b93c5cb6-071f-485d-b0bb-22f95bafa3d0
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2aceef4385652918ee7326709e7838776501e885
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975495"
---
# <a name="using-a-pipeline-component-to-select-an-existing-itinerary"></a>使用管線元件選取現有路線
## <a name="esb-itinerary-selector-pipeline-component"></a>ESB 路線選取器管線元件  
 使用泛型路線入口提交的訊息提交沒有路線的標頭。 若要解決適當的路線，並將它附加到內送訊息，匝道必須提供一種機制，可以設定為從中央儲存機制存取路線。  

 ESB 路線選取器管線元件會使用解析程式連接字串，搭配特製化的解析程式，若要解決伺服器端路線 （依預設，SQL Server） 儲存在中央儲存機制的內容。  

 名稱和版本 （如所表示的 SOAP 標頭），用戶端要求路線中 WCF 入口路線靜態解析程式搭配使用 ESB 路線選取器管線元件時，會從訊息內容和用來選取適當的路線。  

 根據預設，ESB 路線選取器管線元件會位於下列管線：  

- ItinerarySelectReceive  

- ItinerarySelectReceivePassthrough  

- ItinerarySelectReceiveXml  

- ItinerarySelectSendReceive  

  下列各節說明每個元件所執行的步驟。  

## <a name="esb-itinerary-selector-pipeline-component-processing-steps"></a>ESB 路線選取器管線元件處理步驟  
 ESB 路線選取器管線元件會執行下列步驟：  

- 提交的合作對象送出訊息，以進行處理。 路線選取器元件會指定為屬性設定的連接字串，讓開發人員的解析程式用以判斷並從路線的存放區，並根據訊息內容或內容中選取適當的路線。  

- 它會驗證路線，並設定特定的屬性，以設定預設值，如果它們是在路線; 為 null例如：  

  - 如果服務計數小於 1，元件就會擲回例外狀況。  

  - 元件會設定使用的服務計數，而識別碼值的路線根屬性 (**Uuid**)、 開始時間 (**BeginTime**)，以及是否這是單向或雙向的要求 (**IsRequestResponse**)。  

  - 元件會驗證服務、 設定的識別碼，設定目前的服務執行個體 （接下來處理服務），並驗證任何相關聯的解析程式的資料。  

  - 元件會設定 Microsoft BizTalk Server 區段的路線，使用下列屬性：  

    -   **correlationToken**  

    -   **reqRespTransmitPipelineID**  

    -   **interchangeId**  

    -   **receiveInstanceId**  

    -   **epmRRCorrelationToken**  

  - 元件會使用系統 Properties.xsd 結構描述中定義的屬性如下表所示的 BizTalk 訊息內容屬性寫入已修改的路線。  


    |                                           屬性                                           |
    |------------------------------------------------------------------------------------------------|
    |                                   **名稱 = ItineraryHeader**                                   |
    | **命名空間 = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties** |


  - 元件會升級使用系統 Properties.xsd 結構描述中定義的值如下表所示的四個 BizTalk 內容屬性。  

    |屬性|ReplTest1|  
    |--------------|-----------|  
    |**ServiceName**|路線中所定義的目前服務執行個體名稱。|  
    |**ServiceType**|設定為 **協調流程**或是**傳訊**。|  
    |**IsRequestResponse**|設定為 **真**或是**False**。|  
    |**ServiceState**|設定為**暫止**。|  

## <a name="esb-dispatcher-pipeline-component-process-steps"></a>ESB 發送器管線元件處理程序步驟  
 ESB 發送器管線元件會執行下列步驟：  

-   管理任何類型的路線的步驟執行**Messaging**和前進的路線。 ESB 發送器元件是位置感知和執行訊息處理循環，這可能是根據其位置的邏輯**收到傳入**，**傳送傳輸**，**傳送輸入**，或**接收輸出**。 ESB 發送器管線元件會叫用 ESB 路線傳訊服務的 Esb.config 檔案中指定。 根據預設，此元件進行路由與轉換的組態屬性會與下列服務相關聯：  

    -   **Microsoft.Practices.ESB.Services.Transform**。 此服務會執行對傳入訊息的承載的 BizTalk 對應。 服務會驗證轉換需求，並更新包含的文件規格名稱和訊息類型的 BizTalk 內容屬性。 ESB 發送器執行這項服務，如果這是轉換服務的名稱，在 ESB 發送器管線元件的對應屬性中所顯示的樣子。  

    -   **Microsoft.Practices.ESB.Services.Routing。** 此服務會使用解析程式和配接器提供者架構設定適當的端點路由資訊。 ESB 發送器執行這項服務，如果這是路由服務的名稱，在 ESB 發送器管線元件的對應屬性中所顯示的樣子。