---
title: "如何： 將服務發行至 UDDI 3.0 登錄 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c3bd0ed-e5f1-43eb-98d1-e3247a565ba2
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca41923dc4c392959af9f19cf3b7c32f6bfe7c20
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-publish-a-service-to-the-uddi-30-registry"></a>如何： 將服務發行至 UDDI 3.0 登錄
## <a name="goal"></a>目標  
 本節示範如何使用 「 UDDI 服務網站發佈 Web 服務端點可以從中解析內路線為了 ESB 訊息路由傳送的。 您將複製現有的 PurchaseOrderSubmitOrderService 服務目前發行至登錄。  
  
 在此 「 如何 」 主題，您將完成下列步驟：  
  
-   將服務發行至通用描述、 探索與整合 (UDDI) 3 登錄使用此 「 UDDI 發行者 」 工具。  
  
-   服務發行集使用路線路由略過的測試解析使用 UDDI3 解析程式的服務端點。  
  
## <a name="prerequisites"></a>必要條件  
 在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)及執行 「 UDDI 發行者 」 工具 （您可以將它安裝在 %esb 安裝 Folder%\Bin\Microsoft.Practices.ESB.UDDIPublisher.exe)。  
  
## <a name="steps"></a>步驟  
  
#### <a name="to-create-the-newposervice-in-the-uddi-registry"></a>若要建立 NewPOService UDDI 登錄中  
  
1.  在 Internet Explorer 中，瀏覽至 UDDI 服務網站 （根據預設，這個 URL 是 http://localhost/uddi）。  
  
2.  在**uddi 服務**頁面上，按一下**發行**。  
  
3.  在 發行 窗格中，以滑鼠右鍵按一下**Microsoft.Practices.ESB**，然後按一下 **加入服務**。  
  
4.  在下列頁面上，選取**指定要使用的金鑰**，然後按一下 **繼續**。  
  
5.  在下列頁面上，按一下  **esb**資料分割索引鍵。 在**機碼後置詞**方塊中，輸入**newposervice**，然後按一下 **繼續**。  
  
6.  在下列頁面上，旁邊 (**新的服務名稱**)，按一下 **編輯**。 為服務名稱**NewPOService**，然後按一下 **更新**。  
  
7.  按一下**新增描述**，輸入服務的描述 (例如，**範例服務**)，然後按一下 **更新**。  
  
#### <a name="to-add-a-binding-for-the-newposervice"></a>若要新增繫結的 NewPOService  
  
1.  按一下**繫結**索引標籤，然後再按一下**新增繫結**。  
  
2.  選取**指定要使用的金鑰**，然後按一下 **繼續**。  
  
3.  在下列頁面上，按一下  **esb**資料分割索引鍵。 在**機碼後置詞**方塊中，輸入**newposervicebinding**，然後按一下 **繼續**。  
  
4.  在下**存取點**，按一下 **編輯**，然後完成下列：  
  
    1.  在**存取點**方塊中，輸入**http://localhost/ESB.CanadianServices/SubmitPOService.asmx**。  
  
    2.  在**使用型別**下拉式清單中，按一下 **端點**，然後按一下 **更新**。  
  
#### <a name="to-configure-the-binding-instance-information"></a>若要設定的繫結執行個體資訊  
  
1.  按一下**例項資訊**索引標籤，然後再按一下**新增例項資訊**。  
  
2.  在**搜尋 tModel 名稱中包含**方塊中，輸入**%esb** ，然後按一下 **搜尋**。  
  
3.  找出並按一下**tModel**如**transporttype**。  
  
    > [!NOTE]
    >  若要完成此程序中的其餘步驟，您可能必須變更第 1 頁和第 2 頁之間。  
  
4.  在**描述**區段中，按一下**新增描述**。  
  
5.  在**描述**方塊中，輸入**ESB 行程使用的傳輸類型**，然後按一下 **更新**。  
  
6.  按一下**執行個體詳細資料**索引標籤，然後再按一下**編輯**。  
  
7.  在**例項參數**方塊中，輸入**Wcf-basichttp**，然後按一下 **更新**。  
  
