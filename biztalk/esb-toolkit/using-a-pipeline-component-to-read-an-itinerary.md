---
title: "使用管線元件讀取行程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e3b40c7-0f17-4d33-a26f-f51346a98be5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bceec4df732247be043e006b52c7abbfbf6a6b24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-pipeline-component-to-read-an-itinerary"></a>使用管線元件讀取行程
接收管線中的訊息可以包含其定義了其處理需求 （用戶端路線） 的 SOAP 標頭中的中繼資料。 圖 1 說明如何使用 「 ESB 行程和 ESB 發送器管線元件。  
  
 ![管線元件讀取](../esb-toolkit/media/ch4-pipelinecomponentread.gif "第 4 章第 PipelineComponentRead")  
  
 **圖 1**  
  
 **ESB 行程管線元件的範例**  
  
 ESB 行程管線元件可以用來擷取中繼資料，從訊息內容屬性，可以定義 ESB 所套用的處理。  
  
 下列章節說明每個元件所執行的步驟。  
  
## <a name="esb-itinerary-pipeline-component-process-steps"></a>ESB 路線的管線元件處理序的步驟  
 在圖 1 所示的範例中，ESB 行程管線元件會執行下列步驟：  
  
-   它會讀取行程 SOAP 標頭。 正在提交的合作對象，設定路線他或她將訊息提交時，填入 SOAP 標頭。 BizTalk 訊息內容屬性的一系列代表 SOAP 標頭。這些屬性會因所使用的 Web 服務配接器類型而有所不同。 以下是相關的 Web 服務配接器：  
  
    -   **WCF 配接器。** 此配接器會剖析 SOAP 標頭，並於其中填入下表所列的 BizTalk 訊息內容屬性。  
  
        |屬性|  
        |----------------|  
        |**名稱 = 路線**|  
        |**命名空間 = http://schemas.microsoft.biztalk.practices.esb.com/itinerary**|  
  
        > [!NOTE]
        >  根據預設，Windows Communication Foundation (WCF) 配接器會使用名為的 ItineraryDescription.xsd （此結構描述用來產生 ESB 行程 SOAP 標頭） 的結構描述的根名稱做為 BizTalk 內容**名稱**引數，它是使用 BizTalk 內容結構描述的目標命名空間和**命名空間**引數。  
  
    -   **SOAP 配接器。** 此配接器會剖析 SOAP 標頭，並於其中填入下表所列的 BizTalk 訊息內容屬性。  
  
        |屬性|  
        |----------------|  
        |**名稱 = 路線**|  
        |**命名空間 = http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**|  
  
        > [!NOTE]
        >  根據預設，SOAP 配接器會使用名為的 Itinerary.xsd （此結構描述用來產生 ESB 行程 SOAP 標頭） 的結構描述的根名稱做為 BizTalk 內容**名稱**引數，並使用做為 SOAP 標頭的命名空間BizTalk 內容**命名空間**引數。  
  
-   會從訊息內容中移除原始路線的值。  
  
-   它會驗證路線，並設定特定的屬性，以設定預設值，如果它們是在路線; null例如：  
  
    -   如果服務計數小於 1，元件就會擲回例外狀況。  
  
    -   元件會設定服務計數，識別項使用的值的路線根屬性 (**Uuid**)、 開始時間 (**BeginTime**)，以及是否這是單向或雙向的要求 (**IsRequestResponse**)。  
  
    -   元件會驗證服務、 設定的識別碼，設定目前的服務執行個體 （接下來處理服務），和會驗證任何相關聯的解析程式。  
  
    -   元件會先設定 BizTalk 區段的路線，使用下列屬性：  
  
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
        |**ServiceType**|設定為 **協調流程**或**傳訊**|  
        |**IsRequestResponse**|設定為  **True**或**False**|  
        |**ServiceState**|設定為**暫止**|  
  
## <a name="esb-dispatcher-pipeline-component-process-steps"></a>ESB 發送器管線元件處理步驟  
 在圖 1 所示的範例中，ESB 發送器管線元件會執行下列步驟：  
  
-   它會管理任何類型的路線的步驟執行**傳訊**，並往前移路線。 ESB 發送器元件是位置感知和執行在訊息處理循環，這可能會根據其位置的邏輯**接收輸入，傳送傳輸**，**傳送輸入**，或**接收輸出**。 ESB 發送器管線元件會叫用路線 ESB Esb.config 檔案中指定訊息服務。 根據預設，此路由和轉換元件的組態屬性與相關聯的下列服務：  
  
    -   **Microsoft.Practices.ESB.Services.Transform。** 此服務會執行對傳入訊息的裝載 BizTalk 對應。 服務驗證的轉換需求，並更新 BizTalk 內容屬性包含文件規格名稱和訊息類型。 ESB 發送器會執行這項服務，才出現在 ESB 發送器管線元件的對應屬性，這會是轉換服務的名稱。  
  
    -   **Microsoft.Practices.ESB.Services.Routing。**此服務使用的解析程式和配接器提供者架構設定適當的端點的路由資訊。 ESB 發送器會執行這項服務，才出現在 ESB 發送器管線元件的對應屬性，這會是路由服務的名稱。