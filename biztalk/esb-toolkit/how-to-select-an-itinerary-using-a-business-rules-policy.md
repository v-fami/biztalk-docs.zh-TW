---
title: 如何： 選取使用商務規則原則路線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9f6373a8-d9d6-46c6-95e3-f62dd33c342a
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12496da0de4057e96be0b714ad1af048ee6b8ef1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976959"
---
# <a name="how-to-select-an-itinerary-using-a-business-rules-policy"></a>如何： 選取使用商務規則原則路線
## <a name="goal"></a>目標  
 本節示範如何建立可用來選取路線接收訊息的內容為基礎的商務規則，以及如何設定路線選取器管線元件中泛型路線入口匝呼叫這些規則。 本章節描述在其中訊息會路由傳送以不同的方式，客戶所在的區域為基礎的商務案例。  
  
 在本使用說明主題中，您將完成下列步驟：  
  
-   模型的客戶 Global Bank 西部和美國東部部門的路線。  
  
-   建立將用來選取路線處理要求的商務規則原則。  
  
-   設定路線選取器管線元件使用商務規則原則選取適當的路線。  
  
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
  
#### <a name="to-create-a-business-rules-engine-bre-policy-to-select-an-itinerary-using-custom-message-properties"></a>若要建立商務規則引擎 (BRE) 原則，以選取路線，使用自訂訊息屬性  
  
1.  按一下 **開始**在工作列上，指向**所有程式**，指向**BizTalk Server**，然後按一下**商務規則編輯器 」**。  
  
2.  在 [原則總管] 中，以滑鼠右鍵按一下**原則**，然後按一下**新增新的原則**。 命名原則**ResolveItineraryBasedOnCustomer**。  
  
    > [!NOTE]
    >  本使用說明主題使用與本主題中所建立的相同商務規則原則和路線[如何： 分割交換，並將產生的訊息路由至多個檔案的位置使用不同路線](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)。 如果您已經完成該區段，您可以跳至 」 來建立和設定 ESB 匝道 」 的程序，稍後在本主題中。  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-west"></a>若要新增客戶 GlobalBank 西部的選取項目規則  
  
1.  在  **ResolveItineraryBasedOnCustomer**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **新增規則**。 命名規則**SetGlobalBankWestItinerary**。  
  
2.  在 [事實總管] 中，按一下**XML 結構描述**索引標籤上，以滑鼠右鍵按一下**結構描述**，然後按一下**瀏覽**。  
  
3.  在 [**結構描述檔案**] 對話方塊中，瀏覽至 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB。選取 DynamicResolution.Schemas **NAOrderDoc.xsd**，然後按一下**開啟**。  
  
    > [!NOTE]
    >  這是定義 NAOrderDoc.xml 訊息，這用來建立您將用來測試西和東訊息的結構描述。  
  
4.  在 [事實總管] 中，按一下**NAOrderDoc.xsd**，按一下**文件類型**屬性，在 [屬性] 窗格中，然後按**GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.  
  
    > [!NOTE]
    >  這是結構描述的完整的名稱。  
  
5.  在 [事實總管] 中，展開**NAOrderDoc.xsd**，然後展開**OrderDoc**。  
  
6.  在 [規則] 視窗中，以滑鼠右鍵按一下**條件**，指向**述詞**，然後按一下**等於**。  
  
7.  從 [事實總管] 中，拖曳**customerName**項目**引數 1**節點底下**條件**。  
  
8.  按一下  **argument2**節點，然後按**GlobalBankWest**。  
  
9. 在 事實總管 中，按一下**詞彙** 索引標籤。展開**ESB。路線**詞彙，依序展開**1.1 版**，然後將拖曳**設定路線名稱**定義**動作**。  
  
10. 按一下  **\<空字串\>**，然後輸入**GlobalBankWestItinerary**。  
  
    > [!NOTE]
    >  稍後在本使用說明主題中，您將建立此行程來處理訊息從 GlobalBank 西部。  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-east"></a>將選取的規則適用於客戶 GlobalBank 東部  
  
