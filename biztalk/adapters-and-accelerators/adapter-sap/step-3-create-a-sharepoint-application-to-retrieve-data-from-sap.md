---
title: "步驟 3： 建立 SharePoint 應用程式來擷取 SAP 資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO application, creating an
- Business Data Catalog Definition Editor
- application definition file, importing
- Web Part
- SSP
- Web Part page, creating a
- Shared Services Provider, creating a
ms.assetid: 7158caec-9dc0-477c-9db3-179e634e5196
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 879a4b48da7645471e53db357f7c0a6260117f99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-a-sharepoint-application-to-retrieve-data-from-sap"></a>步驟 3： 建立 SharePoint 應用程式來擷取 SAP 資料
![步驟 4 之 3](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **若要完成的時間：** 15 分鐘  
  
 **目標：**您現在必須接受使用 「 商務資料目錄定義編輯器 」 工具，您建立的應用程式定義檔，並匯入 Microsoft Office SharePoint Server。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您應已建立的應用程式定義檔中所述[步驟 2： 建立應用程式定義檔 SAP 成品](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md)。  
  
-   Microsoft Single sign-on 服務必須執行。  
  
## <a name="how-to-create-a-sharepoint-application"></a>如何建立 SharePoint 應用程式  
 建立 SharePoint 應用程式包含下列步驟：  
  
-   在 SharePoint 中建立的單一登入 (SSO) 應用程式  
  
-   建立共用服務提供者  
  
-   匯入應用程式定義檔  
  
-   建立 Web 組件頁面，並加入 Web 組件  
  
 本主題示範如何執行這些步驟。  
  
## <a name="creating-an-sso-application-in-sharepoint"></a>在 SharePoint 中建立的 SSO 應用程式  
 若要存取 SAP 系統從 SharePoint 應用程式中的資料，您必須設定 SAP 使用者對應的 SharePoint 使用者的 SSO 應用程式。 在 SharePoint 中建立的 SSO 應用程式包含下列步驟：  
  
1.  **管理伺服器設定的單一登入**。 在此步驟中，您可以指定使用者帳戶可管理和設定單一登入服務。 您可以在 [管理伺服器設定] 頁面上。 此選項可從 SharePoint 管理中心主控台。 如需這個步驟的詳細資訊，請參閱 「 設定單一登入 Office SharePoint Server 2007 的 」 一節[http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291)。  
  
2.  **管理企業應用程式定義設定**。 在此步驟中，您會設定企業應用程式定義的設定。 您可以從企業應用程式定義 頁面上管理設定。 此選項可從 SharePoint 管理中心主控台。  
  
    1.  在 [管理中心] 的上方導覽列上，按一下**作業**。  
  
    2.  在 [作業] 頁面中**安全性組態**區段中，按一下**管理設定單一登入**。  
  
    3.  在 管理的設定單一登入頁面上，在**企業應用程式定義設定**區段中，按一下**管理企業應用程式定義設定**。  
  
    4.  在 [管理企業應用程式定義] 頁面提供的值**顯示名稱**，**應用程式名稱**，而**連絡電子郵件地址**欄位。  
  
        > [!IMPORTANT]
        >  如**應用程式名稱**欄位中，請確定您指定相同的 SSO 應用程式名稱所指定**SecondarySsoApplicationId**時建立應用程式定義檔中，做為變數中所述[步驟 2： 建立應用程式定義檔 SAP 成品](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md)。  
  
    5.  將其他欄位保留為預設值，然後按一下**確定**。  
  
3.  **管理企業應用程式定義的帳戶資訊**。 在此步驟中，您可以啟用個別使用者或群組，從 SharePoint 連接至企業應用程式。 基本上，在此步驟中您對應個別使用者或群組到使用者在 LOB 系統。 您也可以指定要連接至 LOB 系統的認證。 您可以從企業應用程式定義 頁面上的管理帳戶資訊。 此選項可從 SharePoint 管理中心主控台。 如需這個步驟的詳細資訊，請參閱 「 管理企業應用程式定義的帳戶資訊 」 一節[http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291)。  
  
## <a name="creating-a-shared-services-provider"></a>建立共用的服務提供者  
 共用服務提供者是共用的服務和其支援資源的邏輯群組。 您可以使用 SharePoint 管理中心主控台，以建立 SSP。  
  
 建立 SSP 時，您必須定義的網站 請記住的連接埠號碼和您所建立的網站位址。 您將這個網站來匯入商務資料目錄應用程式定義。  
  
 如需建立 SSP 的詳細資訊，請參閱 「 章概觀： 建立及設定共用服務提供者 」 在[http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119)。  
  
## <a name="importing-the-application-definition-file"></a>匯入應用程式定義檔  
 您必須立即匯入應用程式定義檔的 ssp。  
  
#### <a name="to-import-the-application-definition-file"></a>若要匯入應用程式定義檔  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側瀏覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。  
  
3.  在**商務資料目錄**區段中，按一下**匯入應用程式定義**。  
  
4.  匯入應用程式定義頁面上，開啟時，請瀏覽至 Customer_Orders.xml，選取檔案，然後**開啟**。  
  
5.  按一下 **[匯入]**。  
  
6.  按一下 **[確定]**。  
  
     匯入後的應用程式，您可以檢視您的應用程式，請前往**檢視應用程式**連結。 按一下 應用程式名稱，以查看應用程式中的實體。  
  
## <a name="creating-web-parts"></a>建立 Web 組件  
 您現在必須建立 Web 組件在 SharePoint 網站來檢視和管理將擷取從 SAP 系統的商務資料。 Web 組件是資訊的可重複使用的元件，可以包含任何一種 Web 架構，包括分析、 共同作業，和資料庫資訊。  
  
 在此教學課程中，Web 組件會建立所建立的商務資料目錄定義編輯器的方法執行個體。 Office SharePoint Server 提供特定使用的不同的 Web 組件。 這裡使用下列 Web 組件：  
  
-   **商務資料清單**Web 組件**Finder**方法執行個體。 此 Web 組件可讓您指定要從 SAP 系統中擷取客戶清單的搜尋運算式。 此教學課程中，這稱為搜尋客戶的 Web 組件。  
  
-   **商務資料項目**Web 組件**特定搜尋工具**方法執行個體。 此 Web 組件會顯示您搜尋客戶的 Web 組件從選取的特定客戶的詳細資料。 此 Web 組件會對應至搜尋客戶的 Web 組件。  此教學課程中，這稱為客戶詳細資料 Web 組件。  
  
-   **商務資料相關清單**Web 組件**關聯**方法執行個體。 此 Web 組件會列出您搜尋客戶的 Web 組件從選取的特定客戶的銷售訂單。 此 Web 組件是搜尋客戶的 Web 組件相關聯。  此教學課程中，這稱為銷售訂單詳細資料 Web 組件。  
  
 本節中的指示來建立這些 Web 組件，並建立它們之間的關聯。 如需建立 Web 組件的詳細資訊，請參閱 < 自訂商務資料清單、 Web 組件和站台 」 在[http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131)。  
  
 Web 組件將會加入至單一的 Web 組件頁面。 加入 Web 組件之前，您必須建立 Web 組件頁面。 此教學課程中，此 Web 組件頁面稱為 Customer_SalesOrders。  
  
### <a name="creating-a-web-part-page"></a>建立網頁組件  
 本節提供建立 Web 組件頁面的指示。  
  
##### <a name="to-create-a-web-part-page"></a>若要建立 Web 組件頁面  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下**啟動**，指向**所有程式**，指向 [ **Microsoft Office Server**，然後按一下**SharePoint 3.0 管理中心]**。  
  
2.  在左側瀏覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。  
  
3.  在右上角的 共用服務管理 頁面上，按一下 **網站動作**，然後按一下 **建立**。  
  
     ![若要建立的 web 組件的功能表](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")  
  
4.  在 [建立] 頁面中**網頁**區段中，按一下**Web 組件頁面**。  
  
5.  在新的 Web 組件 頁面上，執行下列作業：  
  
    1.  在**名稱**欄位中，輸入頁面的名稱。 此教學課程中，輸入相同的名稱。 **Customer_SalesOrders**。  
  
    2.  選取**檔案已經存在覆寫**核取方塊，如果您想要覆寫舊的頁面，與您建立新的頁面名稱相同。  
  
    3.  在**配置**] 區段中，從**選擇版面配置範本**方塊中，選取 [Web 組件頁面的版面配置。 此教學課程中，選取**標頭，左側資料行中，主體**。  
  
    4.  在**儲存位置**區段的**文件庫**清單中，按一下**表單範本**。  
  
    5.  按一下 **[建立]**。 只在建立之後下, 圖顯示 Web 組件頁面。  
  
         ![空的 Web 組件頁面](../../adapters-and-accelerators/adapter-sap/media/6aa68c43-59df-47c4-95a6-453f7c668025.gif "6aa68c43-59df-47c4-95a6-453f7c668025")  
  
    6.  您現在必須將不同的 Web 組件加入此頁面。  
  
### <a name="adding-a-business-data-list-web-part"></a>新增商務資料清單網頁組件  
 您現在必須新增 Web 組件頁面的商務資料清單網頁組件。 使用此 Web 組件會擷取客戶清單，從 SAP 系統符合搜尋運算式。 此 Web 組件會對應至**Finder**方法執行個體 (*GetCustomerByName_Instance*) 建立的商務資料目錄定義編輯器。  
  
##### <a name="to-add-a-business-data-list-web-part"></a>若要加入商務資料清單網頁組件  
  
1.  在 Customer_SalesOrders 頁面上，在**標頭**區段中，按一下**新增網頁組件**。  
  
2.  在**新增網頁組件**對話方塊中，於**商務資料**區段中，選取**商務資料清單**核取方塊，然後**新增**。  
  
     ![若要建立商務資料 Web 組件的選項](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")  
  
3.  新增商務資料清單 Web 組件中，按一下 **開啟工具窗格**連結。  
  
     ![Web 組件中開啟工具窗格](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")  
  
4.  在右窗格中，開啟 [商務資料清單] 工具窗格。 在**商務資料清單** 區段中，針對**類型**欄位中，按一下**瀏覽** 按鈕。  
  
     ![商務資料清單 工具窗格](../../adapters-and-accelerators/adapter-sap/media/580c58bf-bfc7-4d48-8c62-8ca4eee4ab48.gif "580c58bf-bfc7-4d48-8c62-8ca4eee4ab48")  
  
5.  在**商務資料型別選擇器**對話方塊中，選取**Customer_Order_Instance**應用程式，，然後按一下**確定**。  
  
     ![選取的應用程式執行個體](../../adapters-and-accelerators/adapter-sap/media/79967c27-9c76-4394-89bc-38c63649bdda.gif "79967c27-9c76-4394-89bc-38c63649bdda")  
  
6.  展開**外觀** 節點，然後在**標題**方塊中，輸入 Web 組件的標題。 此 Web 組件中，輸入**客戶清單**。  
  
7.  在 商務資料清單 工具窗格中，按一下 **套用**，然後按一下 **確定**。 商務資料清單網頁組件現在看起來如下所示：  
  
     ![商務資料清單 」 Web 組件](../../adapters-and-accelerators/adapter-sap/media/185fb3f3-98b0-4efe-960d-91312912ad7d.gif "185fb3f3-98b0-4efe-960d-91312912ad7d")  
  
8.  Web 組件會列出執行 SD_RFC_CUSTOMER_GET RFC 所傳回的欄位。 您可以移除不想要在 SharePoint 網站上顯示的欄位。 若要移除欄位，請按一下**編輯檢視**右上角的 網頁組件連結。  
  
9. 在 [編輯檢視] 頁面的資料行區段中，清除核取方塊，針對您不想要顯示的資料行。  
  
     ![在 SharePoint 中檢視特定資料行](../../adapters-and-accelerators/adapter-sap/media/24213b67-aafe-4534-91a7-06bde7bcbf7c.gif "24213b67-aafe-4534-91a7-06bde7bcbf7c")  
  
10. 按一下 **[確定]**。  
  
### <a name="adding-a-business-data-item-web-part"></a>加入商務資料的項目 Web 組件  
 您現在必須新增 Web 組件頁面的商務資料的項目 Web 組件。 您也將連接與商務資料清單 Web 組件您剛才建立的此 Web 組件。 如此一來，您可以查看您在商務資料清單網頁組件中選取客戶的詳細資料。 此 Web 組件會對應至**特定搜尋工具**方法執行個體 (*GetCustomerByNumber_Instance*) 建立的商務資料目錄定義編輯器。  
  
##### <a name="to-add-a-business-data-item-web-part"></a>若要將商務資料的項目 Web 組件  
  
1.  在右上角的 Customer_SalesOrders 頁面上，按一下 **網站動作**，然後按一下 **編輯頁面**。  
  
2.  在 Customer_SalesOrders 頁面上，在**左欄**區段中，按一下**新增網頁組件**。  
  
3.  在**新增網頁組件**對話方塊中，於**商務資料**區段中，選取**商務資料項目**核取方塊，然後**新增**。  
  
4.  新增商務資料的項目 Web 組件中，按一下 **開啟工具窗格**連結。  
  
5.  在右窗格中，開啟 [商務資料項目] 工具窗格。 在**商務資料項目** 區段中，針對**類型**欄位中，按一下**瀏覽** 按鈕。  
  
     ![商務資料項目 工具窗格](../../adapters-and-accelerators/adapter-sap/media/29322df5-4ce3-4c1f-a658-39a355dfe2aa.gif "29322df5-4ce3-4c1f-a658-39a355dfe2aa")  
  
6.  在**商務資料型別選擇器**對話方塊中，選取**Customer_Order_Instance**應用程式，，然後按一下**確定**。  
  
7.  在**檢視**清單中，選取**預設**。  
  
8.  保留**項目**空的清單。  
  
    > [!NOTE]
    >  如**項目** 欄位中，您必須指定客戶名稱或客戶編號，您想要查看詳細資料。 此 Web 組件當做輸入參數。 因為您會藉由連接到商務資料清單網頁組件取得的輸入的參數，您不必明確指定項目。  
  
9. 在**欄位**區段中，按一下**選擇**，選取您想要顯示在頁面上的欄位。  
  
10. 展開**外觀** 節點，然後在**標題**欄位中，指定 Web 組件的標題。 此 Web 組件中，指定**詳細資料，找出特定客戶**。  
  
11. 按一下**套用**，然後按一下 **確定**。  
  
12. 若要將 Web 組件連接**客戶清單**Web 組件。 若要這樣做：  
  
    1.  按一下**編輯**靠近右上角的 Web 組件。  
  
    2.  從內容功能表中指向**連線**，指向 **取得項目從**，然後按一下**客戶清單**。  
  
         ![連接兩個 Web 組件](../../adapters-and-accelerators/adapter-sap/media/505aead7-f498-448f-a7cb-55d0a121f91f.gif "505aead7-f498-448f-a7cb-55d0a121f91f")  
  
### <a name="adding-a-business-data-related-list-web-part"></a>加入商務資料相關清單 Web 組件  
 您現在必須新增 Web 組件頁面的商務資料相關清單 Web 組件。 您也會連接商務資料清單 Web 組件您稍早建立的此 Web 組件。 如此一來，您將能夠看到您在商務資料清單網頁組件中選取客戶的銷售訂單。 此 Web 組件會對應至**關聯**方法執行個體 (*SalesOrderForCustomer_Instance*) 建立的商務資料目錄定義編輯器。  
  
##### <a name="to-add-a-business-data-related-list-web-part"></a>若要新增商務資料相關清單 Web 組件  
  
1.  在 Customer_SalesOrders 頁面上，在**主體**區段中，按一下**新增網頁組件**。  
  
2.  在**新增網頁組件**對話方塊中，於**商務資料**區段中，選取**商務資料相關清單**核取方塊，然後按一下**新增**。  
  
3.  新增商務資料相關清單 Web 組件中，按一下 **開啟工具窗格**連結。  
  
4.  在右窗格中，開啟 [商務資料相關清單] 工具窗格。 在**商務資料相關清單** 區段中，針對**類型**欄位中，按一下**瀏覽** 按鈕。  
  
     ![商務資料相關清單](../../adapters-and-accelerators/adapter-sap/media/1914e12d-27f0-4ecb-9605-3177183a2d44.gif "1914e12d-27f0-4ecb-9605-3177183a2d44")  
  
5.  在**商務資料型別選擇器**對話方塊中，選取**Customer_Order_Instance**應用程式，，然後按一下**確定**。 **關聯性**清單填入名稱**關聯**方法執行個體 (*SalesOrderForCustomer_Instance*)。  
  
6.  展開**外觀** 節點，然後在**標題**方塊中，輸入 Web 組件的標題。 此 Web 組件中，輸入**找出特定客戶的銷售訂單**。  
  
7.  按一下**套用**，然後按一下 **確定**。  
  
8.  Web 組件會列出執行 BAPI_SALESORDER_GETLIST RFC 所傳回的欄位。 您可以移除不想要在 SharePoint 網站上顯示的欄位。 若要移除欄位，請按一下**編輯檢視**右上角的 網頁組件連結。  
  
9. 在 [編輯檢視] 頁面中**資料行**區段中，清除文字方塊中，針對您不想要顯示的資料行。  
  
10. 按一下 **[確定]**。  
  
11. 若要將 Web 組件連接**客戶清單**Web 組件。 若要這樣做：  
  
    1.  按一下**編輯**靠近右上角**找出特定客戶的銷售訂單**Web 組件。  
  
    2.  從內容功能表，指向**連線**，指向 **取得相關項目從**，然後按一下 **客戶清單**。  
  
12. 按一下**結束編輯模式**從頁面的右上角。  
  
## <a name="next-steps"></a>後續步驟  
 從 SAP 系統中擷取資料來測試 SharePoint 應用程式。 請參閱[步驟 4： 測試 SharePoint 應用程式](../../adapters-and-accelerators/adapter-sap/step-4-test-your-sharepoint-application1.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1： 從 SharePoint 網站上的 SAP 系統中呈現資料](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)