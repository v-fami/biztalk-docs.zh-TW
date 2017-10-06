---
title: "如何： 選取 使用商務規則原則路線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f6373a8-d9d6-46c6-95e3-f62dd33c342a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d06bdea233c88fb740c728a414472d01a8fdc34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-select-an-itinerary-using-a-business-rules-policy"></a>如何： 選取 使用商務規則原則路線
## <a name="goal"></a>目標  
 本節示範如何建立可用來選取行程已接收訊息的內容為基礎的商務規則，以及如何設定路線選取器管線元件內泛型路線上手呼叫這些規則。 本章節描述中的訊息會路由傳送方式會不同，客戶所在的區域為基礎的商務案例。  
  
 在此 「 如何 」 主題，您將完成下列步驟：  
  
-   模型西部和美國東部客戶 Global 銀行畫分之行程。  
  
-   建立商務規則原則將用來選取行程處理要求。  
  
-   設定要用來選取適當的行程的商務規則原則路線選取器管線元件。  
  
## <a name="prerequisites"></a>必要條件  
 在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。  
  
## <a name="before-you-begin"></a>開始之前  
 在執行本使用說明主題中稍後的步驟之前，請完成下列工作：  
  
-   建立 GlobalBank 西測試訊息。  
  
-   建立 GlobalBank 東部測試訊息。  
  
 下列程序說明如何執行每一種。  
  
#### <a name="to-create-the-globalbank-west-test-message"></a>若要建立 GlobalBank 西測試訊息  
  
1.  在 Windows 檔案總管，瀏覽至 C:\HowTos。  
  
2.  建立一份 NAOrderDoc.xml，，然後複製 West.xml。  
  
3.  在 [記事本] 開啟 West.xml，並將值**customerName**元素**GlobalBankWest**。  
  
4.  儲存 West.xml 為 utf-8，，然後關閉 [記事本]。  
  
#### <a name="to-create-the-globalbank-east-test-message"></a>若要建立 GlobalBank 東部測試訊息  
  
1.  在 Windows 檔案總管，瀏覽至 C:\HowTos。  
  
2.  建立一份 NAOrderDoc.xml，，然後複製 East.xml。  
  
3.  在 [記事本] 開啟 East.xml，並將值**customerName**元素**GlobalBankEast**。  
  
4.  儲存 East.xml 為 utf-8，，然後關閉 [記事本]。  
  
## <a name="steps"></a>步驟  
  
#### <a name="to-create-a-business-rules-engine-bre-policy-to-select-an-itinerary-using-custom-message-properties"></a>若要建立商務規則引擎 (BRE) 原則，選取 使用自訂訊息屬性路線  
  
1.  按一下**啟動**在工作列上，指向**所有程式**，指向   **[!INCLUDE[prague](../includes/prague-md.md)]** ，然後按一下**商務規則編輯器 」**。  
  
2.  在 [原則總管] 中，以滑鼠右鍵按一下**原則**，然後按一下**新增原則**。 命名原則**ResolveItineraryBasedOnCustomer**。  
  
    > [!NOTE]
    >  此說明主題使用與本主題中所建立的相同商務規則原則和旅[How to： 將交換分割，並將產生的訊息路由至多個檔案的位置使用不同旅](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)。 如果您已經完成該區段，您可以跳至 「 程序，建立並設定 ESB 上手"本主題稍後的。  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-west"></a>若要加入客戶 GlobalBank 西的選取範圍規則  
  
1.  在**ResolveItineraryBasedOnCustomer**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**新增規則**。 命名規則**SetGlobalBankWestItinerary**。  
  
2.  在 事實總管 中，按一下  **XML 結構描述**索引標籤上，以滑鼠右鍵按一下**結構描述**，然後按一下**瀏覽**。  
  
3.  在**結構描述檔案**對話方塊中，瀏覽至 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB。選取 DynamicResolution.Schemas **NAOrderDoc.xsd**，然後按一下**開啟**。  
  
    > [!NOTE]
    >  這是定義用來建立將用於測試的西和東訊息 NAOrderDoc.xml 訊息的結構描述。  
  
