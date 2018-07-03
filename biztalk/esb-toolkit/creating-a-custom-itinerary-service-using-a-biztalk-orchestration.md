---
title: 建立自訂路線服務使用 BizTalk 協調流程 |Microsoft Docs
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
ms.openlocfilehash: aa36acc84358a8e91a0b9daaa4370270fb5860b1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988535"
---
# <a name="creating-a-custom-itinerary-service-using-a-biztalk-orchestration"></a>建立自訂路線服務使用 BizTalk 協調流程
屬於路線 framework[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援路線使用協調流程的步驟執行。 您可以實作自訂路線服務為 Microsoft BizTalk Server 協調流程根據功能需求，其中可能包含下列：  
  
- 多個服務引動過程 (如所示[安裝和執行分散-集中範例](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md))  
  
- 通訊協定中繼和訊息相互關聯 (例如，HTTP-MQSeries)  
  
- 複雜的路由決策，根據訊息豐富 」，從外部資料來源  
  
- 商務處理邏輯  
  
  使用 BizTalk Server 協調流程實作的每個路線服務會負責下列各項：  
  
- 例外狀況和錯誤處理使用 ESB 例外狀況處理的架構或支援重新提交 （單向路線） 的選擇性自訂例外狀況處理常式  
  
- 前進的路線，並發行輸出訊息透過 BizTalk Server，這樣可以在執行下一個步驟中，路線服務  
  
#### <a name="to-create-a-custom-itinerary-service-using-a-biztalk-server-orchestration"></a>若要建立自訂路線服務使用的 BizTalk Server 協調流程  
  
1. 建立新的 BizTalk Server 專案包含新的協調流程;比方說，MyCustomeItineraryService.odx。  
  
2. 新增下列組件的參考：  
  
   -   **Microsoft.Practices.ESB.Itinerary**  
  
   -   **Microsoft.Practices.ESB.Itinerary.Schemas**  
  
   -   **Microsoft.Practices.ESB.ExceptionHandling**  
  
   -   **Microsoft.Practices.ESB.ExceptionHandling.Faults**  
  
3. 定義邏輯直接繫結協調流程中接收埠，並啟動的接收 」 圖形。  
  
4. 定義訂用帳戶篩選器，以啟動訊息路線內容從協調流程，以便在協調流程執行**MyCustomItineraryService**步驟。 下列程式碼會顯示適當的篩選器的範例。  
  
   ```csharp  
   (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName   
       == "MyCustomItineraryService")   
   && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState == "Pending")  
   && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType   
       == "Orchestration")  
   ```  
  
5. 定義類型的協調流程**Microsoft.Practices.ESB.Itinerary.ItineraryStep**。 下列程式碼所示，則您可以加入會填入此變數，協調流程運算式活動。  
  
   ```csharp  
   // Retrieve the current itinerary step.  
   itinerary = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryWrapper();  
   step = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryStepWrapper();  
  
   itinerary.Itinerary = Microsoft.Practices.ESB.Itinerary.ItineraryOMFactory.Create(InboundMessage);  
   step.ItineraryStep = itinerary.Itinerary.GetItineraryStep(InboundMessage);  
  
   ```  
  
6. 將您的自訂實作新增至建立外寄訊息的下一步 的路線步驟; 路線比方說，OutboundMsg。  
  
7. 前進的路線，使用下列運算式活動會從輸入訊息的訊息內容。  
  
   ```csharp  
   OutboundMessage(*) = InboundMessage(*);   
   itinerary.Itinerary.Advance(OutboundMessage, itineraryStep.ItineraryStep);  
   ```  
  
8. 透過直接繫結傳送埠以啟用 [下一步] 的路線服務中傳送傳出訊息與更新的路線。  
  
   如需有關如何實作自訂路線服務使用 BizTalk Server 協調流程的詳細資訊，請參閱 <<c0> [ 安裝和執行路線入口範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)和[安裝及執行分散-集中範例](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md)。