8.  在**描述**區段中，按一下**新增描述**。  
  
9. 在**描述**方塊中，輸入**WCF 基本 HTTP 傳輸**，然後按一下 **更新**。  
  
10. 在 發行 窗格中，在**NewPOService**，按一下  **http://localhost/esb.canadianservices/submitposervice.asmx**。  
  
11. 在**例項資訊**索引標籤上，按一下 **新增例項資訊**。  
  
12. 使用稍早所述的步驟，加入下列的執行個體資訊，請根據下表中所顯示的值。  
  
    |tModel|Description|參數|參數描述|  
    |------------|-----------------|---------------|---------------------------|  
    |microsoft-com:esb:runtimeresolution:messageexchangepattern|訊息交換模式|雙向|雙向作業|  
    |microsoft-com:esb:runtimeresolution:cachetimeout|快取逾時|-1|目前已停用|  
    |microsoft-com:esb:runtimeresolution:jaxrpcresponse|JaxRpcResponse|false||  
    |microsoft-com:esb:runtimeresolution:action|服務動作|submitOrder|指定要叫用的服務方法|  
    |microsoft-com:esb:runtimeresolution:targetnamespace|服務命名空間|http://globalbank.esb.dynamicresolution.com/canadianservices|目標命名空間|  
  
#### <a name="to-configure-the-binding-categorization"></a>若要設定繫結分類  
  
1.  在 發行 窗格中，在**NewPOService**，按一下  **http://localhost/esb.canadianservices/submitposervice.asmx**。  
  
2.  在**類別**索引標籤上，按一下 **新增自訂類別**。  
  
3.  在**搜尋**方塊中，輸入**%esb** ，然後按一下 **搜尋**。  
  
4.  找出並按一下**microsoft-com:esb:runtimeresolution:biztalkapplication** tModel。  
  
5.  在**機碼名稱**方塊中，輸入**BizTalk 應用程式**。  
  
6.  在**鍵值**方塊中，輸入**Microsoft.Practices.ESB**，然後按一下 **新增類別**。  
  
7.  使用稍早所述的步驟，加入下列自訂分類，根據下表中所顯示的值。  
  
    |tModel|機碼名稱|機碼值|  
    |------------|--------------|---------------|  
    |microsoft-com:esb:runtimeresolution:portname|連接埠名稱|NewPOService|  
    |microsoft-com:esb:runtimeresolution:transporttype|傳輸類型|WCF-BasicHttp|  
  
#### <a name="to-locate-the-service-in-the-uddi-registry"></a>UDDI 登錄中尋找服務  
  
1.  在 Internet Explorer 上**uddi 服務**頁面上，按一下**搜尋**。  
  
2.  按一下**服務** 索引標籤。  
  
3.  在**服務名稱**方塊中，輸入**%PO%**，然後按一下 **搜尋**。  
  
4.  在**搜尋**窗格，請在**結果**索引標籤上，按一下  **NewPOService**。  
  
    > [!NOTE]
    >  這可確認服務已順利發行至登錄。  
  
#### <a name="to-create-an-itinerary-model-to-test-the-uddi-service-publication"></a>若要建立路線的模型來測試 UDDI 服務發行  
  
1.  在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，開啟 C:\HowTos\Patterns\Patterns.sln。  
  
2.  在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。  
  
3.  在**加入新項目**對話方塊中，於**名稱**方塊中，輸入**NewBindingKeySearch**，然後按一下 **新增**。  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>若要設定的路線屬性  
  
1.  在 Visual Studio 中，按一下設計介面的**NewBindingKeySearch.itinerary**。 在**NewBindingKeySearch**屬性 視窗中，設定下列屬性：  
  
    1.  在**為要求回應**下拉式清單中，按一下  **True**。  
  
    2.  在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。  
  
    3.  在**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。  
  
    4.  在**選取 XML 檔案** 對話方塊中，輸入**C:\HowTos\Itineraries\NewBindingKeySearch**中**檔案名稱**方塊，然後再按一下**儲存**.  
  
        > [!NOTE]
        >  這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。 藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。 您將完成此程序，稍後在本使用說明主題。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義路線結構  
  
