---
title: 如何： 將交換分割，並將產生的訊息路由至多個檔案位置使用不同的行程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccd46bee-e4a1-4846-8bde-b0460bda1e72
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 538432f548b1403fd9c0cd566b82eb8cb113f737
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010751"
---
# <a name="how-to-split-an-interchange-and-route-the-resulting-messages-to-multiple-file-locations-using-distinct-itineraries"></a>如何： 將交換分割，並將產生的訊息路由至多個使用不同的行程的檔案位置
## <a name="goal"></a>目標  
 本節示範如何建立 ESB 上手使用**ItinerarySelectReceiveXml**略過的管線，以及如何設定管線元件來分割輸入的交換和選取適當的路由每個產生的訊息，根據訊息內容。 會使用商務規則原則，解析路線的選取項目，訊息會路由傳送不同客戶的所在的區域為基礎。  
  
 在此 「 如何 」 主題，您將完成下列步驟：  
  
-   建立 ESB 上手分割 XML 交換。  
  
-   設定要用來選取適當的行程的商務規則原則路線選取器管線元件。  
  
## <a name="prerequisites"></a>必要條件  
 在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。  
  
## <a name="before-you-begin"></a>開始之前  
 在執行本使用說明主題中稍後的步驟之前，請完成下列工作：  
  
-   建立必要的成品。  
  
-   將結構描述專案加入至模式的方案。  
  
-   將成品新增至結構描述專案。  
  
-   建立 BRE 原則，選取 使用自訂訊息屬性的路線。  
  
-   加入客戶 GlobalBank 西選取範圍規則。  
  
-   加入客戶 GlobalBank 東部的選取範圍規則。  
  
-   發佈和部署原則。  
  
-   建立 GlobalBank 西訊息 ESB 路線網域特定領域語言 (DSL) 模型。  
  
-   設定 GlobalBank 西路線的屬性。  
  
-   定義 GlobalBank 西路線的結構。  
  
-   GlobalBank 西模型匯出到路線的資料庫。  
  
-   建立 GlobalBank 東部訊息的 ESB 路線 DSL 模型。  
  
-   設定 GlobalBank 東部路線的屬性。  
  
-   定義 GlobalBank 東部路線的結構。  
  
-   GlobalBank 東部模型匯出到路線的資料庫。  
  
     下列程序說明如何執行每一種。  
  
#### <a name="to-create-the-required-artifacts"></a>若要建立必要的成品  
  
1.  在 Windows 檔案總管，瀏覽至 C:\HowTos。  
  
2.  建立名為 OrderDocEnvelope.xsd 新文字文件。  
  
3.  在記事本中開啟 OrderDocEnvelope.xsd 結構描述。  
  
