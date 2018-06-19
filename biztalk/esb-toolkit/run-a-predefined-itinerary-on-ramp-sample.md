---
title: 執行預先定義的路線上手範例 |Microsoft 文件
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
ms.openlocfilehash: 38320cc6877815ccbf7b078190a3c2be1c6f74b0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976676"
---
# <a name="run-a-predefined-itinerary-on-ramp-sample"></a>執行預先定義的路線上手範例
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含 20 預先定義的行程使用案例可以執行。 如需這些使用案例，請參閱[路線案例範例](../esb-toolkit/the-sample-itinerary-scenarios.md)。  
  
> [!NOTE]
>  執行範例之前，您必須以手動方式匯適當路線繫結檔案從 \Source\Samples\Itinerary\Install\Binding 資料夾 GlobalBank.ESB BizTalk 應用程式。 此繫結檔案會重設兩個動態傳送埠上的屬性。 匯入名為 GlobalBank.ESB.Itinerary_Bindings.xml 繫結檔案。  
  
### <a name="to-run-one-of-the-pre-defined-itinerary-on-ramp-samples"></a>若要執行的其中一個預先定義的行程上手範例  
  
1.  如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。  
  
2.  在 Windows 檔案總管 中，開啟子資料夾 \Source\Samples\Itinerary\Source\ESB。您已安裝 BizTalk ESB 工具組範例中，並再啟動應用程式的 Itinerary.Test\bin\Debug 名為 Esb.Itinerary.Test.exe。  
  
3.  按一下**LoadItinerary**按鈕，然後再選取 範例路線名為 TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml \Source\Samples\Itinerary\Itineraries 資料夾中。  
  
4.  在**Web 服務選項**區段中，選取**雙向服務**核取方塊。 這會指示測試用戶端執行的要求-回應路線的服務作業。  
  
5.  （選擇性）選取**使用 WCF 服務**核取方塊，如果您想要使用 OnRamp.Itinerary.Response.WCF 應用程式接收位置而不使用預設 OnRamp.Itinerary.Response.SOAP 接收位置。  
  
6.  按一下**LoadMessage**按鈕，然後再從 \Source\Samples\Itinerary\Test\Data 資料夾選取 NAOrderDoc.xml 範例訊息。  
  
7.  按一下**SubmitRequest**  按鈕，將要求傳送至路線上手服務。 圖 1 顯示的結果。  
  
 ![在遞增路線](../esb-toolkit/media/ch6-itineraryonramp.gif "第 6 章第 ItineraryOnRamp")  
  
 **圖 1**  
  
 **行程上手用戶端應用程式執行的其中一個行程上手範例**  
  
 路線的定義中指定的服務名稱對應到直接**ServiceName**服務範例會訂閱的屬性。 在上一個程序 (TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml) 中執行路線範例中，第一個執行的服務是執行轉換，協調流程服務。 路線的下列區段會指定此服務。  
  
```  
<Service uuid="" beginTime="" completeTime=""   
    name="Microsoft.Practices.ESB.Services.Transform"  
    type="Orchestration" state="Pending" isRequestResponse="false"  
    position="0" serviceInstanceId="" />  
```  
  
 在此協調流程服務**\<服務\>** 項目會指定直接繫結協調流程具有在圖 2 所顯示的篩選內容。 請注意，協調流程會訂閱只能有值的訊息**Microsoft.Practices.ESB.Services.Transform**如**ServiceName**內容屬性、 值**暫止**如**ServiceState**內容屬性和值的協調流程的**ServiceType**內容屬性。  
  
 ![篩選運算式](../esb-toolkit/media/ch6-filterexpression.gif "第 6 章第 FilterExpression")  
  
 **圖 2**  
  
 **直接繫結協調流程路線上手範例中所使用的篩選條件運算式**