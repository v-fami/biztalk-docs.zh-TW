---
title: 執行預先定義的路線入口範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4400193-20ac-479a-8bf9-b1c99eb35231
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e428a9106582e5bad3408cfb6643cc5da21ac74
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996583"
---
# <a name="run-a-predefined-itinerary-on-ramp-sample"></a>執行預先定義的路線入口範例
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含 20 預先定義的路線使用案例可以執行。 如需清單，這些使用案例，請參閱 <<c0> [ 範例路線案例](../esb-toolkit/the-sample-itinerary-scenarios.md)。  
  
> [!NOTE]
>  執行範例之前，您必須手動匯適當路線的繫結檔案從 \Source\Samples\Itinerary\Install\Binding 資料夾 GlobalBank.ESB BizTalk 應用程式。 此繫結檔案中，會重設兩個動態傳送連接埠上的屬性。 匯入名為 GlobalBank.ESB.Itinerary_Bindings.xml 繫結檔案。  
  
### <a name="to-run-one-of-the-pre-defined-itinerary-on-ramp-samples"></a>若要執行的其中一個預先定義的路線入口範例  
  
1. 如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。  
  
2. 在 Windows 檔案總管中，開啟子資料夾 \Source\Samples\Itinerary\Source\ESB。Itinerary.Test\bin\Debug 您安裝 BizTalk ESB 工具組範例中，並接著啟動應用程式名為 Esb.Itinerary.Test.exe。  
  
3. 按一下  **LoadItinerary**按鈕，然後再選取名為 TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml \Source\Samples\Itinerary\Itineraries 資料夾中的範例路線。  
  
4. 在  **Web 服務選項**區段中，選取**雙向服務**核取方塊。 這會指示測試用戶端執行的要求-回應的路線服務作業。  
  
5. （選擇性）選取 **使用 WCF 服務**核取方塊，如果您想要使用 OnRamp.Itinerary.Response.WCF 的應用程式接收位置而非預設 OnRamp.Itinerary.Response.SOAP 接收位置。  
  
6. 按一下  **LoadMessage**按鈕，然後再選取 從 \Source\Samples\Itinerary\Test\Data 資料夾的 NAOrderDoc.xml 範例訊息。  
  
7. 按一下 [ **SubmitRequest** ] 按鈕，將要求傳送至路線入口匝服務。 圖 1 顯示的結果。  
  
   ![Ramp 上路線](../esb-toolkit/media/ch6-itineraryonramp.gif "第 6 章第 ItineraryOnRamp")  
  
   **圖 1**  
  
   **路線入口匝用戶端應用程式執行的其中一個路線入口範例**  
  
   路線的定義中指定服務的名稱直接對應至**ServiceName**範例所訂閱之服務的屬性。 在路線的範例，在先前的程序 (TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml) 中執行，第一個執行的服務會是協調流程為基礎的服務，就會執行轉換。 路線的下列區段會指定此服務。  
  
```  
<Service uuid="" beginTime="" completeTime=""   
    name="Microsoft.Practices.ESB.Services.Transform"  
    type="Orchestration" state="Pending" isRequestResponse="false"  
    position="0" serviceInstanceId="" />  
```  
  
 在此協調流程服務**\<服務\>** 項目會指定直接繫結協調流程具有 [圖 2] 所示的篩選屬性。 請注意，協調流程會訂閱只能有值的訊息**Microsoft.Practices.ESB.Services.Transform** for **ServiceName**內容屬性、 值**暫止**for **ServiceState**內容屬性，以及協調流程的值為**ServiceType**內容屬性。  
  
 ![篩選運算式](../esb-toolkit/media/ch6-filterexpression.gif "第 6 章第 FilterExpression")  
  
 **圖 2**  
  
 **直接繫結協調流程路線入口範例中所使用的篩選條件運算式**