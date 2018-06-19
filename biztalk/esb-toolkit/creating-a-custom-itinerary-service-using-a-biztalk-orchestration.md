---
title: 建立自訂路線服務使用 BizTalk 協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bd7ed38-02a3-41b1-9990-754d5539f15e
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 723c0bc93192267f404d42e7fe859bb37ea59895
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289806"
---
# <a name="creating-a-custom-itinerary-service-using-a-biztalk-orchestration"></a>建立自訂路線服務使用 BizTalk 協調流程
屬於路線 framework[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援的計劃使用協調流程的步驟執行。 您可以實作自訂的路線服務為 Microsoft BizTalk Server 協調流程根據功能需求，這可能包括下列各項：  
  
-   多個服務引動過程 (所示[安裝及執行分散-集中範例](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md))  
  
-   通訊協定中繼和訊息相互關聯 (例如，MQSeries HTTP)  
  
-   複雜的路由決策根據訊息豐富 」，從外部資料來源  
  
-   商務處理邏輯  
  
 使用 BizTalk Server 協調流程實作的每個路線服務會負責下列各項：  
  
-   例外狀況和錯誤處理使用 ESB 例外狀況處理的架構或選擇性的自訂例外狀況處理常式，支援重新提交 （單向旅）  
  
-   前進的路線，如此路線服務下一步可以執行發行輸出訊息透過 BizTalk Server  
  
#### <a name="to-create-a-custom-itinerary-service-using-a-biztalk-server-orchestration"></a>若要建立自訂路線服務使用的 BizTalk Server 協調流程  
  
1.  建立包含新的協調流程; 新的 BizTalk Server 專案例如，MyCustomeItineraryService.odx。  
  
2.  加入下列組件的參考：  
  
    -   **Microsoft.Practices.ESB.Itinerary**  
  
    -   **Microsoft.Practices.ESB.Itinerary.Schemas**  
  
    -   **Microsoft.Practices.ESB.ExceptionHandling**  
  
    -   **Microsoft.Practices.ESB.ExceptionHandling.Faults**  
  
3.  定義邏輯直接繫結協調流程中接收埠，並啟動的接收 」 圖形。  
  
4.  定義要啟動訊息路線內容從協調流程，使協調流程執行的訂用帳戶篩選**MyCustomItineraryService**步驟。 下列程式碼顯示適當的篩選器的範例。  
  
    ```csharp  
    (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName   
        == "MyCustomItineraryService")   
    && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState == "Pending")  
    && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType   
        == "Orchestration")  
    ```  
  
5.  定義類型的協調流程**Microsoft.Practices.ESB.Itinerary.ItineraryStep**。 運算式將活動新增至協調流程會填入此變數，如下列程式碼所示。  
  
    ```csharp  
    // Retrieve the current itinerary step.  
    itinerary = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryWrapper();  
    step = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryStepWrapper();  
  
    itinerary.Itinerary = Microsoft.Practices.ESB.Itinerary.ItineraryOMFactory.Create(InboundMessage);  
    step.ItineraryStep = itinerary.Itinerary.GetItineraryStep(InboundMessage);  
  
    ```  
  
6.  將您的自訂實作新增至路線建立外寄訊息路線接下來的步驟。例如，OutboundMsg。  
  
7.  前進的路線，使用下列的運算式活動，會使用從輸入訊息的訊息內容。  
  
    ```csharp  
    OutboundMessage(*) = InboundMessage(*);   
    itinerary.Itinerary.Advance(OutboundMessage, itineraryStep.ItineraryStep);  
    ```  
  
8.  透過直接繫結傳送埠以啟用 下一步路線服務傳送外寄訊息與更新的路線。  
  
 如需有關如何實作自訂路線服務使用 BizTalk Server 協調流程的詳細資訊，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)和[安裝及執行分散-集中範例](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md)。