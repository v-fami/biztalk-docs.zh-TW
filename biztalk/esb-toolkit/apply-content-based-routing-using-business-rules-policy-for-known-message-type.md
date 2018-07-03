---
title: 如何： 實作內容架構路由使用商務規則的已知的訊息類型的原則 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44451c85-929a-4d13-b0dd-53ea600d0859
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7b47fd54aaf6dc93ed26ba7efec3b14bf31401e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004911"
---
# <a name="how-to-implement-content-based-routing-using-a-business-rules-policy-for-a-known-message-type"></a>如何： 實作內容架構路由使用商務規則原則已知的訊息類型
## <a name="goal"></a>目標  
 本節示範如何建立路線動態路由傳送訊息時，根據已知的訊息類型 （結構描述部署到 Microsoft BizTalk Server 組態資料庫） 的內容，使用商務規則原則。  
  
 在本使用說明主題中，您將完成下列步驟：  
  
-   建立將用來路由傳送訊息，內容為基礎的商務規則原則。  
  
-   建立路線傳閱具有動態路由傳送訊息的 BRE 解析程式。  
  
-   測試使用路線測試用戶端的範例應用程式的路線。  
  
## <a name="prerequisites"></a>必要條件  
 本使用說明主題中的程序必須完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。  
  
## <a name="before-you-begin"></a>開始之前  
 您執行本使用說明主題中稍後的步驟之前，請完成下列工作：  
  
- 建立 GlobalBank 西部測試訊息。  
  
- 建立 GlobalBank 東部測試訊息。  
  
  下列程序描述如何進行每一種。  
  
#### <a name="to-create-the-globalbank-west-test-message"></a>若要建立 GlobalBank 西部測試訊息  
  
1.  在 Windows 檔案總管中，瀏覽至 C:\HowTos。  
  
2.  建立一份 NAOrderDoc.xml，並命名 West.xml 的複本。  
  
3.  在記事本中，開啟 West.xml，然後再將值變更**customerName**項目**GlobalBankWest**。  
  
4.  儲存 West.xml 為 utf-8，，然後關閉 [記事本]。  
  
#### <a name="to-create-the-globalbank-east-test-message"></a>若要建立 GlobalBank 東部測試訊息  
  
1.  在 Windows 檔案總管中，瀏覽至 C:\HowTos。  
  
2.  建立一份 NAOrderDoc.xml，並命名 East.xml 的複本。  
  
3.  在記事本中，開啟 East.xml，然後再將值變更**customerName**項目**GlobalBankEast**。  
  
4.  儲存 East.xml 為 utf-8，，然後關閉 [記事本]。  
  
## <a name="steps"></a>步驟  
  
#### <a name="to-create-a-bre-policy-to-route-using-custom-message-properties"></a>若要建立 BRE 原則，以路由傳送使用自訂訊息屬性  
 此規則會使用客戶的名稱，以動態方式設定用來將訊息路由傳送的端點。  
  
1.  按一下 **開始**在工作列上，指向**所有程式**，指向**BizTalk Server**，然後按一下**商務規則編輯器 」**。  
  
2.  在 [原則總管] 中，以滑鼠右鍵按一下**原則**，然後按一下**新增新的原則**。 命名原則**RouteBasedOnCustomerKnownType**。  
  
#### <a name="to-add-a-routing-rule-for-customer-globalbank-west"></a>若要新增客戶 GlobalBank 西部路由規則  
  
1. 在  **RouteBasedOnCustomerKnownType**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **新增規則**。 命名規則**SetWestEndpoint**。  
  
2. 在 [事實總管] 中，按一下**XML 結構描述**索引標籤上，以滑鼠右鍵按一下**結構描述**，然後按一下**瀏覽**。  
  
3. 在 [**結構描述檔案**] 對話方塊中，瀏覽至 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB。選取 DynamicResolution.Schemas **NAOrderDoc.xsd**，然後按一下**開啟**。  
  
   > [!NOTE]
   >  這是定義 NAOrderDoc.xml 訊息，這用來建立您將用來測試西和東訊息的結構描述。  
  
4. 在 [事實總管] 中，按一下**NAOrderDoc.xsd**，然後在 [屬性] 窗格中，按一下**文件類型**屬性，然後按**GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.  
  
   > [!NOTE]
   >  這是結構描述的完整的名稱。  
  
5. 在 [事實總管] 中，展開**NAOrderDoc.xsd**，然後展開**OrderDoc**。  
  
6. 在 [規則] 視窗中，以滑鼠右鍵按一下**條件**，指向**述詞**，然後按一下**等於**。  
  
7. 從 [事實總管] 中，拖曳**customerName**項目**引數 1**節點底下**條件**。  
  
8. 按一下  **argument2**節點，然後按**GlobalBankWest**。  
  