4.  在 事實總管 中，按一下  **NAOrderDoc.xsd**，按一下 **文件類型**屬性 屬性 窗格中，然後輸入**GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.  
  
    > [!NOTE]
    >  這是結構描述的完整的名稱。  
  
5.  在 [事實總管] 中，展開**NAOrderDoc.xsd**，然後展開**OrderDoc**。  
  
6.  在 規則 視窗中，以滑鼠右鍵按一下**條件**，指向 **述詞**，然後按一下**等於**。  
  
7.  從 [事實總管] 中，拖曳**customerName**元素**引數 1**節點下的**條件**。  
  
8.  按一下**引數 2**  節點，然後輸入**GlobalBankWest**。  
  
9. 在 [事實總管] 中，按一下 [**詞彙**] 索引標籤。展開**ESB。行程**詞彙中，展開**1.1 版**，然後將拖曳**設定路線名稱**定義，以**動作**。  
  
10. 按一下**\<空字串 >**，然後輸入**GlobalBankWestItinerary**。  
  
    > [!NOTE]
    >  稍後在本使用說明主題中，您會根據 GlobalBank 西這個行程建立來處理訊息。  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-east"></a>加入客戶 GlobalBank 東部選取規則  
  
1.  在 [原則總管] 中，以滑鼠右鍵按一下**SetGlobalBankWestItinerary**規則，，然後按一下**複製**。  
  
2.  以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**貼上**。  
  
3.  在**新規則的名稱** 對話方塊中，輸入**SetGlobalBankEastItinerary**，然後按一下**確定**。  
  
4.  在 原則總管 中，按一下  **SetGlobalBankEastItinerary**規則。  
  
5.  在**條件**區段中，以滑鼠右鍵按一下**GlobalBankWest**，然後按一下**重設引數**。  
  
6.  按一下**引數 2**，然後輸入**GlobalBankEast**。  
  
7.  在**動作**區段中，以滑鼠右鍵按一下**GlobalBankWestItinerary**，然後按一下**重設引數**。  
  
8.  按一下**\<空字串 >** ，然後輸入**GlobalBankEastItinerary**。  
  
    > [!NOTE]
    >  稍後的 「 如何 」 主題中，您將從 GlobalBank 東這個行程建立來處理訊息。  
  
#### <a name="to-publish-and-deploy-the-policy"></a>若要發行和部署原則  
  
1.  在 [原則總管] 中，在**ResolveItineraryBasedOnCustomer**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**發行**。  
  
2.  在 [原則總管] 中，在**ResolveItineraryBasedOnCustomer**原則，以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下**部署**。  
  
#### <a name="to-create-an-esb-itinerary-domain-specific-language-dsl-model-for-globalbank-west-messages"></a>若要建立 GlobalBank 西訊息 ESB 路線網域特定領域語言 (DSL) 模型  
  
1.  在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，開啟 C:\HowTos\Patterns\Patterns.sln。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新的行程**。  
  
3.  在**加入新項目**對話方塊，在 [範本] 窗格中，按一下**ItineraryDsl**。  
  
4.  在**名稱**方塊中，輸入**GlobalBankWestItinerary**，然後按一下**新增**。  
  
#### <a name="to-configure-the-properties-of-the-globalbank-west-itinerary"></a>若要設定 GlobalBank 西路線的屬性  
  
1.  在 Visual Studio 中，按一下設計介面的**GlobalBankWestItinerary.itinerary**。 在**GlobalBankWestItinerary**屬性 視窗中，設定下列屬性：  
  
    1.  在**模型匯出工具**下拉式清單中，按一下 **資料庫路線匯出工具**。  
  
    2.  按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。  
  
    3.  在**連接屬性**對話方塊中，選擇裝載路線的儲存機制資料庫，SQL Server，，然後指定資料庫的名稱 (預設名稱是**EsbItineraryDb**)。  
  
