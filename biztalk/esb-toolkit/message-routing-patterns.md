---
title: 訊息路由模式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d95c5ba0-122f-4793-bfce-a95830dfe094
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7233c5d5f5a3669cf23931afc29dfaac8548dc3d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022084"
---
# <a name="message-routing-patterns"></a>訊息路由模式
訊息路由模式定義訊息路由傳送至其目標端點經過實證的指導方針。 路由可以是靜態的設定的結果，或它可以動態設定根據一些準則和使用多種方法。  
  
## <a name="message-router"></a>訊息路由器  
 訊息路由器模式決定根據一組條件的訊息的收件者。 如需此模式的詳細說明，請參閱[訊息路由器](http://go.microsoft.com/fwlink/?LinkId=186844)([http://go.microsoft.com/fwlink/?LinkId=186844](http://go.microsoft.com/fwlink/?LinkId=186844)) 上的企業整合模式的站台。  
  
 實作此模式在路線設計工具是組成[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線的路由服務與單一內容為基礎的解析程式。 路線的路由服務會負責將訊息路由的屬性，Microsoft BizTalk 訊息內容中升級或明確的訊息路由。  
  
 您可以選擇路線的路由服務所提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，如下所示：  
  
- 定義路線的路由服務使用訊息的擴充項，BizTalk 管線，以使用路線設計工具中執行。  
  
- 定義要使用路線設計工具執行路由使用 BizTalk 傳送埠的協調流程中執行的協調流程擴充項與路線的路由服務。  
  
  路線的路由服務相關聯的解析程式決定訊息根據訊息內容的收件者。 您可以選擇從解析程式的支援內容為基礎的路由所提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，或者您可以實作自己的解析程式。  
  
  如需實作此模式中的範例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，請參閱下列資源：  
  
- [如何：使用 UDDI 繫結索引鍵搜尋解決服務端點](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  
  
- [如何：使用 UDDI 類別搜尋解決服務端點](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  
  
## <a name="content-based-router"></a>以內容為基礎的路由  
 以內容為基礎的路由器模式決定訊息根據訊息內容的收件者。 如需此模式的詳細說明，請參閱[內容型路由器](http://go.microsoft.com/fwlink/?LinkId=186839)([http://go.microsoft.com/fwlink/?LinkId=186839](http://go.microsoft.com/fwlink/?LinkId=186839)) 上的企業整合模式的站台。  
  
 實作此模式在路線設計工具是組成[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線的路由服務與單一內容為基礎的解析程式。 路線的路由服務會負責將訊息路由的屬性，BizTalk 訊息內容中升級或明確地將訊息路由傳送。  
  
 您可以選擇路線的路由服務所提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，如下所示：  
  
- 定義路線的路由服務使用訊息的擴充項，BizTalk 管線，以使用路線設計工具中執行。  
  
- 定義要使用路線設計工具，它會執行使用 BizTalk 傳送埠路由協調流程中執行的協調流程擴充項與路線的路由服務。  
  
- 定義與執行 BizTalk 管線，以使用路線設計工具中的 broker 訊息 extender 路線的 broker 服務。  
  
  路線的路由服務相關聯的解析程式決定訊息根據訊息內容的收件者。 您可以選擇下列的解析程式從該支援內容為基礎的路由所提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:  
  
- **XPATH 解析程式**。 藉由使用這個解析程式，您可以路由傳送訊息的內容使用 XPATH 查詢。  
  
- **BRE 解析程式**。 藉由使用這個解析程式，您可以從使用 BizTalk 規則引擎的訊息內容擷取路由資訊。  
  
- **訊息內容解析程式**。 藉由使用這個解析程式，您可以從擷取內容訊息的 BizTalk 訊息內容時與其相關聯[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線的 broker 服務。  
  
  > [!NOTE]
  >  除了上述的實作案例中，您可以開發自訂內容為基礎的解析程式和路線的路由解決方案，以傳訊為基礎或協調流程為基礎的服務。 在此情況下，您可能需要實作的擴充項[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線設計工具與交互操作的解析程式和路線服務。  
  
  例如此實作中，請參閱下列資源：  
  
- [安裝和執行路線入口範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)  
  
- [如何：使用已知訊息類型的商務規則原則來實作根據訊息內容決定路由](../esb-toolkit/apply-content-based-routing-using-business-rules-policy-for-known-message-type.md)  
  
- [如何：使用商務規則原則根據訊息內容來動態路由訊息](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
## <a name="routing-slip"></a>傳閱名單  
 傳閱名單模式描述在其中一則訊息必須路由傳送透過一系列的預先定義的順序排列，這可能不知道在設計階段中元件的案例。 如需此模式的詳細說明，請參閱[傳閱](http://go.microsoft.com/fwlink/?LinkId=186840)([http://go.microsoft.com/fwlink/?LinkId=186840](http://go.microsoft.com/fwlink/?LinkId=186840)) 上的企業整合模式的站台。  
  
 此模式的實作由提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]; 它的實作取決於用戶端應用程式提交訊息，以進行以路線為基礎的處理類型：  
  
- **服務 proxy**。 有了這類應用程式中，設定[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]匝道與路線選取器管線元件，並將關聯的路線的解析程式，選取適當[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線。 路線的屬性可能會設定為靜態屬性，使用行程解析程式，或它們可以設定為使用 BizTalk 規則引擎和 BRI 的解析程式的動態屬性。  
  
- **進階用戶端**。 有了這類應用程式中，設定[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]匝道路線選取器管線元件與路線靜態解析程式。 用戶端應用程式會傳送具有路線參考標頭，其中包含路線的名稱、 版本和追蹤識別項的訊息。  
  
- **自適性用戶端**。 使用這類應用程式中，用戶端應用程式會叫用解析程式服務，可接著藉由傳遞做為要求訊息的用戶端狀態中識別 路線的參考。 如果已解決的路線，用戶端應用程式將訊息提交路線的參考相同的方式，如先前的進階用戶端案例中所示。  
  
  如需有關如何實作此模式的詳細資訊，請參閱下列資源：  
  
- [如何：使用商務規則原則選取路線](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
- [如何：轉換訊息，並使用路線傳閱名單將產生的訊息路由至檔案位置](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
  > [!NOTE]
  >  除了上述的案例中，您可以開發自訂的路線解析程式和路線的路由服務。 您可以考慮在路線設計工具中建立用於自訂路線服務的設計工具擴充項。  
  
## <a name="scatter-gather"></a>分散-集中  
 分散-集中模式可讓訊息傳送給多位收件者，以及彙總其回應中;這會導致單一訊息。 如需此模式的詳細說明，請參閱[分散-集中](http://go.microsoft.com/fwlink/?LinkId=186841)([http://go.microsoft.com/fwlink/?LinkId=186841](http://go.microsoft.com/fwlink/?LinkId=186841)) 上的企業整合模式的站台。  
  
 如需實作此模式的範例，請參閱 <<c0> [ 安裝和執行分散-集中範例](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md)範例。  
  
## <a name="recipient-list"></a>收件者清單  
 收件者清單模式會處理一則訊息會路由傳送的實例解決方案給一或多個收件者。 收件者清單可以是以靜態方式定義 （亦即它有固定的收件者清單） 或動態。 如需此模式的詳細說明，請參閱[收件者清單](http://go.microsoft.com/fwlink/?LinkId=186842)([http://go.microsoft.com/fwlink/?LinkId=186842](http://go.microsoft.com/fwlink/?LinkId=186842)) 上的企業整合模式的站台。  
  
 實作此模式在路線設計工具是組成[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線的路由服務和多個的解析程式。 路線的路由服務負責複製一則訊息，然後使用 BizTalk 訊息內容屬性明確地將訊息路由。  
  
 您可以選擇路線的路由服務所提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，如下所示：  
  
- 定義路線的路由服務使用訊息的擴充項，以使用路線設計工具的 BizTalk 管線中執行。  
  
- 定義訊息的擴充項，以使用路線設計工具，它會執行使用 BizTalk 傳送埠路由協調流程執行與路線的路由服務。  
  
  路線的路由服務相關聯的解析程式決定訊息根據訊息內容的收件者。 您可以選擇解析程式所提供一組[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]來實作此案例。 如需有關如何實作此模式的詳細資訊，請參閱下列資源：  
  
- [如何：使用路線傳閱名單將單一訊息路由至多個收件者](../esb-toolkit/route-a-single-message-to-multiple-recipients-using-an-itinerary-routing-slip.md)  
  
## <a name="splitter"></a>分隔器  
 分隔器模式解決問題，當單一訊息需要分割成多個訊息。 如需此模式的詳細說明，請參閱[分隔](http://go.microsoft.com/fwlink/?LinkId=186843)([http://go.microsoft.com/fwlink/?LinkId=186843](http://go.microsoft.com/fwlink/?LinkId=186843)) 上的企業整合模式的站台。 如需有關如何實作此模式的詳細資訊，請參閱下列資源：  
  
-   [如何：分割交換，並使用不同路線將產生的訊息路由至多個檔案位置](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)