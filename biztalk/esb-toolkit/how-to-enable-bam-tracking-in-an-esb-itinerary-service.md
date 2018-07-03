---
title: 如何： 啟用 BAM 追蹤在 ESB 路線服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58859937-f8d0-4c33-9a7a-62fec8441936
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27d0338ad56daa342fce1d339b9e7aa43fd7e25e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991543"
---
# <a name="how-to-enable-bam-tracking-in-an-esb-itinerary-service"></a>如何： 啟用 BAM 追蹤在 ESB 路線服務
## <a name="goal"></a>目標  
 本節示範如何啟用追蹤現有路線 「 商務活動監視器 」 (BAM)。  
  
 在本使用說明主題中，您將完成下列步驟：  
  
-   啟用用來追蹤使用 「 商務活動監視器的路線服務的屬性。  
  
-   測試使用路線測試用戶端的範例應用程式的 BAM 追蹤。  
  
-   驗證 BAM 結果使用 SQL 查詢。  
  
## <a name="prerequisites"></a>必要條件  
 本使用說明主題中的程序必須完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。  
  
## <a name="before-you-begin"></a>開始之前  
 您執行本使用說明主題中稍後的步驟之前，請完成下列工作：  
  
- 建立 ESB 路線的特定領域語言 (DSL) 模型。  
  
- 設定路線的屬性。  
  
- 定義結構的路線。  
  
  下列程序描述如何進行每一種。  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a>若要建立的 ESB 路線 DSL 模型  
  
1.  在 Visual Studio 中，開啟 [C:\HowTos\Patterns\Patterns.sln]。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新路線**。  
  
3.  在 **加入新項目** 對話方塊中，按一下**ItineraryDsl**範本 窗格中。  
  
4.  在 **名稱**方塊中，輸入**BamTracking**，然後按一下**新增**。  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>若要設定的路線屬性  
  
1.  在 Visual Studio 中，按一下設計介面**BamTracking.itinerary**。 在 [ **BamTracking**屬性] 視窗中，設定下列屬性：  
  
    1.  在 **模型匯出工具**下拉式清單中，按一下**XML 路線匯出工具**。  
  
    2.  在  **Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。  
  
    3.  在 **選取 XML 檔案**對話方塊中，於**檔案名稱**方塊中，輸入**C:\HowTos\Itineraries\BamTracking** ，然後按一下 **儲存**。  
  
        > [!NOTE]
        >  此步驟可讓您將匯出為 XML 的路線，到本機檔案的位置。 而不是匯出至本機檔案位置，路線，路線資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。 您將完成此程序，稍後在本使用說明主題。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義的路線結構  
  