9. 在 [事實總管] 中，按一下**詞彙**索引標籤上，依序展開**ESB。EndPointInfo**，然後展開**1.0 版**。  
  
   > [!NOTE]
   >  [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含數個可用來建立規則，用於在 ESB 的詞彙。 其中某些應該取代或夾帶您自己的詞彙。 例如， **DynamicRunTimeMaptypes**已定義中的對應**GlobalBank**範例。  
  
10. 從 [事實總管] 中，拖曳**設定結束點輸出傳輸位置**定義**動作**。  
  
11. 按一下  **\<空字串\>** ，然後輸入**C:\HowTos\Out\West%MessageID%.xml**。  
  
12. 從 [事實總管] 中，拖曳**設定結束點輸出傳輸類型**定義**動作**。  
  
13. 在 [事實總管] 中，展開**ESB。TransportTypes**，依序展開**1.0 版**，然後將拖曳**配接器提供者**定義**\<空字串\>**.  
  
14. 在 **動作**窗格中，展開**配接器提供者**下拉式清單中，然後再按一下**檔案**。  
  
#### <a name="to-add-a-routing-rule-for-customer-globalbank-east"></a>若要新增客戶 GlobalBank 東部路由規則  
  
1.  在 [原則總管] 中，以滑鼠右鍵按一下**SetWestEndpoint**規則，然後按一下**複製**。  
  
2.  以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**貼上**。  
  
3.  在**新的規則名稱**] 對話方塊中，輸入**SetEastEndpoint**，然後按一下 [**確定**。  
  
4.  在 [原則總管] 中，按一下**SetEastEndpoint**規則。  
  
5.  在 **條件**區段中，以滑鼠右鍵按一下**GlobalBankWest**，然後按一下**重設引數**。  
  
6.  按一下  **argument2**，然後輸入**GlobalBankEast**。  
  
7.  在 **動作**區段中，以滑鼠右鍵按一下**C:\HowTos\Out\West%MessageID%.xml**，然後按一下**重設引數**。  
  
8.  按一下  **\<空字串\>**，然後輸入**C:\HowTos\Out\East%MessageID%.xml**。  
  
#### <a name="to-add-a-routing-rule-for-unknown-customers"></a>未知的客戶新增路由規則  
  
1.  在 RouteBasedOnCustomerKnownType 原則中，請以滑鼠右鍵按一下 1.0 版 （未儲存），，，然後按一下 新增規則。 命名規則 SetUnknownCustomerEndpoint。  
  
2.  在 [規則] 視窗中，以滑鼠右鍵按一下 [條件]，然後按一下新增邏輯 and。  
  
3.  在 規則 視窗中，以滑鼠右鍵按一下，指向 述詞，然後按一下 不等於。  
  
4.  在 [事實總管] 中，按一下 [XML 結構描述] 索引標籤中，展開 NAOrderDoc.xsd，，然後展開 OrderDoc。  
  
5.  從 事實總管 中，請 customerName 元件拖曳至 條件下的 引數 1 節點。  
  
6.  按一下 引數 2 節點，然後輸入 GlobalBankWest。  
  
7.  在 規則 視窗中，以滑鼠右鍵按一下，指向 述詞，然後按一下 不等於。  
  
8.  從 事實總管 中，請 customerName 元件拖曳至 條件下的 引數 1 節點。  
  
9. 按一下 引數 2 節點，然後輸入 GlobalBankEast。  
  
10. 在 事實總管 中，按一下 詞彙 索引標籤中，展開 ESB。EndPointInfo，然後展開 1.0 版。  
  
11. 從 [事實總管] 中，拖曳設定結束點輸出傳輸位置定義的動作。  
  
12. 按一下 \<空字串\>，然後輸入 C:\HowTos\Out\CustomerUnknown%MessageID%.xml。  
  
13. 從 [事實總管] 中，拖曳設定結束點輸出傳輸類型定義的動作。  
  
14. 在 事實總管 中，展開 ESB。TransportTypes，依序展開 1.0 版，然後拖曳 配接器提供者定義，以\<空字串\>。  
  
15. 在 [動作] 窗格中，展開 [配接器提供者] 下拉式清單中，，然後按一下檔案。  
  
#### <a name="to-publish-and-deploy-the-policy"></a>發佈和部署原則  
  
1.  在 [原則總管] 中，在**RouteBasedOnCustomerKnownType**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**發行**。  
  
2.  在 [原則總管] 中，在**RouteBasedOnCustomerKnownType**原則，以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下**部署**。  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a>若要建立的 ESB 路線 DSL 模型  
  
1.  在 Visual Studio 中，開啟 [C:\HowTos\Patterns\Patterns.sln]。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新路線**。  
  
3.  在 **加入新項目**對話方塊中，於**名稱**方塊中，輸入**CbrKnownType**，然後按一下 **新增**。  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>若要設定的路線屬性  
  
1.  在 Visual Studio 中，按一下設計介面**CbrKnownType.itinerary**。 在 [ **CbrKnownType**屬性] 視窗中，設定下列屬性：  
  
    1.  在 **模型匯出工具**下拉式清單中，按一下**XML 路線匯出工具**。  
  
    2.  在  **Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。  
  
    3.  在 [**選取 XML 檔案**] 對話方塊中，輸入**C:\HowTos\Itineraries\CbrKnownType**中**檔名**方塊，然後再按一下**儲存**。  
  
        > [!NOTE]
        >  此步驟可讓您將匯出為 XML 的路線，到本機檔案的位置。 而不是匯出至本機檔案位置，路線，路線資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。 您將完成此程序，稍後在本使用說明主題。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義的路線結構  
  
1.  從 [工具箱] 拖曳**匝道**模型項目到設計介面。 在 [ **OnRamp1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**ReceiveNAOrder**。  
  
    2.  在  **Extender**下拉式清單中，按一下**匝道 ESB Extender**。  
  
    3.  在  **BizTalk 應用程式**下拉式清單中，按一下**Microsoft.Practices.ESB**。  
  
    4.  在 **接收埠**下拉式清單中，按一下**OnRamp.Itinerary**。  
  
2.  從 [工具箱] 拖曳**出口匝**模型項目到設計介面，並再將其放置在右邊**ReceiveNAOrder**模型項目。 在 [ **OffRamp1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**SendRegionalOrders**。  
  
    2.  在  **Extender**下拉式清單中，按一下**出口匝 ESB Extender**。  
  
    3.  在  **BizTalk 應用程式**下拉式清單中，按一下**GlobalBank.ESB**。  
  
    4.  在 **傳送埠**下拉式清單中，按一下**DynamicResolutionOneWay**。  
  
3.  從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendRegionalOrders**模型項目。 在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**SendPortFilter**。  
  
    2.  在 **路線服務的擴充項**下拉式清單中，按一下**出口匝 Extender**。  
  
    3.  在 **出口匝**下拉式清單中，展開**SendRegionalOrders**，然後按一下 **傳送處理常式**。  
  
4.  以滑鼠右鍵按一下**解析**的集合**SendPortFilter**模型項目，然後按一下**加入新的解析程式**。 在 [ **Resolver1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**RouteRegionalOrders**。  
  
    2.  在 **傳輸名稱**下拉式清單中，按一下**BRE**。  
  
    3.  在 **解析程式實作**下拉式清單中，按一下**Bre 解析程式擴充功能**。  
  
    4.  在 **原則**下拉式清單中，按一下**RouteBasedOnCustomerKnownType**。  
  
    5.  在 **辨識訊息格式**下拉式清單中按一下 **，則為 True**。  
  
    6.  在  **UseMsg**下拉式清單中，按一下 **，則為 True**。  
  
        > [!NOTE]
        >  如果您使用 BRE 解析程式擴充功能，從協調流程**recognizeMessageFormat**屬性必須設為**False**。  
  
5.  在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**ReceiveNAOrder**模型項目**SendPortFilter**模型項目。  
  
6.  在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**SendPortFilter**模型項目**SendRegionalOrders**模型項目。  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>若要匯出使用路線測試用戶端使用的模型  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面**CbrKnownType**路線，，然後按一下**匯出模型**。  
  
    > [!NOTE]
    >  在 Visual Studio 中，開啟路線的 XML 版本。  
  
2.  儲存專案的所有成品。  
  
3.  在 Windows 檔案總管中，瀏覽至 C:\HowTos\Itineraries 並注意您的路線 XML (CbrKnownType.xml) 建立。  
  
#### <a name="to-test-the-itinerary-and-business-rules"></a>若要測試的路線和商務規則  
  
1.  開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。  
  
2.  在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後按一下**負載路線**。  
  
3.  在 [**開啟路線檔案**] 對話方塊中，瀏覽至 C:\HowTos\Itineraries。 選取  **CbrKnownType.xml**，然後按一下**開啟**載入路線。  
  
4.  按一下  **確定**清除**路線成功載入**訊息。  
  
5.  在路線測試用戶端中，按一下 [旁的省略符號按鈕 （...）**載入訊息**] 方塊中。  
  
6.  在 [**選取要載入的 XML 文件**] 對話方塊中，瀏覽至 C:\HowTos。 選取  **West.xml**，然後按一下**開啟**載入測試訊息。  
  
7.  按一下 [**送出要求**] 按鈕。 測試完成時，按一下**確定**關閉顯示的確認。  
  
8.  在 Windows 檔案總管中，瀏覽至 C:\HowTos\Out。確認目錄中已寫入 West%MessageID%.xml 訊息。  
  
9. 重複使用 East.xml 訊息的測試程序。  
  
10. 在 Windows 檔案總管中，瀏覽至 C:\HowTos\Out。確認目錄中已寫入 East%MessageID%.xml 訊息。  
  
11. 重複使用 NAOrderDoc.xml 訊息的測試程序。  
  
12. 在 Windows 檔案總管中，瀏覽至 C:\HowTos\Out。確認目錄中已寫入 CustomerUnknown%MessageID%.xml 訊息。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [如何：使用商務規則原則選取路線](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [如何：使用商務規則原則根據訊息內容來動態路由訊息](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [訊息路由模式](../esb-toolkit/message-routing-patterns.md)