2.  在**路線狀態**下拉式清單中，按一下 **部署**。  
  
    > [!NOTE]
    >  這個步驟可讓您匯出至中央儲存機制; 路線選取並從這個儲存機制，在訊息接收時附加行程。 您稍後將設定路線選取器管線元件使用 「 商務規則引擎解析程式 」 (BRI) 評估內送的訊息，並從這個儲存機制中選取適當的路線。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義路線結構  
  
1.  從 [工具箱] 拖曳**上手**至設計介面的模型項目。 在**OnRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **上手 ESB 服務延伸模組**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。  
  
    4.  在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。  
  
2.  從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**ReceiveNAOrder**模型項目。 在**OffRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendNAOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **匝道 ESB 服務延伸模組**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。  
  
    4.  在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。  
  
3.  從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendNAOrder**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**RouteMessage**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **匝道路線服務延伸模組**。  
  
    3.  在**匝道**下拉式清單中，展開**SendNAOrder**，然後按一下**傳送處理常式**。  
  
4.  以滑鼠右鍵按一下**解析程式**集合**RouteMessage**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**StaticResolver**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**傳輸名稱**下拉式清單中，按一下 **檔案**。  
  
    4.  按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\West%MessageID%.xml**。  
  
5.  在工具箱中，按一下 **連接器**。 拖曳連接**ReceiveNAOrder**模型項目的**RouteMessage**模型項目。  
  
6.  在工具箱中，按一下 **連接器**。 拖曳連接**RouteMessage**模型項目的**SendNAOrder**模型項目。  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a>將模型匯出至路線資料庫  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**GlobalBankWestItinerary**路線，然後再按一下**匯出模型**。  
  
    > [!NOTE]
    >  路線已經匯出成路線的資料庫，現在可供路線選取器元件。  
  
2.  儲存專案的所有成品。  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-east-message"></a>若要建立 GlobalBank 東部訊息 ESB 路線 DSL 模型  
  
1.  在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，開啟 C:\HowTos\Patterns.sln。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新的行程**。  
  
3.  在**加入新項目**對話方塊，在 [範本] 窗格中，按一下**ItineraryDsl**。  
  
4.  在**名稱**方塊中，輸入**GlobalBankEastItinerary**，然後按一下**新增**。  
  
#### <a name="to-configure-the-properties-of-the-globalbank-east-itinerary"></a>若要設定的 GlobalBank 東部路線屬性  
  
1.  在 Visual Studio 中，按一下設計介面的**GlobalBankEastItinerary.itinerary**。 在**GlobalBankEastItinerary**屬性 視窗中，設定下列屬性：  
  
    1.  在**模型匯出工具**下拉式清單中，按一下 **資料庫路線匯出工具**。  
  
    2.  按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。  
  
    3.  在**連接屬性**對話方塊中，選擇裝載路線的儲存機制資料庫，SQL Server，，然後指定資料庫的名稱 (預設名稱是**EsbItineraryDb**)。  
  
2.  在**路線狀態**下拉式清單中，按一下 **部署**。  
  
    > [!NOTE]
    >  這個步驟可讓您匯出至中央儲存機制; 路線可以選取和接收訊息時就會從這個儲存機制附加行程。 您稍後將設定要用於評估內送的訊息，並從這個儲存機制中選取適當的行程 BRI 解析程式路線選取器管線元件。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義路線結構  
  
1.  從 [工具箱] 拖曳**上手**至設計介面的模型項目。 在**OnRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **上手 ESB 服務延伸模組**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。  
  
    4.  在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。  
  
2.  從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**ReceiveNAOrder**模型項目。 在**OffRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendNAOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **匝道 ESB 服務延伸模組**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。  
  
    4.  在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。  
  
3.  從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendNAOrder**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**RouteMessage**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **匝道路線服務延伸模組**。  
  
    3.  在**匝道**下拉式清單中，展開**SendNAOrder**，然後按一下**傳送處理常式**。  
  