1.  從 [工具箱] 拖曳**匝道**模型項目到設計介面。 在 [ **OnRamp1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**ReceiveNAOrder**。  
  
    2.  在  **Extender**下拉式清單中，按一下**匝道 ESB 服務延伸模組**。  
  
    3.  在  **BizTalk 應用程式**下拉式清單中，按一下**Microsoft.Practices.ESB**。  
  
    4.  在 **接收埠**下拉式清單中，按一下**OnRamp.Itinerary**。  
  
2.  從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並再將其放置在右邊**匝道**模型項目。 在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**MapNAOrderToCNOrder**。  
  
    2.  在 **路線服務的擴充項**下拉式清單中，按一下**傳訊路線服務延伸**。  
  
        > [!NOTE]
        >  這個屬性會定義此程序需要 （傳訊） 的管線中的位置。 或者，如果協調流程中的位置時，會進行的程序，設定**路線服務 Extender**屬性設**協調流程路線服務延伸模組**。  
  
    3.  在 **容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。  
  
    4.  在 **服務名稱**下拉式清單中，按一下**Microsoft.Practices.ESB.Services.Transform**。  
  
3.  以滑鼠右鍵按一下**解析**的集合**MapNAOrderToCNOrder**模型項目，然後按一下**加入新的解析程式**。 在 [ **Resolver1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**StaticallySpecifyTheMap**。  
  
    2.  在 **解析程式實作**下拉式清單中，按一下**靜態的解析程式擴充**。  
  
    3.  在 **轉換的型別**下拉式清單中，按一下**GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**。  
  
    4.  在  **TransportName**下拉式清單中，按一下**檔案**。  
  
4.  在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**ReceiveNAOrder**模型項目**MapNAOrderToCNOrder**模型項目。  
  
5.  從 [工具箱] 拖曳**出口匝**模型項目到設計介面，並再將其放置在右邊**MapNAOrderToCNOrder**模型項目。 在 [ **OffRamp1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**SendCNOrder**。  
  
    2.  在  **Extender**下拉式清單中，按一下**出口匝 ESB 服務延伸模組**。  
  
    3.  在  **BizTalk 應用程式**下拉式清單中，按一下**GlobalBank.ESB**。  
  
    4.  在 **傳送埠**下拉式清單中，按一下**DynamicResolutionOneWay**。  
  
6.  從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並將其之間放置**MapNAOrderToCNOrder**模型項目和**SendCNOrder**模型項目。 在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**SendPortFilter**。  
  
    2.  在 **路線服務的擴充項**下拉式清單中，按一下**出口匝路線服務延伸模組**。  
  
    3.  在 **出口匝**下拉式清單中，展開**SendCNOrder**，然後按一下 **傳送處理常式**。  
  
7.  以滑鼠右鍵按一下**解析**的集合**SendPortFilter**模型項目，然後按一下**加入新的解析程式**。 在 [ **Resolver1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**ConfigureFolderSettings**。  
  
    2.  在 **解析程式實作**下拉式清單中，按一下**靜態的解析程式擴充**。  
  
    3.  在 **傳輸名稱**下拉式清單中，按一下**檔案**。  
  
    4.  按一下 **傳輸位置**屬性，然後按**C:\HowTos\Out\BAM%MessageID%.xml**  
  
        > [!NOTE]
        >  每個出口匝會有相關聯，路線服務結合的路線服務的屬性和出口匝屬性來定義動態傳送埠的訂用帳戶。  
  
8.  在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**MapNAOrderToCNOrder**模型項目**SendPortFilter**模型項目。  
  
9. 在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**SendPortFilter**模型項目**SendCNOrder**模型項目。  
  
10. 儲存專案的所有成品。  
  
## <a name="steps"></a>步驟  
  
#### <a name="to-modify-the-itinerary"></a>若要修改的路線  
  
1.  在 Visual Studio 中，開啟 [C:\HowTos\Patterns\Patterns.sln]。  
  
2.  在 [方案總管] 中，按兩下**BamTracking.itinerary**。  
  
3.  按一下  **MapNAOrderToCNOrder**路線服務項目。  
  
4.  在 [ **MapNAOrderToCNOrder**屬性] 視窗中，按一下 **，則為 True**中**追蹤已啟用**下拉式清單。  
  
5.  按一下  **SendPortFilter**路線服務項目。  
  
6.  在 [ **SendPortFilter**屬性] 視窗中，按一下 **，則為 True**中**追蹤已啟用**下拉式清單。  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>若要匯出使用路線測試用戶端使用的模型  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面**BamTracking**路線，，然後按一下**匯出模型**。  
  
    > [!NOTE]
    >  在 Visual Studio 中，開啟路線的 XML 版本。  
  
2.  儲存專案的所有成品。  
  
3.  在 Windows 檔案總管中，瀏覽至 C:\HowTos\Itineraries 並注意您的路線 XML (BamTracking.xml) 建立。  
  
#### <a name="to-test-the-itinerary"></a>若要測試的路線  
  
1.  開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。  
  
2.  在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後按一下**負載路線**。  
  
3.  在 [**開啟路線檔案**] 對話方塊中，瀏覽至 C:\HowTos\Itineraries。 選取  **BamTracking.xml**，然後按一下**開啟**載入路線。  
  
4.  按一下  **確定**清除**路線成功載入**訊息。  
  
5.  在路線測試用戶端中，按一下 [旁的省略符號按鈕 （...）**載入訊息**] 方塊中。  
  
6.  在 [**選取要載入的 XML 文件**] 對話方塊中，瀏覽至 C:\HowTos。 選取  **NAOrderDoc.xml**，然後按一下**開啟**載入測試訊息。  
  
7.  按一下 [**送出要求**] 按鈕。 測試完成時，按一下**確定**關閉顯示的確認。  
  
8.  在 Windows 檔案總管中，瀏覽至 C:\HowTos\Out。確認目錄中已寫入 BAM%MessageID%.xml 訊息。  
  
#### <a name="to-verify-message-tracking"></a>若要確認訊息追蹤  
  
1. 按一下 **開始**在工作列上，指向**所有程式**，指向[!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]，然後按一下**SQL Server Management Studio**。  
  
2. 按一下 **[新增查詢]**。  
  
3. 在 [查詢] 窗格中，輸入下列命令：  
  
   ```  
   SELECT *  
   FROM [BAMPrimaryImport].[dbo].[bam_ItineraryServiceActivity_Completed]  
   GO  
   ```  
  
4. 按一下 **[執行]**。  
  
5. 在 [結果] 窗格中，使用**時間戳記**欄找出最新的項目。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [訊息路由模式](../esb-toolkit/message-routing-patterns.md)  
  
-   [使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)