1.  從 [工具箱] 拖曳**上手**至設計介面的模型項目。 在**OnRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **上手 ESB Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。  
  
    4.  在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary.Response**。  
  
2.  從 [工具箱] 拖曳**路線服務**至設計介面的模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**TransformNAOrder**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。  
  
    3.  在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。  
  
    4.  在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Transform**。  
  
3.  以滑鼠右鍵按一下**解析程式**集合**TransformNAOrder**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**NAOrder_to_CNOrder**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**轉換類型**下拉式清單中，按一下  **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**。  
  
4.  在工具箱中，按一下 **連接器**。 拖曳連接**ReceiveNAOrder**模型項目的**TransformNAOrder**模型項目。  
  
5.  從 [工具箱] 拖曳**路線服務**至設計介面的模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**BindingKeyRoute**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。  
  
    3.  在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。  
  
    4.  在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。  
  
6.  以滑鼠右鍵按一下**解析程式**集合**BindingKeyRoute**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**BindingKeySearch**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下  **Uddi3 解析程式擴充功能**。  
  
    3.  在**解析程式 Moniker**下拉式清單中，按一下  **UDDI3**。  
  
    4.  按一下**繫結索引鍵**屬性，，然後輸入**uddi:esb:newposervicebinding**。 若要尋找的索引鍵值，按一下 http://localhost/ESB.CanadianServices/SubmitPOService.asmx 中的服務 「 UDDI，，然後按一下 更多詳細資料。  
  
7.  以滑鼠右鍵按一下**BindingKeySearch**解析程式，然後再按一下**測試解析程式組態**。  
  
    > [!NOTE]
    >  確認 [輸出] 視窗中顯示的輸出。  
  
8.  在工具箱中，按一下 **連接器**。 拖曳連接**TransformNAOrder**模型項目的**BindingKeyRoute**模型項目。  
  
9. 從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**BindingKeyRoute**模型項目。 在**OffRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendCNOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。  
  
    4.  在**傳送埠**下拉式清單中，按一下  **DynamicResolutionSolicitResp**。  
  
10. 從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**BindingKeyRoute**模型項目和**SendCNOrder**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendPortFilter**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。  
  
    3.  在**匝道**下拉式清單中，展開**SendCNOrder**，然後按一下 **傳送處理常式**。  
  
11. 在工具箱中，按一下 **連接器**。 拖曳連接**BindingKeyRoute**模型項目的**SendPortFilter**模型項目。  
  
12. 在工具箱中，按一下 **連接器**。 拖曳連接**SendPortFilter**模型項目的**SendNAOrder**模型項目。  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>若要匯出的行程測試用戶端使用的模型  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**NewBindingKeySearch**路線，然後再按一下**匯出模型**。  
  
    > [!NOTE]
    >  在 Visual Studio 中，開啟路線的 XML 版本。  
  
2.  儲存專案的所有成品。  
  
3.  在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries 並注意您路線 XML (NewBindingKeySearch.xml) 建立。  
  
#### <a name="to-test-the-itinerary"></a>若要測試路線  
  
1.  開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。  
  
2.  在路線測試用戶端，在**Web 服務選項**群組中，清除**使用 WCF 服務**方塊，然後選取 **雙向服務**核取方塊。  
  
3.  按一下**負載路線** 按鈕。  
  
4.  在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。 選取**NewBindingKeySearch.xml**，然後按一下 **開啟**載入路線。  
  
5.  按一下**確定**清除**路線成功載入**訊息。  
  
6.  在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。  
  
7.  在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。 選取**NAOrderDoc.xml**，然後按一下 **開啟**載入測試訊息。  
  
8.  按一下**送出要求** 按鈕。 測試完成時，按一下**確定**解除顯示的確認。  
  
9. 請確認正確的回應訊息出現在**結果**文字方塊**Itineray 測試用戶端**。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [如何： 解決使用繫結機碼搜尋 UDDI 服務端點](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  
  
-   [如何： 解決使用 UDDI 類別目錄搜尋之服務端點](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  
  
-   [開發活動](../esb-toolkit/development-activities.md)