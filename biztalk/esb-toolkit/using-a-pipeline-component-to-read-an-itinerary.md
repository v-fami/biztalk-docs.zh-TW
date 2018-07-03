---
title: 使用管線元件讀取路線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e3b40c7-0f17-4d33-a26f-f51346a98be5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c03e4e48b125d7a8236c66ce36e458dd2d51a6f7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991119"
---
# <a name="using-a-pipeline-component-to-read-an-itinerary"></a>使用管線元件讀取路線
接收管線中的訊息可以包含其定義其處理需求 （用戶端路線） 的 SOAP 標頭中的中繼資料。 圖 1 說明如何使用 ESB 路線和 ESB 發送器管線元件。  

 ![管線元件讀取](../esb-toolkit/media/ch4-pipelinecomponentread.gif "第 4 章第 PipelineComponentRead")  

 **圖 1**  

 **ESB 路線管線元件的範例**  

 ESB 路線管線元件可用來擷取中繼資料，從訊息內容屬性，可以定義 ESB 所套用的處理。  

 下列各節說明每個元件所執行的步驟。  

## <a name="esb-itinerary-pipeline-component-process-steps"></a>ESB 路線的管線元件的程序步驟  
 [圖 1] 所示的範例中，在 ESB 路線管線元件會執行下列步驟：  

- 它會讀取路線 SOAP 標頭。 提交的合作對象設定路線他或她將訊息提交時，填入 SOAP 標頭。 BizTalk 訊息內容屬性的一系列代表 SOAP 標頭;這些屬性會因所使用的 Web 服務配接器的類型而有所不同。 以下是相關的 Web 服務配接器：  

  - **WCF 配接器。** 此配接器會剖析 SOAP 標頭，並於其中填入下表所列的 BizTalk 訊息內容屬性。  


    |                                  屬性                                  |
    |------------------------------------------------------------------------------|
    |                             **名稱 = 路線**                             |
    | **命名空間 = http://schemas.microsoft.biztalk.practices.esb.com/itinerary** |

    > [!NOTE]
    >  根據預設，Windows Communication Foundation (WCF) 配接器會使用名為的 ItineraryDescription.xsd （此結構描述用來產生 ESB 路線 SOAP 標頭） 的結構描述根名稱做為 BizTalk 內容**名稱**引數，也會使用結構描述的目標命名空間，做為 BizTalk 內容**命名空間**引數。  

  - **SOAP 配接器。** 此配接器會剖析 SOAP 標頭，並於其中填入下表所列的 BizTalk 訊息內容屬性。  


    |                              屬性                              |
    |----------------------------------------------------------------------|
    |                         **名稱 = 路線**                         |
    | **命名空間 = http://schemas.microsoft.com/BizTalk/2003/SOAPHeader** |

    > [!NOTE]
    >  根據預設，SOAP 配接器會使用名為的 Itinerary.xsd （此結構描述用來產生 ESB 路線 SOAP 標頭） 的結構描述根名稱做為 BizTalk 內容**名稱**引數，並使用的 SOAP 標頭，因為命名空間BizTalk 內容**命名空間**引數。  

- 它從訊息內容中移除原始的路線值。  

- 它會驗證路線，並設定特定的屬性，以設定預設值，如果它們是在路線; 為 null例如：  

  - 如果服務計數小於 1，元件就會擲回例外狀況。  

  - 元件會設定使用的服務計數，而識別碼值的路線根屬性 (**Uuid**)、 開始時間 (**BeginTime**)，以及是否這是單向或雙向的要求 (**IsRequestResponse**)。  

  - 元件會驗證服務、 設定的識別碼，設定目前的服務執行個體 （接下來處理服務），並驗證任何相關聯的解析程式的資料。  

  - 元件會設定 BizTalk 區段的路線，使用下列屬性：  

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
    |**ServiceType**|設定為 **協調流程**或**傳訊**|  
    |**IsRequestResponse**|設定為 **真**或**False**|  
    |**ServiceState**|若要設定**暫止**|  

## <a name="esb-dispatcher-pipeline-component-process-steps"></a>ESB 發送器管線元件處理程序步驟  
 在 [圖 1] 所示的範例中，ESB 發送器管線元件會執行下列步驟：  

- 管理任何類型的路線的步驟執行**Messaging**和前進的路線。 ESB 發送器元件是位置感知和執行訊息處理循環，這可能是根據其位置的邏輯**接收輸入、 傳送傳輸**，**傳送輸入**，或**接收輸出**。 ESB 發送器管線元件會叫用 ESB 路線傳訊服務的 Esb.config 檔案中指定。 根據預設，此元件進行路由與轉換的組態屬性會與下列服務相關聯：  

  - **Microsoft.Practices.ESB.Services.Transform。** 此服務會執行對傳入訊息的承載的 BizTalk 對應。 服務會驗證轉換需求，並更新包含的文件規格名稱和訊息類型的 BizTalk 內容屬性。 ESB 發送器執行這項服務，如果這是轉換服務的名稱，在 ESB 發送器管線元件的對應屬性中所顯示的樣子。  

  - <strong>Microsoft.Practices.ESB.Services.Routing。</strong>這項服務使用的解析程式和配接器提供者架構來設定適當的端點路由資訊。 ESB 發送器執行這項服務，如果這是路由服務的名稱，在 ESB 發送器管線元件的對應屬性中所顯示的樣子。