4.  編輯文件使用下列程式碼。  
  
    ```  
    <?xml version="1.0" ?>  
    <xs:schema xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://ESB.BizUnit.Map.Test" targetNamespace="http://ESB.BizUnit.Map.Test" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
      <xs:import schemaLocation="GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc" namespace="http://globalbank.esb.dynamicresolution.com/northamericanservices/" />  
      <xs:annotation>  
        <xs:appinfo>  
          <b:schemaInfo is_envelope="yes" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" />  
          <b:references>  
            <b:reference targetNamespace="http://globalbank.esb.dynamicresolution.com/northamericanservices/" />  
          </b:references>  
        </xs:appinfo>  
      </xs:annotation>  
      <xs:element name="OrderEnvelope">  
        <xs:annotation>  
          <xs:appinfo>  
            <b:recordInfo body_xpath="/*[local-name()='OrderEnvelope' and namespace-uri()='http://ESB.BizUnit.Map.Test']" />  
          </xs:appinfo>  
        </xs:annotation>  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element ref="ns0:OrderDoc" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
5.  儲存 OrderDocEnvelope.xsd 為 utf-8，，然後關閉 [記事本]。  
  
6.  在 [C:\HowTos] 資料夾中，建立名為 Batch.xml 新文字文件。  
  
7.  在 [記事本] 開啟 Batch.xml。  
  
8.  編輯文件使用下列程式碼。  
  
    ```  
    <?xml version="1.0" ?>  
    <ns0:OrderEnvelope xmlns:ns0="http://ESB.BizUnit.Map.Test">  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankWest</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>10</ns0:requestType>  
      </ns0:OrderDoc>  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankEast</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>11</ns0:requestType>  
      </ns0:OrderDoc>  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankEast</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>12</ns0:requestType>  
      </ns0:OrderDoc>  
    </ns0:OrderEnvelope>  
    ```  
  
9. 儲存並關閉 Batch.xml。  
  
#### <a name="to-add-a-schemas-project-to-the-patterns-solution"></a>將結構描述專案加入至模式的方案  
  
1.  在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。  
  
2.  在 方案總管 中，以滑鼠右鍵按一下**方案 '模式'**，指向 **新增**，然後按一下 **新專案**。  
  
3.  在**加入新的專案**對話方塊，在 [專案類型] 窗格中，按一下**BizTalk 專案**，然後執行下列步驟：  
  
    1.  在 [範本] 窗格中，按一下**空白 BizTalk Server 專案**。  
  
    2.  在**名稱**方塊中，輸入**Patterns.Schemas**，然後按一下 **確定**。  
  
4.  在 方案總管 中，以滑鼠右鍵按一下**Patterns.Schemas**，然後按一下 **屬性**。  
  
5.  在 [屬性] 視窗上**簽署**索引標籤上，選取**簽署組件**核取方塊。  
  
6.  在**選擇強式名稱金鑰檔**下拉式清單中，按一下  **\<新增...\>**.  
  
7.  在**建立強式名稱金鑰**對話方塊方塊中，設定下列屬性：  
  
    1.  在**金鑰檔名稱**方塊中，輸入**分割**。  
  
    2.  清除**保護我的密碼金鑰檔**核取方塊，然後**確定**。  
  
8.  在 [屬性] 視窗上**部署**索引標籤的**應用程式名稱**方塊中，輸入**Microsoft.Practices.ESB**。  
  
9. 關閉 [屬性] 視窗。  
  
#### <a name="to-add-the-artifacts-to-the-schemas-project"></a>若要將成品新增至結構描述專案  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**Patterns.Schemas**，然後按一下 **加入參考**。  
  
2.  在**瀏覽** 索引標籤**加入參考**對話方塊中，瀏覽並選取 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB。DynamicResolution.Schemas\bin\Debug\GlobalBank.ESB.DynamicResolution.Schemas.dll，然後再按一下**確定**。  
  
3.  在 方案總管 中，以滑鼠右鍵按一下**Patterns.Schemas**，指向 **新增**，然後按一下 **現有項目**。  
  
4.  在**加入現有項目**對話方塊中，瀏覽至並選取 C:\HowTos\OrderDocEnvelope.xsd，，然後按一下**新增**。  
  
5.  儲存方案的所有成品。  
  
6.  在 方案總管 中，以滑鼠右鍵按一下**Patterns.Schemas**，然後按一下 **部署**。  
  
    > [!NOTE]
    >  此說明主題使用與中所建立的相同商務規則原則和旅[如何： 選取 使用商務規則原則路線](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)主題。 如果您尚未完成該區段，請完成下列額外的步驟。 如果您已經完成該區段，繼續 < 步驟 > 一節。  
  
#### <a name="to-create-a-business-rules-engine-bre-policy-to-select-an-itinerary-using-custom-message-properties"></a>若要建立商務規則引擎 (BRE) 原則，選取 使用自訂訊息屬性路線  
  
1.  按一下**啟動**在工作列上，指向**所有程式**，指向  **BizTalk Server**，然後按一下 **商務規則編輯器 」**。  
  
2.  在 原則總管 中，以滑鼠右鍵按一下**原則**，然後按一下 **新增原則**。 命名原則**ResolveItineraryBasedOnCustomer**。  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-west"></a>若要加入客戶 GlobalBank 西的選取範圍規則  
  
1.  在**ResolveItineraryBasedOnCustomer**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **新增規則**。 命名規則**SetGlobalBankWestItinerary**。  
  
2.  在 事實總管 中，按一下  **XML 結構描述**索引標籤上，以滑鼠右鍵按一下**結構描述**，然後按一下 **瀏覽**。  
  
3.  在**結構描述檔案**對話方塊中，瀏覽至 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB。DynamicResolution.Schemas，選取 NAOrderDoc.xsd，，然後按一下**開啟**。  
  
    > [!NOTE]
    >  這是定義用來建立將用於測試的西和東訊息 NAOrderDoc.xml 訊息的結構描述。  
  
4.  在 事實總管 中，按一下 NAOrderDoc.xsd 中，按一下**文件類型**屬性 屬性 窗格中，然後輸入**GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**。  
  
    > [!NOTE]
    >  這是結構描述的完整的名稱。  
  
5.  在 [事實總管] 中，展開**NAOrderDoc.xsd**，然後展開**OrderDoc**。  
  
6.  在 規則 視窗中，以滑鼠右鍵按一下**條件**，指向 **述詞**，然後按一下 **等於**。  
  
7.  從 [事實總管] 中，拖曳**customerName**元素**引數 1**節點下的**條件**。  
  
8.  按一下**引數 2**  節點，然後輸入**GlobalBankWest**。  
  
9. 在 [事實總管] 中，按一下 [**詞彙**] 索引標籤。展開**ESB。行程**詞彙中，展開**1.1 版**，然後將拖曳**設定路線名稱**定義，以**動作**。  
  
10. 按一下**\<空字串\>** ，然後輸入**GlobalBankWestItinerary**。  
  
    > [!NOTE]
    >  稍後在本使用說明主題中，您會根據 GlobalBank 西這個行程建立來處理訊息。  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-east"></a>若要加入客戶 GlobalBank 東部的選取範圍規則  
  
1.  在 原則總管 中，以滑鼠右鍵按一下**SetGlobalBankWestItinerary**規則，，然後按一下 **複製**。  
  
2.  以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **貼上**。  
  
3.  在**新規則的名稱**] 對話方塊中，輸入**SetGlobalBankEastItinerary**，然後按一下 [**確定**。  
  
4.  在 原則總管 中，按一下  **SetGlobalBankEastItinerary**規則。  
  
5.  在**條件**區段中，以滑鼠右鍵按一下**GlobalBankWest**，然後按一下 **重設引數**。  
  
6.  按一下**引數 2**，然後輸入**GlobalBankEast**。  
  
7.  在**動作**區段中，以滑鼠右鍵按一下**GlobalBankWestItinerary**，然後按一下 **重設引數**。  
  
8.  按一下**\<空字串\>** ，然後輸入**GlobalBankEastItinerary。**  
  
    > [!NOTE]
    >  稍後在本使用說明主題中，您將從 GlobalBank 東這個行程建立來處理訊息。  
  
#### <a name="to-publish-and-deploy-the-policy"></a>若要發行和部署原則  
  
1.  在 原則總管 中，在**ResolveItineraryBasedOnCustomer**原則，按一下**版本 1.0 （未儲存）**，然後按一下 **發行**。  
  
2.  在 原則總管 中，在**ResolveItineraryBasedOnCustomer**原則，按一下**1.0 版-已發佈**，然後按一下 **部署**。  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-west-messages"></a>若要建立 GlobalBank 西訊息 ESB 路線 DSL 模型  
  
1.  在**Visual Studio**，開啟 C:\HowTos\Patterns\Patterns.sln。  
  
2.  在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。  
  
3.  在**加入新項目**對話方塊，在 [範本] 窗格中，按一下**ItineraryDsl**。  
  
4.  在**名稱**方塊中，輸入**GlobalBankWestItinerary**，然後按一下 **新增**。  
  
#### <a name="to-configure-the-properties-of-the-globalbank-west-itinerary"></a>若要設定 GlobalBank 西路線的屬性  
  
1.  在 Visual Studio 中，按一下設計介面的**GlobalBankWestItinerary.itinerary**。 在**GlobalBankWestItinerary**屬性 視窗中，設定下列屬性：  
  
    1.  在**模型匯出工具**下拉式清單中，按一下 **資料庫路線匯出工具**。  
  
    2.  按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。  
  
    3.  在**連接屬性**對話方塊中，選擇裝載路線的儲存機制資料庫，SQL Server，，然後指定資料庫的名稱 (預設名稱是**EsbItineraryDb**)。  
  
2.  在**路線狀態**下拉式清單中，按一下 **部署**。  
  
    > [!NOTE]
    >  這個步驟可讓您匯出至中央儲存機制; 路線可以選取和接收訊息時就會從這個儲存機制附加行程。 您稍後將設定要用於評估內送的訊息，並從這個儲存機制中選取適當的行程 BRI 解析程式路線選取器管線元件。  
  
#### <a name="to-define-the-structure-of-the-globalbank-west-itinerary"></a>若要定義 GlobalBank 西路線的結構  
  
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
  
    3.  在**匝道**下拉式清單中，展開**SendNAOrder**，然後按一下 **傳送處理常式**。  
  
4.  以滑鼠右鍵按一下**解析程式**集合**RouteMessage**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**StaticResolver**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**傳輸名稱**下拉式清單中，按一下 **檔案**。  
  
    4.  按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\West%MessageID%.xml**。  
  
5.  在工具箱中，按一下 **連接器**。 拖曳連接**ReceiveNAOrder**模型項目的**RouteMessage**模型項目。  
  
6.  在工具箱中，按一下 **連接器**。 拖曳連接**RouteMessage**模型項目的**SendNAOrder**模型項目。  
  
#### <a name="to-export-the-globalbank-west-model-to-the-itinerary-database"></a>將 GlobalBank 西模型匯出至路線資料庫  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**GlobalBankWestItinerary**路線，然後再按一下**匯出模型**。  
  
    > [!NOTE]
    >  路線已經匯出成路線的資料庫，現在可供路線選取器元件。  
  
2.  儲存專案的所有成品。  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-east-message"></a>若要建立 GlobalBank 東部訊息 ESB 路線 DSL 模型  
  
1.  在**Visual Studio**，開啟 C:\HowTos\Patterns.sln。  
  
2.  在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。  
  
3.  在**加入新項目**對話方塊，在 [範本] 窗格中，按一下**ItineraryDsl**。  
  
4.  在**名稱**方塊中，輸入**GlobalBankEastItinerary**，然後按一下 **新增**。  
  
#### <a name="to-configure-the-properties-of-the-globalbank-east-itinerary"></a>若要設定的 GlobalBank 東部路線屬性  
  
1.  在 Visual Studio 中，按一下設計介面的**GlobalBankEastItinerary.itinerary**。 在**GlobalBankEastItinerary**屬性 視窗中，設定下列屬性：  
  
    1.  在**模型匯出工具**下拉式清單中，按一下 **資料庫路線匯出工具**。  
  
    2.  按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。  
  
    3.  在**連接屬性**對話方塊中，選擇裝載路線的儲存機制資料庫，SQL Server，，然後指定資料庫的名稱 (預設名稱是**EsbItineraryDb**)。  
  
2.  在**路線狀態**下拉式清單中，按一下 **部署**。  
  
    > [!NOTE]
    >  這個步驟可讓您匯出至中央儲存機制; 路線可以選取和接收訊息時就會從這個儲存機制附加行程。 您稍後將設定要用於評估內送的訊息，並從這個儲存機制中選取適當的行程 BRI 解析程式路線選取器管線元件。  
  
#### <a name="to-define-the-structure-of-the-globalbank-east-itinerary"></a>若要定義 GlobalBank 東部路線的結構  
  
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
  
    3.  在**匝道**下拉式清單中，展開**SendNAOrder**，然後按一下 **傳送處理常式**。  
  
4.  以滑鼠右鍵按一下**解析程式**集合**RouteMessage**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**StaticResolver**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。  
  
    3.  在**傳輸名稱**下拉式清單中，按一下 **檔案**。  
  
    4.  按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\East%MessageID%.xml**。  
  
5.  在工具箱中，按一下 **連接器**。 拖曳連接**ReceiveNAOrder**模型項目的**RouteMessage**模型項目。  
  
6.  在工具箱中，按一下 **連接器**。 拖曳連接**RouteMessage**模型項目的**SendNAOrder**模型項目。  
  
#### <a name="to-export-the-globalbank-east-model-to-the-itinerary-database"></a>將 GlobalBank 東部模型匯出至路線資料庫  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**GlobalBankEastItinerary**路線，然後再按一下**匯出模型**。  
  
    > [!NOTE]
    >  路線已經匯出成路線的資料庫，現在可供路線選取器元件。  
  
2.  儲存專案的所有成品。  
  
## <a name="steps"></a>步驟  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a>若要建立及設定 ESB 上手  
  
1.  按一下**啟動**在工作列上，指向**所有程式**，指向  **BizTalk Server**，然後按一下  **BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，依序展開**應用程式**，然後展開**Microsoft.Practices.ESB**。  
  
3.  以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**。  
  
4.  在**選取接收埠**對話方塊中，按一下  **OnRamp.Itinerary**，然後按一下 **確定**。  
  
5.  在**接收位置屬性**對話方塊中，於**名稱**方塊中，輸入**OnRamp.Itinerary.HowTo**。  
  
6.  在**類型**下拉式清單中，按一下 **檔案，** ，然後按一下 **設定**。  
  
7.  中**FILE 傳輸屬性**對話方塊中，於**接收資料夾**方塊中，輸入**C:\HowTos\DropFolder**，然後按一下 **確定**。  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a>若要設定路線選取器管線元件  
  
1.  在**接收位置屬性**對話方塊中，按一下  **ItinerarySelectReceiveXml**中**接收管線**下拉式清單，，然後按一下省略符號按鈕 （...）。  
  
2.  使用**設定管線**對話方塊來設定下列**路線選取器**元件屬性：  
  
    1.  按一下**ItineraryFactKey**屬性，，然後輸入**Resolver.Itinerary**。  
  
    2.  按一下**ResolverConnectionString**屬性，，然後輸入**BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**  
  
    3.  按一下**確定**關閉**設定管線** 對話方塊。  
  
        > [!NOTE]
        >  由於此接收位置解譯 XML 交換，XML 解譯器元件就不需要設定。  
  
3.  按一下**確定**關閉**接收位置屬性** 對話方塊。  
  
4.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**啟用**。  
  
#### <a name="to-test-the-itinerary-selector-and-business-rules"></a>若要測試的行程選取器 」 和 「 商務規則  
  
1.  在 Windows 檔案總管，瀏覽至 C:\HowTos。  
  
2.  複製 （不會移動） Batch.xml DropFolder 資料夾。  
  
3.  瀏覽至 C:\HowTos\Out。請確認的已寫入一個 West%MessageID%.xml 訊息與兩個 East%MessageID%.xml 訊息目錄。  
  
    > [!NOTE]
    >  雖然訊息是相同的但客戶元素的值，但它們的處理使用不同的行程，根據路線選取器管線元件的解析度。  
  
4.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下 OnRamp.Itinerary.HowTo 接收位置，然後再按一下停用。  
  
5.  之後**OnRamp.Itinerary.HowTo**接收位置已停用，以滑鼠右鍵按一下，，然後按一下**刪除**。 在**確認刪除接收位置**對話方塊中，按一下 **是**。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [如何：使用商務規則原則選取路線](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [安裝和執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)  
  
-   [訊息路由模式](../esb-toolkit/message-routing-patterns.md)