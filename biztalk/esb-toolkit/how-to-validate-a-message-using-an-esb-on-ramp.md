---
title: 如何： 驗證訊息，使用 ESB 上手 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43dfc791-7cb6-45a4-898f-f53def199c08
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e14fd3f433609da7748197a8b67112d815da153
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009519"
---
# <a name="how-to-validate-a-message-using-an-esb-on-ramp"></a>如何： 驗證訊息，使用 ESB 上手
## <a name="goal"></a>目標  
 本節示範如何設定 ESB 發送器解譯管線元件來執行訊息驗證的 XML 訊息提交給 ESB 上手。  
  
 在此 「 如何 」 主題，您將完成下列步驟：  
  
-   建立 ESB 上手使用**ItinerarySelectReceiveXml**管線。  
  
-   設定 ESB 發送器解譯管線元件以驗證訊息內容。  
  
-   若要解決適當路線路線選取器管線元件設定。  
  
-   測試訊息驗證使用有效的訊息和一個無效的訊息。  
  
## <a name="prerequisites"></a>必要條件  
 在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。  
  
## <a name="before-you-begin"></a>開始之前  
 在執行本使用說明主題中稍後的步驟之前，請完成下列工作：  
  
-   建立無效的測試訊息。  
  
-   建立 ESB 路線網域特定領域語言 (DSL) 模型。  
  
-   設定屬性的路線。  
  
-   定義結構的路線。  
  
-   將模型匯出至路線資料庫。  
  
 下列程序說明如何執行每一種。  
  
#### <a name="to-create-an-invalid-test-message"></a>若要建立無效的測試訊息  
  
1.  在 Windows 檔案總管，瀏覽至 C:\HowTos。  
  
2.  建立一份 NAOrderDoc.xml，，然後重新命名複製 Invalid.xml。  
  
3.  在 [記事本] 開啟 Invalid.xml。  
  
4.  變更 **\<ns0:requestType\>10\</ns0:requestType\>至\<ns0:requestType\>十個\</ns0:requestType\>** .  
  
5.  儲存 Invalid.xml 為 utf-8，，然後關閉 [記事本]。  
  
    > [!NOTE]
    >  藉由變更這個項目的數值成文字，訊息將不再有效根據結構描述。  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a>若要建立 ESB 路線 DSL 模型  
  
1.  在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。  
  
2.  在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**，指向 **新增**，然後按一下 **新的行程**。  
  
3.  在**加入新項目** 對話方塊中，輸入**驗證**中**名稱**方塊，然後再按一下**新增**。  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>若要設定的路線屬性  
  
1.  在 Visual Studio 中，按一下設計介面的**Validation.itinerary**。 在**驗證**屬性 視窗中，設定下列屬性：  
  
    1.  在**模型匯出工具**下拉式清單中，按一下 **資料庫路線匯出工具**。  
  
    2.  按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。  
  
    3.  在**連接屬性**對話方塊中，選擇裝載路線的儲存機制資料庫，SQL Server，，然後指定資料庫的名稱 (預設名稱是**EsbItineraryDb**)。  
  
2.  在**路線狀態**下拉式清單中，按一下 **部署**。  
  
    > [!NOTE]
    >  這個步驟可讓您匯出至中央儲存機制; 路線可以選取和接收訊息時就會從這個儲存機制附加行程。 您稍後將設定路線選取器管線元件從這個儲存機制中選取適當的行程中使用靜態的解析程式。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義路線結構  
  
1.  從 [工具箱] 拖曳**上手**至設計介面的模型項目。 在**OnRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **上手 ESB Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。  
  
    4.  在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。  
  
2.  從 [工具箱] 拖曳**匝道**模型項目至設計介面，並將其放置到現有的模型項目的右。 在**OffRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendNAOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。  
  
    4.  在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。  
  
3.  從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendNAOrder**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendPortFilter**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。  
  
    3.  在**匝道**下拉式清單中，展開**SendNAOrder**，然後按一下 **傳送處理常式**。  
  
4.  以滑鼠右鍵按一下**解析程式**集合**SendPortFilter**項目，然後再按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ConfigureOffRamp**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**傳輸名稱**下拉式清單中，按一下 **檔案**。  
  
    4.  按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\Validated%MessageID%.xml**。  
  
5.  在工具箱中，按一下 **連接器**。 拖曳連接**ReceiveNAOrder**模型項目的**SendPortFilter**模型項目。  
  
6.  在工具箱中，按一下 **連接器**。 拖曳連接**SendPortFilter**模型項目的**SendNAOrder**模型項目。  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a>將模型匯出至路線資料庫  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**驗證**路線，然後再按一下**匯出模型**。  
  
    > [!NOTE]
    >  路線已經匯出成路線的資料庫，現在可供路線選取器管線元件。  
  