1.  在 [原則總管] 中，以滑鼠右鍵按一下**SetGlobalBankWestItinerary**規則，然後按一下**複製**。  
  
2.  以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**貼上**。  
  
3.  在**新的規則名稱**] 對話方塊中，輸入**SetGlobalBankEastItinerary**，然後按一下 [**確定**。  
  
4.  在 [原則總管] 中，按一下**SetGlobalBankEastItinerary**規則。  
  
5.  在 **條件**區段中，以滑鼠右鍵按一下**GlobalBankWest**，然後按一下**重設引數**。  
  
6.  按一下  **argument2**，然後輸入**GlobalBankEast**。  
  
7.  在 **動作**區段中，以滑鼠右鍵按一下**GlobalBankWestItinerary**，然後按一下**重設引數**。  
  
8.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo\<接收位置，然後按一下\>停用**。  
  
    > [!NOTE]
    >  在後OnRamp.Itinerary.HowTo接收位置已停用，以滑鼠右鍵按一下，然後按一下 刪除。  
  
#### <a name="to-publish-and-deploy-the-policy"></a>發佈和部署原則  
  
1.  在 [**確認刪除接收位置**] 對話方塊中，按一下**是**。  
  
2.  在 [原則總管] 中，在**ResolveItineraryBasedOnCustomer**原則，以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下**部署**。  
  
#### <a name="to-create-an-esb-itinerary-domain-specific-language-dsl-model-for-globalbank-west-messages"></a>若要建立 GlobalBank 西部訊息 ESB 路線的特定領域語言 (DSL) 模型  
  
1.  在 Visual Studio 中，開啟 [C:\HowTos\Patterns\Patterns.sln]。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新路線**。  
  
3.  在 **加入新項目**對話方塊，在 範本 窗格中，按一下**ItineraryDsl**。  
  
4.  在 **名稱**方塊中，輸入**GlobalBankWestItinerary**，然後按一下**新增**。  
  
#### <a name="to-configure-the-properties-of-the-globalbank-west-itinerary"></a>若要設定 GlobalBank 西部路線的屬性  
  
1.  在 Visual Studio 中，按一下設計介面**GlobalBankWestItinerary.itinerary**。 在 [ **GlobalBankWestItinerary**屬性] 視窗中，設定下列屬性：  
  
    1.  在 **模型匯出工具**下拉式清單中，按一下**資料庫路線匯出工具**。  
  
    2.  按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。  
  
    3.  在 **連接屬性** 對話方塊中，選擇裝載路線的存放庫資料庫中，SQL Server，然後指定 資料庫名稱 (預設名稱是**EsbItineraryDb**)。  
  
2.  在 **路線狀態**下拉式清單中，按一下**部署**。  
  
    > [!NOTE]
    >  此步驟可讓您匯出至中央儲存機制; 的路線可以選取路線，並將它附加在訊息接收時從此存放庫中。 您稍後將會設定路線選取器管線元件，用以評估內送的訊息，並選取適當的路線，從這個儲存機制中的商務規則引擎解析程式 (BRI)。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義的路線結構  
  
1.  從 [工具箱] 拖曳**匝道**模型項目到設計介面。 在 [ **OnRamp1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**ReceiveNAOrder**。  
  
    2.  在  **Extender**下拉式清單中，按一下**匝道 ESB 服務延伸模組**。  
  
    3.  在  **BizTalk 應用程式**下拉式清單中，按一下**Microsoft.Practices.ESB**。  
  
    4.  在 **接收埠**下拉式清單中，按一下**OnRamp.Itinerary**。  
  
2.  從 [工具箱] 拖曳**出口匝**模型項目到設計介面，並再將其放置在右邊**ReceiveNAOrder**模型項目。 在 [ **OffRamp1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**SendNAOrder**。  
  
    2.  在  **Extender**下拉式清單中，按一下**出口匝 ESB 服務延伸模組**。  
  
    3.  在  **BizTalk 應用程式**下拉式清單中，按一下**GlobalBank.ESB**。  
  
    4.  在 **傳送埠**下拉式清單中，按一下**DynamicResolutionOneWay**。  
  
3.  從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendNAOrder**模型項目。 在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**RouteMessage**。  
  
    2.  在 **路線服務的擴充項**下拉式清單中，按一下**出口匝路線服務延伸模組**。  
  
    3.  在 **出口匝**下拉式清單中，展開**SendNAOrder**，然後按一下 **傳送處理常式**。  
  
4.  以滑鼠右鍵按一下**解析**的集合**RouteMessage**模型項目，然後按一下**加入新的解析程式**。 在 [ **Resolver1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**StaticResolver**。  
  
    2.  在 **解析程式實作**下拉式清單中，按一下**靜態的解析程式擴充**。  
  
    3.  在 **傳輸名稱**下拉式清單中，按一下**檔案**。  
  
    4.  按一下 **傳輸位置**屬性，然後按**C:\HowTos\Out\West%MessageID%.xml**。  
  
5.  在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**ReceiveNAOrder**模型項目**RouteMessage**模型項目。  
  
6.  在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**RouteMessage**模型項目**SendNAOrder**模型項目。  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a>將模型匯出至路線資料庫  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面**GlobalBankWestItinerary**路線，，然後按一下**匯出模型**。  
  
    > [!NOTE]
    >  路線已匯出至路線資料庫，並可立即供路線選取器元件。  
  
2.  儲存專案的所有成品。  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-east-message"></a>若要建立 GlobalBank 東部訊息 ESB 路線 DSL 模型  
  
1.  在 Visual Studio 中，開啟 [C:\HowTos\Patterns.sln]。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新路線**。  
  
3.  在 **加入新項目**對話方塊，在 範本 窗格中，按一下**ItineraryDsl**。  
  
4.  在 **名稱**方塊中，輸入**GlobalBankEastItinerary**，然後按一下**新增**。  
  
#### <a name="to-configure-the-properties-of-the-globalbank-east-itinerary"></a>若要設定 GlobalBank 東部路線的屬性  
  
1.  在 Visual Studio 中，按一下設計介面**GlobalBankEastItinerary.itinerary**。 在 [ **GlobalBankEastItinerary**屬性] 視窗中，設定下列屬性：  
  
    1.  在 **模型匯出工具**下拉式清單中，按一下**資料庫路線匯出工具**。  
  
    2.  按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。  
  
    3.  在 **連接屬性** 對話方塊中，選擇裝載路線的存放庫資料庫中，SQL Server，然後指定 資料庫名稱 (預設名稱是**EsbItineraryDb**)。  
  
2.  在 **路線狀態**下拉式清單中，按一下**部署**。  
  
    > [!NOTE]
    >  此步驟可讓您匯出至中央儲存機制; 的路線可以選取路線，並將其接收訊息時，從這個儲存機制連接。 您稍後將會設定路線選取器管線元件，用以評估內送的訊息，並選取適當的路線，從這個儲存機制的 BRI 解析程式。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義的路線結構  
  
1.  從 [工具箱] 拖曳**匝道**模型項目到設計介面。 在 [ **OnRamp1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**ReceiveNAOrder**。  
  
    2.  在  **Extender**下拉式清單中，按一下**匝道 ESB 服務延伸模組**。  
  
    3.  在  **BizTalk 應用程式**下拉式清單中，按一下**Microsoft.Practices.ESB**。  
  
    4.  在 **接收埠**下拉式清單中，按一下**OnRamp.Itinerary**。  
  
2.  從 [工具箱] 拖曳**出口匝**模型項目到設計介面，並再將其放置在右邊**ReceiveNAOrder**模型項目。 在 [ **OffRamp1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**SendNAOrder**。  
  
    2.  在  **Extender**下拉式清單中，按一下**出口匝 ESB 服務延伸模組**。  
  
    3.  在  **BizTalk 應用程式**下拉式清單中，按一下**GlobalBank.ESB**。  
  
    4.  在 **傳送埠**下拉式清單中，按一下**DynamicResolutionOneWay**。  
  
3.  從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendNAOrder**模型項目。 在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**RouteMessage**。  
  
    2.  在 **路線服務的擴充項**下拉式清單中，按一下**出口匝路線服務延伸模組**。  
  
    3.  在 **出口匝**下拉式清單中，展開**SendNAOrder**，然後按一下 **傳送處理常式**。  
  
4.  以滑鼠右鍵按一下**解析**的集合**RouteMessage**模型項目，然後按一下**加入新的解析程式**。 在 [ **Resolver1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**StaticResolver**。  
  
    2.  在 **解析程式實作**下拉式清單中，按一下**靜態的解析程式擴充**。  
  
    3.  在 **傳輸名稱**下拉式清單中，按一下**檔案**。  
  
    4.  按一下 **傳輸位置**屬性，然後按**C:\HowTos\Out\East%MessageID%.xml**。  
  
5.  在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**ReceiveNAOrder**模型項目**RouteMessage**模型項目。  
  
6.  在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**RouteMessage**模型項目**SendNAOrder**模型項目。  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a>將模型匯出至路線資料庫  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面**GlobalBankEastItinerary**路線，，然後按一下**匯出模型**。  
  
    > [!NOTE]
    >  路線已匯出至路線資料庫，並可立即供路線選取器元件。  
  
2.  儲存專案的所有成品。  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a>建立和設定 ESB 匝道  
  
1.  按一下 **開始**在工作列上，指向**所有程式**，指向**BizTalk Server**，然後按一下**BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，展開**應用程式**，然後展開**Microsoft.Practices.ESB**。  
  
3.  以滑鼠右鍵按一下**接收位置**，指向**新增**，然後按一下**單向接收位置**。  
  
4.  在 [**選取接收埠**] 對話方塊中，按一下**OnRamp.Itinerary**，然後按一下 **[確定]**。  
  
5.  在 **接收位置屬性**對話方塊中，於**名稱**方塊中，輸入**OnRamp.Itinerary.HowTo**。  
  
6.  在 **型別**下拉式清單中，按一下**檔案**，然後按一下 **設定**。  
  
7.  中**FILE 傳輸屬性**對話方塊中，於**接收資料夾**方塊中，輸入**C:\HowTos\DropFolder**，然後按一下**確定**。  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a>若要設定路線選取器管線元件  
  
1.  在 **接收位置屬性**對話方塊的 **接收管線**下拉式清單中，按一下**ItinerarySelectReceiveXml**，然後按一下省略符號按鈕 （...).  
  
2.  使用**設定管線**對話方塊，即可設定下列各項**路線選取器**元件屬性：  
  
    1.  按一下  **ItineraryFactKey**屬性，然後按**Resolver.Itinerary**。  
  
    2.  按一下  **ResolverConnectionString**屬性，然後按**BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**  
  
    3.  按一下 [ **[確定]** 以關閉**設定管線**] 對話方塊。  
  
3.  按一下 [ **[確定]** 以關閉**接收位置屬性**] 對話方塊。  
  
4.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**啟用**。  
  
#### <a name="to-test-the-itinerary-selector-and-business-rules"></a>若要測試的路線選取器 」 和 「 商務規則  
  
1.  在 Windows 檔案總管中，瀏覽至 C:\HowTos。  
  
2.  複製 （不會移動） 到 DropFolder 資料夾 East.xml 和 West.xml 檔案。  
  
3.  瀏覽至 C:\HowTos\Out。請確認 East%MessageID%.xml 和 West%MessageID%.xml 訊息已寫入該目錄。  
  
    > [!NOTE]
    >  除了客戶元素的值相同，但使用不同路線，根據路線選取器管線元件的解析度處理訊息。  
  
4.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**停用**。  
  
5.  在後**OnRamp.Itinerary.HowTo**接收位置已停用，以滑鼠右鍵按一下，然後按一下 **刪除**。 在 [**確認刪除接收位置**] 對話方塊中，按一下**是**。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [如何：分割交換，並使用不同路線將產生的訊息路由至多個檔案位置](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [安裝和執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)  
  
-   [訊息路由模式](../esb-toolkit/message-routing-patterns.md)