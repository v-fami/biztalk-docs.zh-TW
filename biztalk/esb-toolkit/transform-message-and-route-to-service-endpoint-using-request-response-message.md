---
title: "如何： 轉換訊息及使用要求-回應訊息交換模式的服務端點的路由 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1e656fb-6c5f-4b2b-a1b6-4c812b78ee22
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dfc7c7d572f3370e87df2f03d392a993116b74d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-transform-a-message-and-route-to-a-service-endpoint-using-a-request-response-message-exchange-pattern"></a>如何： 轉換訊息及使用要求-回應訊息交換模式的服務端點的路由
## <a name="goal"></a>目標  
 本節示範如何使用 ESB 設計工具的特定領域語言 (DSL) 來建立適用於雙向上手要求-回應路線。 您將建立接收訊息、 將訊息轉換、 提交訊息至服務，並返回原始訊息的傳送者的服務回應訊息的路由受控滑動。  
  
 在此 「 如何 」 主題，您將完成下列步驟：  
  
-   建立轉換路線實作的服務，Microsoft BizTalk Server 對應路線的路由受控滑動。  
  
-   設定轉換後的訊息路由至服務端點路線。  
  
-   設定服務回應訊息回到原始的傳送合作對象路線。  
  
-   測試使用路線測試用戶端範例應用程式的路線。  
  
## <a name="prerequisites"></a>必要條件  
 在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。  
  
## <a name="steps"></a>步驟  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a>若要建立 ESB 路線 DSL 模型  
  
1.  在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，開啟 C:\HowTos\Patterns\Patterns.sln。  
  
2.  在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。  
  
3.  在**加入新項目**對話方塊中，於**名稱**方塊中，輸入**RequestResponse**，然後按一下 **新增**。  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>若要設定的路線屬性  
  
1.  在 Visual Studio 中，按一下設計介面的**RequestResponse.itinerary**。 在**RequestResponse**屬性 視窗中，設定下列屬性：  
  
    1.  在**為要求回應**下拉式清單中，按一下  **True**。  
  
    2.  在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。  
  
    3.  在**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。  
  
    4.  在**選取 XML 檔案**對話方塊中，於**檔案名稱**方塊中，輸入**C:\HowTos\Itineraries\RequestResponse**，然後按一下 **儲存**。  
  
        > [!NOTE]
        >  這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。 藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。 您將完成此程序，稍後在本使用說明主題。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義路線結構  
  
1.  從 [工具箱] 拖曳**上手**至設計介面的模型項目。 在**OnRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **上手 ESB Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。  
  
    4.  在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary.Response**。  
  
2.  從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**上手**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**MapNAOrderToCNOrder**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。  
  
        > [!NOTE]
        >  這個屬性會定義程序將需要 (messaging) 在管線中的位置。 或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。  
  
    3.  在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。  
  
    4.  在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Transform**。  
  
3.  以滑鼠右鍵按一下**解析程式**集合**MapNAOrderToCNOrder**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**StaticallySpecifyTheMap**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**轉換類型**下拉式清單中，按一下  **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**。  
  
4.  在工具箱中，按一下 **連接器**。 拖曳連接**ReceiveNAOrder**模型項目的**MapNAOrderToCNOrder**模型項目。  
  
5.  從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**MapNAOrderToCNOrder**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**RouteToCNService**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。  
  
        > [!NOTE]
        >  這個屬性會定義程序將需要 (messaging) 在管線中的位置。 或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。  
  
    3.  在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。  
  
    4.  在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。  
  
6.  以滑鼠右鍵按一下**解析程式**集合**RouteToCNService**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**StaticallySpecifyTheService**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**傳輸名稱**下拉式清單中，按一下  **Wcf-basichttp**。  
  
    4.  按一下**傳輸位置**屬性，，然後輸入**http://localhost/ESB.CanadianServices/SubmitPOService.asmx**。  
  
    5.  按一下**目標命名空間**屬性，，然後輸入**http://globalbank.esb.dynamicresolution.com/canadianservices**。  
  
    6.  按一下**動作**屬性，，然後輸入**submitOrder**。  
  
7.  在工具箱中，按一下 **連接器**。 拖曳連接**MapNAOrderToCNOrder**模型項目的**RouteToCNService**模型項目。  
  
8.  從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**RouteToCNService**模型項目。 在**OffRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**InvokeCNService**。  
  
    2.  在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。  
  
    4.  在**傳送埠**下拉式清單中，按一下  **DynamicResolutionSolicitResp**。  
  
9. 從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**RouteToCNService**模型項目和**InvokeCNService**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendPortFilter**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。  
  
    3.  在**匝道**下拉式清單中，展開**InvokeCNService**，然後按一下 **傳送處理常式**。  
  
10. 在工具箱中，按一下 **連接器**。 拖曳連接**RouteToCNService**模型項目的**SendPortFilter**模型項目。  
  
11. 在工具箱中，按一下 **連接器**。 拖曳連接**SendPortFilter**模型項目的**InvokeCNService**模型項目。  
  
12. 以滑鼠右鍵按一下設計介面，然後按一下**驗證**。  
  
    > [!NOTE]
    >  路線驗證;您不需要連線匝道回到上遞增，以便將回應訊息傳送回提出要求的合作對象。 藉由使用雙向上手，最後的訊息會自動傳回到發出要求的合作對象。  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>若要匯出的行程測試用戶端使用的模型  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**RequestResponse**路線，然後再按一下**匯出模型**。  
  
    > [!NOTE]
    >  在 Visual Studio 中，開啟路線的 XML 版本。  
  
2.  儲存專案的所有成品。  
  
3.  在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries。 請注意您路線 XML (RequestResponse.xml) 建立。  
  
#### <a name="to-test-the-itinerary"></a>若要測試路線  
  
1.  開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。  
  
2.  在路線測試用戶端中，清除**使用 WCF 服務**核取方塊。  
  
3.  在**Web 服務選項**區段中，選取**兩個方式服務**核取方塊，然後**負載路線**。  
  
4.  在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。 選取**RequestResponse.xml**，然後按一下 **開啟**載入路線。  
  
5.  按一下**確定**清除**路線成功載入**訊息。  
  
6.  在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。  
  
7.  在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。 選取**NAOrderDoc.xml**，然後按一下 **開啟**載入測試訊息。  
  
8.  按一下**送出要求** 按鈕。 測試完成時，按一下**確定**解除顯示的確認。  
  
9. 在**結果**方塊中，注意到訊息的根節點是**submitOrderResponse**和預設命名空間是...**canadianservices**。  
  
    > [!NOTE]
    >  如果回應訊息需要其他轉換之前，回應會傳送到提出要求的合作對象，您必須使用包含 ESB 轉寄站元件的管線。 如需這項功能的範例，請參閱[安裝及執行多個 Web 服務範例](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [如何： 轉換訊息，並將產生的訊息路由至使用路線的路由名單的檔案位置](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [訊息的路由模式](../esb-toolkit/message-routing-patterns.md)  
  
-   [安裝及執行多個 Web 服務範例](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)