4.  以滑鼠右鍵按一下**解析程式**集合**RouteMessage**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**StaticResolver**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**傳輸名稱**下拉式清單中，按一下 **檔案**。  
  
    4.  按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\East%MessageID%.xml**。  
  
5.  在工具箱中，按一下 **連接器**。 拖曳連接**ReceiveNAOrder**模型項目的**RouteMessage**模型項目。  
  
6.  在工具箱中，按一下 **連接器**。 拖曳連接**RouteMessage**模型項目的**SendNAOrder**模型項目。  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a>將模型匯出至路線資料庫  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**GlobalBankEastItinerary**路線，然後再按一下**匯出模型**。  
  
    > [!NOTE]
    >  路線已經匯出成路線的資料庫，現在可供路線選取器元件。  
  
2.  儲存專案的所有成品。  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a>若要建立及設定 ESB 上手  
  
1.  按一下**啟動**在工作列上，指向**所有程式**，指向   **[!INCLUDE[prague](../includes/prague-md.md)]** ，然後按一下 **BizTalk Server 管理**.  
  
2.  在[!INCLUDE[prague](../includes/prague-md.md)]管理主控台中，展開  **BizTalk 群組**，依序展開**應用程式**，然後展開**Microsoft.Practices.ESB**。  
  
3.  以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下**單向接收位置**。  
  
4.  在**選取接收埠**對話方塊中，按一下  **OnRamp.Itinerary**，然後按一下**確定**。  
  
5.  在**接收位置屬性**對話方塊中，於**名稱**方塊中，輸入**OnRamp.Itinerary.HowTo**。  
  
6.  在**類型**下拉式清單中，按一下 **檔案**，然後按一下**設定**。  
  
7.  中**FILE 傳輸屬性**對話方塊中，於**接收資料夾**方塊中，輸入**C:\HowTos\DropFolder**，然後按一下**確定**。  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a>若要設定路線選取器管線元件  
  
1.  在**接收位置屬性**對話方塊中，於**接收管線**下拉式清單中，按一下  **ItinerarySelectReceiveXml**，然後按一下省略符號按鈕 （...).  
  
2.  使用**設定管線**對話方塊來設定下列**路線選取器**元件屬性：  
  
    1.  按一下**ItineraryFactKey**屬性，，然後輸入**Resolver.Itinerary**。  
  
    2.  按一下**ResolverConnectionString**屬性，，然後輸入**BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**  
  
    3.  按一下**確定**關閉**設定管線** 對話方塊。  
  
3.  按一下**確定**關閉**接收位置屬性** 對話方塊。  
  
4.  在[!INCLUDE[prague](../includes/prague-md.md)]管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**啟用**。  
  
#### <a name="to-test-the-itinerary-selector-and-business-rules"></a>若要測試的計劃的選取器 」 和 「 商務規則  
  
1.  在 Windows 檔案總管，瀏覽至 C:\HowTos。  
  
2.  複製 （不會移動） 到 DropFolder 資料夾 East.xml 和 West.xml 檔案。  
  
3.  瀏覽至 C:\HowTos\Out。請確認 East%MessageID%.xml 和 West%MessageID%.xml 訊息已寫入目錄。  
  
    > [!NOTE]
    >  除了客戶元素的值相同，但使用不同的行程，根據路線選取器管線元件的解析度處理訊息。  
  
4.  在[!INCLUDE[prague](../includes/prague-md.md)]管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**停用**。  
  
5.  之後**OnRamp.Itinerary.HowTo**接收位置已停用，以滑鼠右鍵按一下，，然後按一下**刪除**。 在**確認刪除接收位置**對話方塊中，按一下 **是**。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [如何： 將交換分割，並將產生的訊息路由至多個使用不同的行程的檔案位置](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [安裝及執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)  
  
-   [訊息的路由模式](../esb-toolkit/message-routing-patterns.md)