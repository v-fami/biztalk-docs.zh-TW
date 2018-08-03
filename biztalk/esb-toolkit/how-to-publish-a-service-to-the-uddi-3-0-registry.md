---
title: 如何： 將服務發佈至 UDDI 3.0 登錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2c3bd0ed-e5f1-43eb-98d1-e3247a565ba2
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb5ab38da9c78831b319d8c64e789b442fb6eef5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008015"
---
# <a name="how-to-publish-a-service-to-the-uddi-30-registry"></a>如何： 將服務發佈至 UDDI 3.0 登錄
## <a name="goal"></a>目標  
 本節示範如何使用 「 UDDI 服務網站來發佈 Web 服務端點可用於路由訊息，ESB 路線內解析從。 您將複製現有的 PurchaseOrderSubmitOrderService 服務目前發行至登錄。  

 在本使用說明主題中，您將完成下列步驟：  

-   將服務發佈至通用描述、 探索與整合 (UDDI) 3 使用 「 UDDI 發行者 」 工具的登錄。  

-   測試使用路線傳閱解析使用 UDDI3 解析程式服務端點的服務發行集。  

## <a name="prerequisites"></a>必要條件  
 本使用說明主題中的程序必須完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)及執行 （您可以在安裝 %esb 安裝 Folder%\Bin\ 此 「 UDDI 發行者 」 工具Microsoft.Practices.ESB.UDDIPublisher.exe)。  

## <a name="steps"></a>步驟  

#### <a name="to-create-the-newposervice-in-the-uddi-registry"></a>若要在 UDDI 登錄中建立 NewPOService  