2.  儲存專案的所有成品。  
  
## <a name="steps"></a>步驟  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a>若要建立及設定 ESB 上手  
  
1.  按一下**啟動**在工作列上，指向**所有程式**，指向  **BizTalk Server**，然後按一下  **BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，依序展開**應用程式**，然後展開**Microsoft.Practices.ESB**。  
  
3.  以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**。  
  
4.  在**選取接收埠**對話方塊中，按一下  **OnRamp.Itinerary**，然後按一下 **確定**。  
  
5.  在**接收位置屬性** 對話方塊中，輸入**OnRamp.Itinerary.HowTo**中**名稱**方塊。  
  
6.  在**類型**下拉式清單中，按一下 **檔案**，然後按一下 **設定**。  
  
7.  在**FILE 傳輸屬性** 對話方塊中，輸入**C:\HowTos\DropFolder**中**接收資料夾**方塊，然後再按一下**確定**。  
  
#### <a name="to-configure-the-on-ramp-to-perform-message-validation"></a>若要設定上手執行訊息驗證  
  
1.  在**接收位置屬性**對話方塊中，於**接收管線**下拉式清單中，按一下  **ItinerarySelectReceiveXml**，然後按一下省略符號按鈕 （...).  
  
2.  使用**設定管線**對話方塊來設定下列**XML 解譯器**元件屬性：  
  
    1.  展開 GlobalBank.Esb 應用程式，然後按一下**結構描述**。 以滑鼠右鍵按一下**GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**，然後按一下 **屬性**。 複製**名稱**和**組件**屬性並將它們貼至文字檔案。  
  
    2.  在**解譯**元件，請按一下**True**中**ValidateDocument**下拉式清單。  
  
    3.  按一下**DocumentSpecNames**屬性，然後輸入完整名稱的結構描述。 名稱為開頭的完整限定的名稱，且後面逗號和擷取步驟中的組件資訊。 以下是一個範例：  
  
         GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc，GlobalBank.ESB.DynamicResolution.Schemas，版本 = 2.0.0.0，Culture = neutral，PublicKeyToken = c2c8b2b87f54180a  
  
        > [!NOTE]
        >  這是要驗證之結構描述的完整格式的名稱它包含的結構描述名稱和四個組件屬性： 組件名稱、 版本、 文化特性和公開金鑰語彙基元。 允許多個值。使用管道 (&#124;) 分隔多個結構描述的符號。  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a>若要設定路線選取器管線元件  
  
1.  在**設定管線**對話方塊方塊中，設定下列各項**路線選取器**元件屬性：  
  
    1.  按一下**ItineraryFactKey**屬性，，然後輸入**Resolver.Itinerary**。  
  
    2.  按一下**ResolverConnectionString**屬性，，然後輸入**路線：\\\name=Validation;**。  
  
    3.  按一下**確定**關閉**設定管線** 對話方塊。  
  
2.  按一下**確定**關閉**接收位置屬性** 對話方塊。  
  
3.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**啟用**。  
  
#### <a name="to-test-the-message-validation-and-itinerary-selection"></a>若要測試訊息驗證和行程選取項目  
  
1.  在 Windows 檔案總管，瀏覽至 C:\HowTos。  
  
2.  複製 （不會移動） NAOrderDoc.xml DropFolder 資料夾。  
  
3.  瀏覽至 C:\HowTos\Out。請確認 Validated%MessageID%.xml 已寫入至目錄。  
  
    > [!NOTE]
    >  有效的訊息其行程為基礎的路由，依照預期方式完成。  
  
4.  Validated%MessageID%.xml 刪除 Out 資料夾中。  
  
5.  在 Windows 檔案總管，瀏覽至 C:\HowTos。  
  
6.  複製 （不會移動） Invalid.xml DropFolder 資料夾。  
  
7.  瀏覽至 C:\HowTos\Out。請確認已傳送任何新訊息。  
  
    > [!NOTE]
    >  無法驗證訊息。因此，行程為基礎的路由無法完成。  
  
8.  按一下**啟動**在工作列上，指向**系統管理工具**，然後按一下 **事件檢視器**。  
  
9. 在 事件檢視器中，展開**Windows 記錄檔**，然後按一下 **應用程式**。  
  
10. 找出最近的事件位置**來源**是**BizTalk Server**，而**事件識別碼**是**5719**。  
  
    > [!NOTE]
    >  提交和失敗的無效訊息應用程式事件記錄檔產生的例外狀況的項目。  
  
11. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**停用**。  
  
12. 之後**OnRamp.Itinerary.HowTo**接收位置已停用，以滑鼠右鍵按一下，，然後按一下**刪除**。 在**確認刪除接收位置**對話方塊中，按一下 **是**。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [如何：使用商務規則原則選取路線](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [安裝和執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)