---
title: 如何： 將單一訊息路由至多個收件者使用路線路由名單 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c30493-4fe1-4fd5-8bc7-af091535b091
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c493b33081e540a4e18d6d20e4813cdddad894a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010471"
---
# <a name="how-to-route-a-single-message-to-multiple-recipients-using-an-itinerary-routing-slip"></a>如何： 將單一訊息路由至多個收件者使用路線路由名單
## <a name="goal"></a>目標  
 本節示範如何使用三個的相異收件者使用靜態的解析程式和 BizTalk Server 檔案配接器來建立將訊息傳送路線設計工具的特定領域語言 (DSL)。  
  
 在此 「 如何 」 主題，您將完成下列步驟：  
  
-   建立具有三個靜態的解析程式將訊息路由至多個收件者的路線。  
  
-   測試使用路線測試用戶端範例應用程式的路線。  
  
## <a name="prerequisites"></a>必要條件  
 在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。  
  
## <a name="steps"></a>步驟  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a>若要建立 ESB 路線 DSL 模型  
  
1.  在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。  
  
2.  在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**，指向 **新增**，然後按一下 **新的行程**。  
  
3.  在**加入新項目**對話方塊中，按一下  **ItineraryDsl**在範本窗格中。  
  
4.  在**名稱**方塊中，輸入**RecipientList**，然後按一下 **新增**。  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>若要設定的路線屬性  
  
1.  在 Visual Studio 中，按一下 RecipientList.itinerary 的設計介面。 在 [RecipientList 屬性] 視窗中，設定下列屬性：  
  
    1.  在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。  
  
    2.  在**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。  
  
    3.  在**選取 XML 檔案**對話方塊中，於**檔案名稱**方塊中，輸入**C:\HowTos\Itineraries\RecipientList**，然後按一下 **儲存**。  
  
        > [!NOTE]
        >  這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。 藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。 您將完成此程序，稍後在本使用說明主題。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義路線結構  
  
1.  從 [工具箱] 拖曳**上手**至設計介面的模型項目。 在**OnRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **上手 Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。  
  
    4.  在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。  
  
2.  從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**上手**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**RouteToThreeRecipients**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。  
  
        > [!NOTE]
        >  這個屬性會定義程序將需要 (messaging) 在管線中的位置。 或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。  
  
    3.  在**容器**下拉式清單中，展開**ReceiveNaOrderDoc**，然後按一下 **接收處理常式**。  
  
    4.  在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。  
  
3.  以滑鼠右鍵按一下**解析程式**集合**RouteToThreeRecipients**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**FirstResolver**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**傳輸名稱**下拉式清單中，按一下 **檔案**。  
  
    4.  按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\First%MessageID%.xml**。  
  
        > [!NOTE]
        >  您已加入此路線服務的三個解決器的第一個。 您現在要加入更多的兩個解析程式將訊息路由至其他收件者。  
  
4.  以滑鼠右鍵按一下**解析程式**集合**RouteToThreeRecipients**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SecondResolver**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**傳輸名稱**下拉式清單中，按一下 **檔案**。  
  
    4.  按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\Second%MessageID%.xml**。  
  
5.  以滑鼠右鍵按一下**解析程式**集合**RouteToThreeRecipients**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ThirdResolver**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**傳輸名稱**下拉式清單中，按一下 **檔案**。  
  
    4.  按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\Third%MessageID%.xml**。  
  
6.  在工具箱中，按一下 **連接器**。 拖曳連接**ReceiveNAOrder**模型項目的**RouteToThreeRecipients**模型項目。  
  
7.  從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**RouteToThreeRecipients**模型項目。 在**OffRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendThreeMessages**。  
  
    2.  在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。  
  
    4.  在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。  
  
8.  從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**RouteToThreeRecipients**模型項目和**SendThreeMessages**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendPortFilter**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。  
  
    3.  在**匝道**下拉式清單中，展開**SendThreeMessages**，然後按一下 **傳送處理常式**。  
  
9. 在工具箱中，按一下 **連接器**。 拖曳連接**RouteToThreeRecipients**模型項目的**SendPortFilter**模型項目。  
  
10. 在工具箱中，按一下 **連接器**。 拖曳連接**SendPortFilter**模型項目的**SendThreeMessages**模型項目。  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>若要匯出的行程測試用戶端使用的模型  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**RecipientList**路線，然後再按一下**匯出模型**。  
  
    > [!NOTE]
    >  在 Visual Studio 中，開啟路線的 XML 版本。  
  
2.  儲存專案的所有成品。  
  
3.  在 Windows 檔案總管，瀏覽 C:\HowTos\Itineraries，並注意您路線 XML (RecipientList.xml) 建立。  
  
#### <a name="to-test-the-itinerary"></a>若要測試路線  
  
1.  開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。  
  
2.  在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。  
  
3.  在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。 選取**RecipientList.xml**，然後按一下 **開啟**載入路線。  
  
4.  按一下**確定**清除 「 路線成功載入： 訊息。  
  
5.  在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。  
  
6.  在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\Patterns。 選取 NAOrderDoc.xml，，然後按一下**開啟**載入測試訊息。  
  
7.  按一下**送出要求** 按鈕。 測試完成時，按一下**確定**解除顯示的確認。  
  
8.  在 Windows 檔案總管，瀏覽至 C:\HowTos\Out\\。 請確認下列訊息的已寫入到目錄：  
  
    -   First%MessageID%.xml  
  
    -   Second%MessageID%.xml  
  
    -   Third%MessageID%.xml  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [訊息路由模式](../esb-toolkit/message-routing-patterns.md)  
  
-   [使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)