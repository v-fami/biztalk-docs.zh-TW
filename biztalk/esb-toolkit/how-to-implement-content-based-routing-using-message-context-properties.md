---
title: "如何： 實作內容架構路由使用訊息內容屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 952af792-5762-4b04-9087-980bb3323568
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be099923fea9d5dbb22559203b297fadf5dd1fdc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-implement-content-based-routing-using-message-context-properties"></a>如何： 實作內容架構路由使用訊息內容屬性
## <a name="goal"></a>目標  
 本節示範如何使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線設計工具建立行程選取訊息收件者根據訊息內容屬性，然後將訊息路由傳送至該收件者，使用行程 Broker 訊息服務。  
  
 在本主題中，您將完成下列步驟：  
  
-   建立行程路線的 broker 與使用靜態的解析程式的兩個路由服務。  
  
-   測試使用路線測試用戶端範例應用程式的路線。  
  
> [!NOTE]
>  在目前的實作不提供任何協調流程為基礎的 broker 服務。  
  
## <a name="prerequisites"></a>必要條件  
 在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。  
  
## <a name="steps"></a>步驟  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a>若要建立 ESB 行程 DSL 模型  
  
1.  在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。  
  
2.  在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**，指向 **新增**，然後按一下 **新的行程**。  
  
3.  在**加入新項目**對話方塊中，按一下  **ItineraryDsl**在範本窗格中。  
  
4.  在**名稱**方塊中，輸入**ChoiceRouter**，然後按一下 **新增**。  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>若要設定的路線屬性  
  
1.  在 Visual Studio 中，按一下設計介面的**ChoiceRouter**路線。 在**ChoiceRouter**屬性 視窗中，設定下列屬性：  
  
    1.  在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。  
  
    2.  在**Extender 設定**區段中，按一下旁邊的省略符號按鈕 （...）**路線 XML 檔案**屬性。  
  
    3.  在**匯出模式**屬性下拉式清單中，按一下  **Strict**。  
  
    4.  在**選取 XML 檔案** 對話方塊中，輸入**C:\HowTos\Itineraries\ChoiceRouter**中**檔案名稱**方塊，然後再按一下**儲存**。  
  
    > [!NOTE]
    >  這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。 藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，您可以測試使用 ESB 測試用戶端應用程式的路線。 您將完成此程序，稍後在本使用說明主題。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義路線結構  
  
1.  從 [工具箱] 拖曳**上手**至設計介面的模型項目。 在 [OnRamp1 屬性] 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **上手 Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。  
  
    4.  在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。  
  
2.  從 [工具箱] 拖曳**路線 Broker 服務**模型設計工具介面中，項目，然後將它放到右側**上手**模型項目。 在**ItineraryBrokerService1**，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**RouteBrokerService**。  
  
    2.  在**Extender**下拉式清單中，按一下 **傳訊 Broker Extender**。  
  
    3.  在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。  
  
    4.  在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Itinerary.Services.Broker.MessagingBroker**。  
  
3.  以滑鼠右鍵按一下**篩選**集合，然後再按一下**加入新的篩選器**。 在**Filter1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ASMXFilter**。  
  
    2.  按一下**篩選**實作下拉式清單中，，然後按一下**XPath 篩選條件**。  
  
    3.  按一下**運算式**屬性，，然後輸入**計數 (ContextProperties/屬性 [@name= 'InboundTransportLocation'] [包含 (。，'ProcessItinerary.asmx')]) > 0**。  
  
4.  以滑鼠右鍵按一下**篩選**集合，然後再按一下**加入新的篩選器**。 在**Filter1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**WCFFilter**。  
  
    2.  按一下**篩選器實作**下拉式清單，然後按一下**XPath 篩選條件**。  
  
    3.  按一下**運算式**屬性，，然後輸入**計數 (ContextProperties/屬性 [@name= 'InboundTransportLocation'] [包含 (。，' ESB。ItineraryServices.WCF')]) > 0**。  
  
5.  以滑鼠右鍵按一下**解析程式**集合**RouteBrokerService**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ResolverBrokerRoute**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下  **MessageContext 解析程式擴充功能**。  
  
6.  在工具箱中，按一下 **連接器**。 拖曳連接**ReceiveNAOrder**模型項目的**RouteBrokerService**模型項目。  
  
7.  從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其下放置**RouteBrokerService**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**RouteToFileFromASMX**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。  
  
        > [!NOTE]
        >  這個屬性會定義程序將需要 (messaging) 在管線中的位置。 或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。  
  
    3.  在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。  
  
    4.  在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。  
  
8.  以滑鼠右鍵按一下**解析程式**集合**RouteToFileFromASMX**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ResolverFromAsmx**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**傳輸名稱**下拉式清單中，按一下 **檔案**。  
  
    4.  按一下**傳輸位置**屬性，，然後輸入**c:\howtos\out\asmx%MessageId%.xml**。  
  
9. 從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**RouteToFileFromASMX**模型項目。 在**OffRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendASMXOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。  
  
    4.  在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。  
  
10. 從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**RouteToFileFromASMX**模型項目和**SendASMXOrder**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendPortFilterASMX**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。  
  
    3.  在**匝道**下拉式清單中，展開**SendASMXOrder**，然後按一下 **傳送處理常式**。  
  
