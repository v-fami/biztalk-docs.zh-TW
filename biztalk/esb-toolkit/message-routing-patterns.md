---
title: 訊息路由模式 |Microsoft 文件
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
ms.openlocfilehash: a332a8ab942363ff5224f34149b345c9c7d40698
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22296886"
---
# <a name="message-routing-patterns"></a>訊息的路由模式
訊息的路由模式定義訊息路由傳送至其目標端點經過證實的指導方針。 路由可以是靜態設定，因為它可以動態設定根據一些準則和使用多種方法。  
  
## <a name="message-router"></a>訊息路由器  
 訊息路由器模式會決定一組條件所根據訊息的收件者。 如需此模式的詳細說明，請參閱[訊息路由器](http://go.microsoft.com/fwlink/?LinkId=186844)([http://go.microsoft.com/fwlink/?LinkId=186844](http://go.microsoft.com/fwlink/?LinkId=186844)) 上的企業整合模式站台。  
  
 此模式在路線設計工具中的實作是組合[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線的路由服務與單一內容為基礎的解析程式。 路線路由服務負責將訊息路由的屬性，Microsoft BizTalk 訊息內容中升級或明確的訊息路由。  
  
 您可以選擇路線路由服務所提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，如下所示：  
  
-   定義訊息的擴充項 BizTalk 管線使用路線設計工具中執行的路線路由服務。  
  
-   定義以協調流程中使用執行路由使用 BizTalk 傳送埠的路線設計工具來執行的協調流程擴充的路線路由服務。  
  
 路線路由服務相關聯的解析程式決定訊息，並根據訊息內容的收件者。 您可以選擇 「 解決者 」 從該支援內容為基礎的路由提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，或您可以實作自己的解析程式。  
  
 如需實作此模式中的範例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，請參閱下列資源：  
  
-   [如何： 解決使用繫結機碼搜尋 UDDI 服務端點](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  
  
-   [如何： 解決使用 UDDI 類別目錄搜尋之服務端點](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  
  
## <a name="content-based-router"></a>以內容為基礎的路由  
 內容型路由器模式決定訊息根據訊息內容的收件者。 如需此模式的詳細說明，請參閱[內容型路由器](http://go.microsoft.com/fwlink/?LinkId=186839)([http://go.microsoft.com/fwlink/?LinkId=186839](http://go.microsoft.com/fwlink/?LinkId=186839)) 企業整合模式站台上。  
  
 此模式在路線設計工具中的實作是組合[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線的路由服務與單一內容為基礎的解析程式。 路線路由服務負責將 BizTalk 訊息內容中的訊息路由屬性升級，或明確地將訊息路由傳送。  
  
 您可以選擇路線路由服務所提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，如下所示：  
  
-   定義要在 BizTalk 管線中使用路線設計工具中執行的傳訊 extender 路線路由服務。  
  
-   定義要執行為協調流程中使用路線設計工具中，以執行路由使用 BizTalk 傳送埠協調流程 extender 路線路由服務。  
  
-   定義路線 broker 服務的 broker 訊息擴充項 BizTalk 管線使用路線設計工具中執行。  
  
 路線路由服務相關聯的解析程式決定訊息根據訊息內容的收件者。 您可以選擇下列解析程式從該支援內容為基礎的路由提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:  
  
-   **XPATH 解析程式**。 藉由使用這個解析程式，您可以路由使用 XPATH 查詢的訊息內容。  
  
-   **BRE 解析程式**。 藉由使用這個解析程式，您可以從使用 BizTalk 規則引擎的訊息內容擷取路由資訊。  
  
-   **訊息內容解析程式**。 藉由使用這個解析程式，您可以擷取訊息的內容從 BizTalk 訊息內容會與相關聯時[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線 broker 服務。  
  
    > [!NOTE]
    >  除了上述的實作情況下，您可以開發自訂內容為基礎的解析程式和路線的路由解決方案以傳訊為基礎或協調流程為基礎的服務。 在此情況下，您可能需要實作的擴充項[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和行程路線設計工具與交互操作的服務。  
  
 如需範例的這個實作中，請參閱下列資源：  
  
-   [安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)  
  
-   [如何： 實作內容架構路由使用商務規則原則已知的訊息類型](../esb-toolkit/apply-content-based-routing-using-business-rules-policy-for-known-message-type.md)  
  
-   [如何： 動態地路由傳送訊息的內容使用商務規則原則為基礎的訊息](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
## <a name="routing-slip"></a>路由名單  
 路由名單模式描述的案例中的訊息必須路由傳送透過一系列的預先定義的順序，可能不知道在設計階段中的元件。 如需此模式的詳細說明，請參閱[路由 Slip](http://go.microsoft.com/fwlink/?LinkId=186840) ([http://go.microsoft.com/fwlink/?LinkId=186840](http://go.microsoft.com/fwlink/?LinkId=186840)) 企業整合模式站台上。  
  
 此模式的實作由提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]; 它的實作取決於用戶端應用程式所提交訊息，以進行行程為基礎的處理類型：  
  
-   **服務 proxy**。 這種類型的應用程式中，設定[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]上手與路線選取器管線元件，並將關聯的路線的解析程式來選取適當[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線。 路線屬性可設定為靜態屬性，使用行程解析程式，或將它們設定為使用 BizTalk 規則引擎和 BRI 解析程式的動態屬性。  
  
-   **進階用戶端**。 這種類型的應用程式中，設定[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]上手路線選取器管線元件與路線靜態解析程式。 用戶端應用程式傳送訊息，其中路線參考標頭，其中包含計劃的名稱、 版本，以及追蹤識別碼。  
  
-   **自動調整的用戶端**。 這種類型的應用程式中，用戶端應用程式會叫用的解析程式服務，接著，藉由傳遞做為要求訊息的用戶端狀態識別路線的參考。 如果解析路線，用戶端應用程式會在先前的進階用戶端案例中的相同方式提交路線參考訊息。  
  
 如需實作此模式的詳細資訊，請參閱下列資源：  
  
-   [如何： 選取 使用商務規則原則路線](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [如何： 轉換訊息，並將產生的訊息路由至使用路線的路由名單的檔案位置](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
    > [!NOTE]
    >  除了上述的情況下，您可以開發自訂的路線解析程式 」 和 「 路線路由服務。 您可以考慮在路線設計工具中建立用於自訂路線服務的設計工具的擴充項。  
  
## <a name="scatter-gather"></a>分散-集中  
 分散-集中模式可讓訊息傳送給多位收件者，以及彙總其回應中。這會導致單一訊息。 如需此模式的詳細說明，請參閱[分散-集中](http://go.microsoft.com/fwlink/?LinkId=186841)([http://go.microsoft.com/fwlink/?LinkId=186841](http://go.microsoft.com/fwlink/?LinkId=186841)) 上的企業整合模式站台。  
  
 如需實作此模式的範例，請參閱[安裝及執行分散-集中範例](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md)範例。  
  
## <a name="recipient-list"></a>收件者清單  
 收件者清單模式給一或多個收件者位址的訊息會路由傳送的實例解決方案。 收件者清單可以是以靜態方式定義 （亦即它有固定的收件者清單） 或動態。 如需此模式的詳細說明，請參閱[收件者清單](http://go.microsoft.com/fwlink/?LinkId=186842)([http://go.microsoft.com/fwlink/?LinkId=186842](http://go.microsoft.com/fwlink/?LinkId=186842)) 上的企業整合模式站台。  
  
 此模式在路線設計工具中的實作是組合[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線路由服務和多個的解析程式。 路線路由服務負責複製一則訊息，然後使用 BizTalk 訊息內容屬性明確地將訊息路由。  
  
 您可以選擇路線路由服務所提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，如下所示：  
  
-   定義訊息的擴充項 BizTalk 管線使用路線設計工具中執行的路線路由服務。  
  
-   定義訊息的擴充性，以使用路線設計工具，執行路由使用 BizTalk 傳送埠協調流程來執行的路線路由服務。  
  
 路線路由服務相關聯的解析程式決定訊息根據訊息內容的收件者。 您可以選擇解析程式所提供一組[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]來實作此案例。 如需實作此模式的詳細資訊，請參閱下列資源：  
  
-   [如何： 將單一訊息路由至多個收件者使用路線路由名單](../esb-toolkit/route-a-single-message-to-multiple-recipients-using-an-itinerary-routing-slip.md)  
  
## <a name="splitter"></a>分隔器  
 分隔器模式單一訊息必須分割成多個訊息時，以解決問題。 如需此模式的詳細說明，請參閱[分隔器](http://go.microsoft.com/fwlink/?LinkId=186843)([http://go.microsoft.com/fwlink/?LinkId=186843](http://go.microsoft.com/fwlink/?LinkId=186843)) 上的企業整合模式站台。 如需實作此模式的詳細資訊，請參閱下列資源：  
  
-   [如何： 將交換分割，並將產生的訊息路由至多個使用不同的行程的檔案位置](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)