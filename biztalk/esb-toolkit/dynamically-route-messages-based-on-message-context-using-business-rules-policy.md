---
title: "如何： 動態地路由傳送訊息根據訊息內容使用商務規則原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d3b68de-6b24-46fe-ae0d-91afb630bc19
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717e0180ba92d49751342e00a4d0367832084135
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-dynamically-route-a-message-based-on-message-context-using-a-business-rules-policy"></a>如何： 動態地路由傳送訊息的內容使用商務規則原則為基礎的訊息
## <a name="goal"></a>目標  
 本節示範如何建立會決定訊息的端點，根據訊息內容屬性，使用行程[!INCLUDE[prague](../includes/prague-md.md)]商務規則引擎 (BRE) 原則，然後再路由訊息使用[!INCLUDE[prague](../includes/prague-md.md)]FILE 配接器。  
  
 在此 「 如何 」 主題，您將完成下列步驟：  
  
-   建立商務規則原則評估訊息類型。  
  
-   建立動態路由使用商務規則原則路線路由受控滑動。  
  
-   測試使用路線測試用戶端範例應用程式的路線。  
  
## <a name="prerequisites"></a>必要條件  
 在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。  
  
## <a name="steps"></a>步驟  
 **若要建立使用訊息內容屬性將訊息路由傳送的 BRE 原則**  
  
1.  按一下**啟動**在工作列上，指向**所有程式**，指向   **[!INCLUDE[prague](../includes/prague-md.md)]** ，然後按一下**商務規則編輯器 」**。  
  
2.  在 [原則總管] 中，以滑鼠右鍵按一下**原則**，然後按一下**新增原則**。 命名原則**RouteBasedOnMessageType**。  
  
 **若要加入北美地區的訂單的路由規則**  
  
1.  在**RouteBasedOnMessageType**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**新增規則**。 命名規則**SetNAOrderEndpoint**。  
  
2.  在 規則 視窗中，以滑鼠右鍵按一下**條件**，指向 **述詞**，然後按一下**等於**。  
  
3.  在 [事實總管] 中，展開**ESB。ContextInfo**詞彙中，展開**1.0 版**，然後將拖曳**內容的訊息類型**事實**引數 1**節點下的**條件**。  
  
    > [!NOTE]
    >  [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含數個可以用來建立規則的詞彙。 這些應該取代或夾帶您自己的詞彙。 例如， **DynamicRunTimeMaptypes**原則都有定義中的對應**GlobalBank**範例。  
  
4.  按一下**引數 2**  節點，然後輸入**http://globalbank.esb.dynamicresolution.com/northamericanservices/#OrderDoc**  
  
5.  在 [事實總管] 中，展開**ESB。EndPointInfo**詞彙中，展開**1.0 版**，然後將拖曳**設定結束點輸出傳輸位置**定義**動作**。  
  
6.  按一下**\<空字串 >**，然後輸入**C:\HowTos\Out\NorthAmerica%MessageID%.xml**  
  
7.  從 [事實總管] 中，拖曳**設定結束點輸出傳輸類型**定義**動作**。  
  
8.  在 [事實總管] 中，展開**ESB。TansportTypes**詞彙中，展開**1.0 版**，然後將拖曳**配接器提供者**定義**\<空字串 >**。  
  
9. 在 [動作] 窗格中，依序展開**配接器提供者**下拉式清單，然後按一下**檔案**。  
  
 **若要發行和部署原則**  
  
1.  在 [原則總管] 中，在**RouteBasedOnMessageType**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**發行**。  
  
2.  在 [原則總管] 中，在**RouteBasedOnMessageType**原則，以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下**部署**。  
  
 **若要建立 ESB 路線網域特定領域語言 (DSL) 模型**  
  
1.  在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，開啟 C:\HowTos\Patterns\Patterns.sln。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新的行程**。  
  
3.  在**名稱**方塊中，輸入**MessageType**，然後按一下**新增**。  
  
 **若要設定的路線屬性**  
  
1.  在 Visual Studio 中，按一下設計介面的**MessageType.itinerary**。 在**MessageType**屬性 視窗中，設定下列屬性：  
  
    1.  在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。  
  
    2.  在**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。  
  
    3.  在**選取 XML 檔案**對話方塊中，於**檔案名稱**方塊中，輸入**C:\HowTos\Itineraries\MessageType**，然後按一下**儲存**。  
  
        > [!NOTE]
        >  這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。 將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。 您將完成此程序，稍後在本使用說明主題。  
  
 **若要定義路線結構**  
  
1.  從 [工具箱] 拖曳**上手**至設計介面的模型項目。 在**OnRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ReceiveOrders**。  
  
    2.  在**Extender**下拉式清單中，按一下 **上手 ESB Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。  
  
    4.  在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。  
  
2.  從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**上手**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**BreRoute**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。  
  
        > [!NOTE]
        >  這個屬性會定義程序將需要 (messaging) 在管線中的位置。 或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。  
  
    3.  在**容器**下拉式清單中，展開**ReceiveOrders**，然後按一下**接收處理常式**。  
  
    4.  在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。  
  
3.  以滑鼠右鍵按一下**解析程式**集合**BreRoute**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ByMessageType**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下  **Bre 解析程式擴充功能**。  
  
    3.  在**原則**下拉式清單中，按一下  **RouteBasedOnMessageType v 1.0**。  
  
4.  在工具箱中，按一下 **連接器**。 拖曳連接**ReceiveOrders**模型項目的**BreRoute**模型項目。  
  
5.  從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**BreRoute**模型項目。 在**OffRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendBasedOnType**。  
  
    2.  在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。  
  
    4.  在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。  
  
6.  從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**BreRoute**模型項目和**SendBasedOnType**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendPortFilter**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。  
  
    3.  在**匝道**下拉式清單中，展開**SendBasedOnType**，然後按一下**傳送處理常式**。  
  
7.  在工具箱中，按一下 **連接器**。 拖曳連接**BreRoute**模型項目的**SendPortFilter**模型項目。  
  
8.  在工具箱中，按一下 **連接器**。 拖曳連接**SendPortFilter**模型項目的**SendBasedOnType**模型項目。  
  
 **若要匯出的行程測試用戶端使用的模型**  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**MessageType**路線，然後再按一下**匯出模型**。  
  
    > [!NOTE]
    >  在 Visual Studio 中，開啟路線的 XML 版本。  
  
2.  儲存專案的所有成品。  
  
3.  在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries 並注意您路線 XML (MessageType.xml) 建立。  
  
 **若要測試路線**  
  
1.  開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。  
  
2.  在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。  
  
3.  在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。 選取**MessageType.xml**，然後按一下**開啟**載入路線。  
  
4.  按一下**確定**清除**路線成功載入**訊息。  
  
5.  在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。  
  
6.  在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。 選取**NAOrderDoc.xml**，然後按一下**開啟**載入測試訊息。  
  
7.  按一下**送出要求** 按鈕。 測試完成時，按一下**確定**解除顯示的確認。  
  
8.  在 Windows 檔案總管，瀏覽至 C:\HowTos\Out\\。 請確認 NorthAmerica%MessageID%.xml 訊息已寫入至目錄。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [如何： 選取 使用商務規則原則路線](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [如何： 轉換訊息，並將產生的訊息路由至使用路線的路由名單的檔案位置](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [如何： 實作內容架構路由使用商務規則原則已知的訊息類型](../esb-toolkit/apply-content-based-routing-using-business-rules-policy-for-known-message-type.md)  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [訊息的路由模式](../esb-toolkit/message-routing-patterns.md)  
  
-   [使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)