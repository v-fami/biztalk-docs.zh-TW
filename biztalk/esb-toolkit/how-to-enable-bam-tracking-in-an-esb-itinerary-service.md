---
title: "如何： 啟用 BAM 追蹤在 ESB 路線服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58859937-f8d0-4c33-9a7a-62fec8441936
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 011de667e06f4275fe75a28b6566a6bc393cf841
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-enable-bam-tracking-in-an-esb-itinerary-service"></a>如何： 啟用 BAM 追蹤 ESB 路線服務中
## <a name="goal"></a>目標  
 本節示範如何啟用商務活動監視器 (BAM) 追蹤現有的路線。  
  
 在此 「 如何 」 主題，您將完成下列步驟：  
  
-   啟用用來追蹤使用 「 商務活動監視器的路線服務的內容。  
  
-   測試路線測試用戶端範例應用程式中的 BAM 追蹤。  
  
-   驗證 BAM 結果使用 SQL 查詢。  
  
## <a name="prerequisites"></a>必要條件  
 在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。  
  
## <a name="before-you-begin"></a>開始之前  
 在執行本使用說明主題中稍後的步驟之前，請完成下列工作：  
  
-   建立 ESB 路線網域特定領域語言 (DSL) 模型。  
  
-   設定屬性的路線。  
  
-   定義結構的路線。  
  
 下列程序說明如何執行每一種。  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a>若要建立 ESB 路線 DSL 模型  
  
1.  在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。  
  
2.  在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。  
  
3.  在**加入新項目**對話方塊中，按一下  **ItineraryDsl**在範本窗格中。  
  
4.  在**名稱**方塊中，輸入**BamTracking**，然後按一下 **新增**。  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>若要設定的路線屬性  
  
1.  在 Visual Studio 中，按一下設計介面的**BamTracking.itinerary**。 在**BamTracking**屬性 視窗中，設定下列屬性：  
  
    1.  在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。  
  
    2.  在**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。  
  
    3.  在**選取 XML 檔案**對話方塊中，於**檔案名稱**方塊中，輸入**C:\HowTos\Itineraries\BamTracking** ，然後按一下 **儲存**。  
  
        > [!NOTE]
        >  這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。 藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。 您將完成此程序，稍後在本使用說明主題。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義路線結構  
  
1.  從 [工具箱] 拖曳**上手**至設計介面的模型項目。 在**OnRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **上手 ESB 服務延伸模組**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。  
  
    4.  在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。  
  
2.  從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**上手**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**MapNAOrderToCNOrder**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **傳訊路線服務延伸模組**。  
  
        > [!NOTE]
        >  這個屬性會定義程序將需要 (messaging) 在管線中的位置。 或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程路線服務延伸模組**。  
  
    3.  在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。  
  
    4.  在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Transform**。  
  
3.  以滑鼠右鍵按一下**解析程式**集合**MapNAOrderToCNOrder**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**StaticallySpecifyTheMap**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**轉換類型**下拉式清單中，按一下  **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**。  
  
    4.  在**TransportName**下拉式清單中，按一下 **檔案**。  
  
4.  在工具箱中，按一下 **連接器**。 拖曳連接**ReceiveNAOrder**模型項目的**MapNAOrderToCNOrder**模型項目。  
  
5.  從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**MapNAOrderToCNOrder**模型項目。 在**OffRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendCNOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **匝道 ESB 服務延伸模組**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。  
  
    4.  在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。  
  
6.  從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**MapNAOrderToCNOrder**模型項目和**SendCNOrder**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendPortFilter**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **匝道路線服務延伸模組**。  
  
    3.  在**匝道**下拉式清單中，展開**SendCNOrder**，然後按一下 **傳送處理常式**。  
  
7.  以滑鼠右鍵按一下**解析程式**集合**SendPortFilter**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ConfigureFolderSettings**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**傳輸名稱**下拉式清單中，按一下 **檔案**。  
  
    4.  按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\BAM%MessageID%.xml**  
  
        > [!NOTE]
        >  每個匝道會有相關聯的路線服務結合的路線服務屬性以及匝道的屬性來定義動態傳送埠的訂用帳戶。  
  
8.  在工具箱中，按一下 **連接器**。 拖曳連接**MapNAOrderToCNOrder**模型項目的**SendPortFilter**模型項目。  
  
9. 在工具箱中，按一下 **連接器**。 拖曳連接**SendPortFilter**模型項目的**SendCNOrder**模型項目。  
  
10. 儲存專案的所有成品。  
  
## <a name="steps"></a>步驟  
  
#### <a name="to-modify-the-itinerary"></a>若要修改路線  
  
1.  在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。  
  
2.  在 [方案總管] 中，按兩下**BamTracking.itinerary**。  
  
3.  按一下**MapNAOrderToCNOrder**路線服務項目。  
  
4.  在**MapNAOrderToCNOrder**屬性] 視窗中，按一下 [ **True**中**啟用追蹤**下拉式清單。  
  
5.  按一下**SendPortFilter**路線服務項目。  
  
6.  在**SendPortFilter**屬性] 視窗中，按一下 [ **True**中**啟用追蹤**下拉式清單。  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>若要匯出的行程測試用戶端使用的模型  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**BamTracking**路線，然後再按一下**匯出模型**。  
  
    > [!NOTE]
    >  在 Visual Studio 中，開啟路線的 XML 版本。  
  
2.  儲存專案的所有成品。  
  
3.  在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries 並注意您路線 XML (BamTracking.xml) 建立。  
  
#### <a name="to-test-the-itinerary"></a>若要測試路線  
  
1.  開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。  
  
2.  在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。  
  
3.  在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。 選取**BamTracking.xml**，然後按一下 **開啟**載入路線。  
  
4.  按一下**確定**清除**路線成功載入**訊息。  
  
5.  在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。  
  
6.  在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。 選取**NAOrderDoc.xml**，然後按一下 **開啟**載入測試訊息。  
  
7.  按一下**送出要求** 按鈕。 測試完成時，按一下**確定**解除顯示的確認。  
  
8.  在 Windows 檔案總管，瀏覽至 C:\HowTos\Out。請確認 BAM%MessageID%.xml 訊息已寫入至目錄。  
  
#### <a name="to-verify-message-tracking"></a>若要驗證的訊息追蹤  
  
1.  按一下**啟動**在工作列上，指向**所有程式**，指向  [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]，然後按一下  **SQL Server Management Studio**。  
  
2.  按一下 **[新增查詢]**。  
  
3.  在 [查詢] 窗格中，輸入下列命令：  
  
    ```  
    SELECT *  
    FROM [BAMPrimaryImport].[dbo].[bam_ItineraryServiceActivity_Completed]  
    GO  
    ```  
  
4.  按一下 **[執行]**。  
  
5.  在 [結果] 窗格中，使用**時間戳記**找到最新的項目資料行。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [訊息路由模式](../esb-toolkit/message-routing-patterns.md)  
  
-   [使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)