11. 在工具箱中，按一下 **連接器**。 拖曳連接**RouteToFileFromASMX**模型項目的**SendPortFilterASMX**模型項目。  
  
12. 在工具箱中，按一下 **連接器**。 拖曳連接**SendPortFilterASMX**模型項目的**SendASMXOrder**模型項目。  
  
13. 從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**RouteBrokerService**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**RouteToFileFromWCF**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。  
  
        > [!NOTE]
        >  這個屬性會定義程序將需要 (messaging) 在管線中的位置。 或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。  
  
    3.  在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。  
  
    4.  在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。  
  
14. 以滑鼠右鍵按一下**解析程式**集合**RouteToFileFromWCF**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ResolverFromWCF**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**傳輸名稱**下拉式清單中，按一下 **檔案**。  
  
    4.  按一下**傳輸位置**屬性，，然後輸入**c:\howtos\out\wcf%MessageId%.xml**。  
  
15. 從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**RouteToFileFromWCF**模型項目。 在**OffRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendWCFOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。  
  
    4.  在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。  
  
16. 從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**RouteToFileFromWCF**模型項目和**SendWCFOrder**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendPortFilterWCF**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。  
  
    3.  在**匝道**下拉式清單中，展開**SendWCFOrder**，然後按一下 **傳送處理常式**。  
  
17. 在工具箱中，按一下 **連接器**。 拖曳連接**RouteToFileFromWCF**模型項目的**SendPortFilterWCF**模型項目。  
  
18. 在工具箱中，按一下 **連接器**。 拖曳連接**SendPortFilterWCF**模型項目的**SendWCFOrder**模型項目。  
  
19. 從 [工具箱] 拖曳**路線 Outport**到右框線的模型項目**RouteBrokerService**。 在**ItineraryBrokerOutPort1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**WCF 連接埠**。  
  
    2.  在**篩選**下拉式清單中，按一下  **WCFFilter**。  
  
    3.  在**解析程式**下拉式清單中，按一下  **ResolverBrokerRoute**。  
  
20. 從 [工具箱] 拖曳**路線 Outport**模型項目的下框線的**RouteBrokerService**。 在**ItineraryBrokerOutPort1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ASMX 連接埠**。  
  
    2.  在**篩選**下拉式清單中，按一下  **ASMXFilter**。  
  
    3.  在**解析程式**下拉式清單中，按一下  **ResolverBrokerRoute**。  
  
21. 在工具箱中，按一下 **連接器**。 拖曳連接**WCF 連接埠**模型項目的**RouteToFileFromWCF**模型項目。  
  
22. 在工具箱中，按一下 **連接器**。 拖曳連接**ASMX 連接埠**模型項目的**RouteToFileFromASMX**模型項目。  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>若要匯出的行程測試用戶端使用的模型  
  
> [!NOTE]
>  您必須匯出路線兩次： 一次在 XML 中，另一個時間來測試路由的 broker 透過資料庫。  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**ChoiceRouter**路線，然後再按一下**匯出模型**。  
  
    > [!NOTE]
    >  在 Visual Studio 中，開啟路線的 XML 版本。  
  
2.  在 Windows 檔案總管，瀏覽 C:\HowTos\Itineraries，並注意您路線 XML (ChoiceRouter.xml) 建立。  
  
3.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**ChoiceRouter**路線，然後再按一下**匯出模型**。  
  
4.  在 [屬性] 視窗中，按一下**資料庫路線匯出工具**中**模型匯出工具**下拉式清單。  
  
5.  在 [屬性] 視窗中，設定**路線資料庫**屬性指向路線資料庫的連接字串。  
  
6.  在**路線狀態**屬性下拉式清單中，選取**部署**。  
  
7.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**ChoiceRouter**路線，然後再按一下**匯出模型**。  
  
#### <a name="to-test-the-itinerary"></a>若要測試路線  
  
1.  開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。  
  
2.  在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。  
  
3.  在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。 選取**ChoiceRouter.xml**，然後按一下 **開啟**載入路線。  
  
4.  按一下**確定**關閉 「 路線載入成功 」 訊息。  
  
5.  在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。  
  
6.  在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\Patterns\HowTos。 選取 NAOrderDoc.xml，，然後按一下**開啟**載入測試訊息。  
  
7.  按一下**送出要求** 按鈕。 測試完成時，按一下**確定**關閉出現的確認訊息。  
  
8.  在 Windows 檔案總管，瀏覽至 C:\HowTos\Out。請確認 ASMX%MessageID%.xml 訊息已寫入至這個目錄。  
  
9. 按一下 路線測試用戶端**使用 WCF 服務**核取方塊。 在**路線名稱**方塊中，輸入**ChoiceRouter**，然後按一下 [**送出要求**] 按鈕。 測試完成時，按一下**確定**關閉確認訊息。  
  
10. 在 Windows 檔案總管，瀏覽至 C:\HowTos\Out。請確認 WCF%MessageID%.xml 訊息已寫入至這個目錄。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [如何：使用商務規則原則選取路線](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [如何：使用商務規則原則根據訊息內容來動態路由訊息](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [訊息路由模式](../esb-toolkit/message-routing-patterns.md)