1.  在 Internet Explorer 中，瀏覽至 UDDI 服務站台 (根據預設，此 URL 是http://localhost/uddi)。  

2.  在  **uddi 服務站**頁面上，按一下**發佈**。  

3.  在 [發行] 窗格中，以滑鼠右鍵按一下**Microsoft.Practices.ESB**，然後按一下**加入服務**。  

4.  在下列頁面上，選取**指定要使用的金鑰**，然後按一下**繼續**。  

5.  在下列頁面上，按一下**esb**主要磁碟分割。 在 **機碼後置詞**方塊中，輸入**newposervice**，然後按一下**繼續**。  

6.  在下列頁面上，旁邊 (**新的服務名稱**)，按一下**編輯**。 將服務命名**NewPOService**，然後按一下**更新**。  

7.  按一下 **新增描述**，輸入服務的描述 (例如**範例服務**)，然後按一下 **更新**。  

#### <a name="to-add-a-binding-for-the-newposervice"></a>若要加入 NewPOService 繫結  

1.  按一下 **繫結**索引標籤，然後再按一下**新增繫結**。  

2.  選取 **指定要使用的金鑰**，然後按一下**繼續**。  

3.  在下列頁面上，按一下**esb**主要磁碟分割。 在 **機碼後置詞**方塊中，輸入**newposervicebinding**，然後按一下**繼續**。  

4.  底下**存取點**，按一下**編輯**，然後完成下列：  

    1.  在 **存取點**方塊中，輸入**http://localhost/ESB.CanadianServices/SubmitPOService.asmx**。  

    2.  在**使用型別**下拉式清單中，按一下**端點**，然後按一下**Update**。  

#### <a name="to-configure-the-binding-instance-information"></a>若要設定的繫結執行個體資訊  

1. 按一下 **例項資訊**索引標籤，然後再按一下**新增例項資訊**。  

2. 在 **搜尋 tModel 名稱中包含**方塊中，輸入**esb %** ，然後按一下 **搜尋**。  

3. 找出並按一下**tModel** for **transporttype**。  

   > [!NOTE]
   >  若要完成此程序的其餘步驟，您可能必須變更第 1 頁和第 2 頁之間。  

4. 在 **描述**區段中，按一下**新增描述**。  

5. 在 **描述**方塊中，輸入**ESB 路線使用的傳輸類型**，然後按一下**更新**。  

6. 按一下 **執行個體詳細資料**索引標籤，然後再按一下**編輯**。  

7. 在 **例項參數**方塊中，輸入**Wcf-basichttp**，然後按一下**Update**。  

8. 在 **描述**區段中，按一下**新增描述**。  

9. 在 **描述**方塊中，輸入**基本 HTTP 傳輸 WCF**，然後按一下**更新**。  

10. 在 [發行] 窗格中，在**NewPOService**，按一下**http://localhost/esb.canadianservices/submitposervice.asmx**。  

11. 在 **例項資訊**索引標籤上，按一下**新增例項資訊**。  

12. 使用稍早所述的步驟，加入下列的執行個體資訊，根據下表所示的值。  


    |                           tModel                           |       描述        |                          參數                           |         參數描述          |
    |------------------------------------------------------------|--------------------------|--------------------------------------------------------------|----------------------------------------|
    | microsoft-com:esb:runtimeresolution:messageexchangepattern | 訊息交換模式 |                           雙向                            |           雙向作業            |
    |      microsoft-com:esb:runtimeresolution:cachetimeout      |      快取逾時       |                              -1                              |           目前已停用           |
    |     microsoft-com:esb:runtimeresolution:jaxrpcresponse     |      JaxRpcResponse      |                            false                             |                                        |
    |         microsoft-com:esb:runtimeresolution:action         |      服務動作      |                         submitOrder                          | 指定要叫用服務方法 |
    |    microsoft-com:esb:runtimeresolution:targetnamespace     |    服務命名空間     | http://globalbank.esb.dynamicresolution.com/canadianservices |            目標命名空間            |

#### <a name="to-configure-the-binding-categorization"></a>若要設定繫結分類  

1.  在 [發行] 窗格中，在**NewPOService**，按一下**http://localhost/esb.canadianservices/submitposervice.asmx**。  

2.  在 **分類**索引標籤上，按一下**新增自訂類別**。  

3.  在 **搜尋**方塊中，輸入**esb %** ，然後按一下 **搜尋**。  

4.  找出並按一下**microsoft-com:esb:runtimeresolution:biztalkapplication** tModel。  

5.  在  **Key-name**方塊中，輸入**BizTalk 應用程式**。  

6.  在 **資料索引鍵值**方塊中，輸入**Microsoft.Practices.ESB**，然後按一下 **新增類別**。  

7.  使用稍早所述的步驟，加入下列的自訂類別，根據下表所示的值。  

    |tModel|機碼名稱|機碼值|  
    |------------|--------------|---------------|  
    |microsoft-com:esb:runtimeresolution:portname|連接埠名稱|NewPOService|  
    |microsoft-com:esb:runtimeresolution:transporttype|傳輸類型|WCF-BasicHttp|  

#### <a name="to-locate-the-service-in-the-uddi-registry"></a>若要在 UDDI 登錄中找出服務  

1.  在 Internet Explorer 上**uddi 服務站**頁面上，按一下**搜尋**。  

2.  按一下 [ **Services** ] 索引標籤。  

3.  在 **服務名稱**方塊中，輸入 **%po**，然後按一下**搜尋**。  

4.  在 **搜尋**窗格上**結果**索引標籤上，按一下  **NewPOService**。  

    > [!NOTE]
    >  這可確認服務已成功發行至登錄。  

#### <a name="to-create-an-itinerary-model-to-test-the-uddi-service-publication"></a>若要建立路線的模型，以測試 「 UDDI 服務發行  

1.  在 Visual Studio 中，開啟 [C:\HowTos\Patterns\Patterns.sln]。  

2.  在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新路線**。  

3.  在 **加入新項目**對話方塊中，於**名稱**方塊中，輸入**NewBindingKeySearch**，然後按一下 **新增**。  

#### <a name="to-configure-the-properties-of-the-itinerary"></a>若要設定的路線屬性  

1.  在 Visual Studio 中，按一下設計介面**NewBindingKeySearch.itinerary**。 在 [ **NewBindingKeySearch**屬性] 視窗中，設定下列屬性：  

    1.  在 **是要求回應**下拉式清單中，按一下 **，則為 True**。  

    2.  在 **模型匯出工具**下拉式清單中，按一下**XML 路線匯出工具**。  

    3.  在  **Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。  

    4.  在 [**選取 XML 檔案**] 對話方塊中，輸入**C:\HowTos\Itineraries\NewBindingKeySearch**中**檔名**方塊，然後再按一下**儲存**.  

        > [!NOTE]
        >  此步驟可讓您將匯出為 XML 的路線，到本機檔案的位置。 而不是匯出至本機檔案位置，路線，路線資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。 您將完成此程序，稍後在本使用說明主題。  

#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義的路線結構  

1.  從 [工具箱] 拖曳**匝道**模型項目到設計介面。 在 [ **OnRamp1**屬性] 視窗中，設定下列屬性：  

    1.  按一下 **名稱**屬性，然後按**ReceiveNAOrder**。  

    2.  在  **Extender**下拉式清單中，按一下**匝道 ESB Extender**。  

    3.  在  **BizTalk 應用程式**下拉式清單中，按一下**Microsoft.Practices.ESB**。  

    4.  在 **接收埠**下拉式清單中，按一下**OnRamp.Itinerary.Response**。  

2.  從 [工具箱] 拖曳**路線服務**模型項目到設計介面。 在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：  

    1.  按一下 **名稱**屬性，然後按**TransformNAOrder**。  

    2.  在 **路線服務的擴充項**下拉式清單中，按一下**傳訊 Extender**。  

    3.  在 **容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。  

    4.  在 **服務名稱**下拉式清單中，按一下**Microsoft.Practices.ESB.Services.Transform**。  

3.  以滑鼠右鍵按一下**解析**的集合**TransformNAOrder**模型項目，然後按一下**加入新的解析程式**。 在 [ **Resolver1**屬性] 視窗中，設定下列屬性：  

    1.  按一下 **名稱**屬性，然後按**NAOrder_to_CNOrder**。  

    2.  在 **解析程式實作**下拉式清單中，按一下**靜態的解析程式擴充**。  

    3.  在 **轉換的型別**下拉式清單中，按一下**GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**。  

4.  在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**ReceiveNAOrder**模型項目**TransformNAOrder**模型項目。  

5.  從 [工具箱] 拖曳**路線服務**模型項目到設計介面。 在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：  

    1.  按一下 **名稱**屬性，然後按**BindingKeyRoute**。  

    2.  在 **路線服務的擴充項**下拉式清單中，按一下**傳訊 Extender**。  

    3.  在 **容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。  

    4.  在 **服務名稱**下拉式清單中，按一下**Microsoft.Practices.ESB.Services.Routing**。  

6.  以滑鼠右鍵按一下**解析**的集合**BindingKeyRoute**模型項目，然後按一下**加入新的解析程式**。 在 [ **Resolver1**屬性] 視窗中，設定下列屬性：  

    1.  按一下 **名稱**屬性，然後按**BindingKeySearch**。  

    2.  在 **解析程式實作**下拉式清單中，按一下**Uddi3 解析程式擴充功能**。  

    3.  在 **解析 Moniker**下拉式清單中，按一下**UDDI3**。  

    4.  按一下 **繫結索引鍵**屬性，然後按**uddi:esb:newposervicebinding**。 若要尋找的索引鍵值，請按一下http://localhost/ESB.CanadianServices/SubmitPOService.asmxUDDI 中的服務，然後按一下 更多詳細資料。  

7.  以滑鼠右鍵按一下**BindingKeySearch**解析程式，然後再按一下**測試解析程式組態**。  

    > [!NOTE]
    >  確認 [輸出] 視窗中顯示的輸出。  

8.  在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**TransformNAOrder**模型項目**BindingKeyRoute**模型項目。  

9. 從 [工具箱] 拖曳**出口匝**模型項目到設計介面，並再將其放置在右邊**BindingKeyRoute**模型項目。 在 [ **OffRamp1**屬性] 視窗中，設定下列屬性：  

    1.  按一下 **名稱**屬性，然後按**SendCNOrder**。  

    2.  在  **Extender**下拉式清單中，按一下**出口匝 ESB Extender**。  

    3.  在  **BizTalk 應用程式**下拉式清單中，按一下**GlobalBank.ESB**。  

    4.  在 **傳送埠**下拉式清單中，按一下**DynamicResolutionSolicitResp**。  

10. 從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並將其之間放置**BindingKeyRoute**模型項目和**SendCNOrder**模型項目。 在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：  

    1.  按一下 **名稱**屬性，然後按**SendPortFilter**。  

    2.  在 **路線服務的擴充項**下拉式清單中，按一下**出口匝 Extender**。  

    3.  在 **出口匝**下拉式清單中，展開**SendCNOrder**，然後按一下 **傳送處理常式**。  

11. 在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**BindingKeyRoute**模型項目**SendPortFilter**模型項目。  

12. 在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**SendPortFilter**模型項目**SendNAOrder**模型項目。  

#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>若要匯出使用路線測試用戶端使用的模型  

1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面**NewBindingKeySearch**路線，，然後按一下**匯出模型**。  

    > [!NOTE]
    >  在 Visual Studio 中，開啟路線的 XML 版本。  

2.  儲存專案的所有成品。  

3.  在 Windows 檔案總管中，瀏覽至 C:\HowTos\Itineraries 並注意您的路線 XML (NewBindingKeySearch.xml) 建立。  

#### <a name="to-test-the-itinerary"></a>若要測試的路線  

1.  開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。  

2.  在路線測試用戶端，在**Web 服務選項**群組中，清除**使用 WCF 服務**方塊，然後選取**雙向服務**核取方塊。  

3.  按一下 [**負載路線**] 按鈕。  

4.  在 [**開啟路線檔案**] 對話方塊中，瀏覽至 C:\HowTos\Itineraries。 選取  **NewBindingKeySearch.xml**，然後按一下**開啟**載入路線。  

5.  按一下  **確定**清除**路線成功載入**訊息。  

6.  在路線測試用戶端中，按一下 [旁的省略符號按鈕 （...）**載入訊息**] 方塊中。  

7.  在 [**選取要載入的 XML 文件**] 對話方塊中，瀏覽至 C:\HowTos。 選取  **NAOrderDoc.xml**，然後按一下**開啟**載入測試訊息。  

8.  按一下 [**送出要求**] 按鈕。 測試完成時，按一下**確定**關閉顯示的確認。  

9. 確認正確的回應訊息會出現在**結果**的文字方塊**Itineray 測試用戶端**。  

## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  

-   [如何：使用 UDDI 繫結索引鍵搜尋解決服務端點](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  

-   [如何：使用 UDDI 類別搜尋解決服務端點](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  

-   [開發活動](../esb-toolkit/development-activities.md)