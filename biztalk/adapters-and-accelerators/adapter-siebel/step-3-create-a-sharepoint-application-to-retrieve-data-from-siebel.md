---
title: 步驟 3： 建立 SharePoint 應用程式來擷取 Siebel 的資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 86bde531-2daf-452b-b3e6-5481d66f72e7
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df6c92b371291f4359c4bbce5e16529700bcc0c8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971863"
---
# <a name="step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel"></a>步驟 3： 建立 SharePoint 應用程式來擷取 Siebel 資料
![步驟 4 之 3](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **若要完成的時間：** 15 分鐘。  
  
 **目標：** 您現在必須使用商務資料目錄定義編輯器中，您建立應用程式定義檔案，然後匯入 Office SharePoint Server。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您應該先建立應用程式定義檔中所述[步驟 2： 建立 Siebel 商務元件操作的應用程式定義檔](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md)。  
  
-   必須執行 Microsoft Single sign-on 服務。  
  
## <a name="how-to-create-a-sharepoint-application"></a>如何建立 SharePoint 應用程式  
 建立 SharePoint 應用程式包含下列步驟：  
  
-   在 SharePoint 中建立的單一登入 (SSO) 應用程式  
  
-   建立共用的服務提供者 (SSP)  
  
-   匯入應用程式定義檔  
  
-   建立網頁組件頁面上，並新增 Web 組件  
  
## <a name="creating-an-sso-application-in-sharepoint"></a>在 SharePoint 中建立的 SSO 應用程式  
 若要在 Siebel 系統中，從 SharePoint 應用程式存取資料，您必須設定對應到 Siebel 使用者的 SharePoint 使用者的 SSO 應用程式。 在 SharePoint 中建立的 SSO 應用程式包含下列步驟：  
  
1.  **管理伺服器設定單一登入**。 在此步驟中，您可以指定使用者帳戶可管理和設定單一登入服務。 您可以從管理伺服器設定 頁面來這麼做。 此選項可從 SharePoint 管理中心 的主控台。 如需此步驟的詳細資訊，請參閱 「 設定單一登入 Office SharePoint server 2007 」 一節[ http://go.microsoft.com/fwlink/?LinkId=105291 ](http://go.microsoft.com/fwlink/?LinkId=105291)。  
  
2.  **管理企業應用程式定義的設定**。 在此步驟中，您可以設定企業應用程式定義的設定。 您可以從企業應用程式定義 頁面上的管理設定來這麼做。 此選項可從 SharePoint 管理中心 的主控台。  
  
    1.  在 [管理中心] 的上方導覽列中，按一下**作業**。  
  
    2.  在 [作業] 頁面中，在**安全性設定**區段中，按一下**管理設定單一登入**。  
  
    3.  在 管理設定單一登入頁面上，在**企業應用程式定義設定**區段中，按一下**管理企業應用程式定義的設定**。  
  
    4.  在管理企業應用程式定義 頁面上，針對提供的值**顯示名稱**，**應用程式名稱**，而**連絡人電子郵件地址**欄位。  
  
        > [!IMPORTANT]
        >  針對**應用程式名稱**欄位中，請確定您指定您為指定的相同 SSO 應用程式名稱**SecondarySsoApplicationId**時建立應用程式定義檔中，做為變數中所述[步驟 2： 建立 Siebel 商務元件操作的應用程式定義檔](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md)。  
  
    5.  將其他欄位保留為預設值，然後按一下 **確定**。  
  
3.  **管理企業應用程式定義的帳戶資訊**。 在此步驟中，您可以啟用個別使用者或群組，從 SharePoint 連接到企業應用程式。 基本上，在此步驟中對應的個別使用者或群組到使用者 LOB 系統中。 您也可以指定要連接至 LOB 系統的認證。 則可以從 [管理帳戶資訊的企業應用程式定義] 頁面。 此選項可從 SharePoint 管理中心 的主控台。 如需有關此步驟的詳細資訊，請參閱的 「 管理企業應用程式定義的帳戶資訊 」 一節[ http://go.microsoft.com/fwlink/?LinkId=105291 ](http://go.microsoft.com/fwlink/?LinkId=105291)。  
  
## <a name="creating-a-shared-services-provider"></a>建立共用的服務提供者  
 SSP 是共用的服務和其支援的資源的邏輯群組。 您可以建立使用 SharePoint 中央系統管理主控台的 SSP。  
  
 您必須定義網站時建立的 ssp。 請記得連接埠號碼和您所建立的網站位址。 您會將商務資料目錄應用程式定義匯入此站台。  
  
 如需建立 SSP 的詳細資訊，請參閱 「 章概觀： 建立及設定共用服務提供者 」 在[ http://go.microsoft.com/fwlink/?LinkId=105119 ](http://go.microsoft.com/fwlink/?LinkId=105119)。  
  
## <a name="importing-the-application-definition-file"></a>匯入應用程式定義檔  
 您必須立即將應用程式定義檔案匯入的 ssp。  
  
#### <a name="to-import-the-application-definition-file"></a>若要匯入應用程式定義檔  
  
1. 啟動 SharePoint 3.0 管理中心。 按一下 **開始**，指向**所有程式**，指向**Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2. 在左側的導覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。  
  
3. 在 **商務資料目錄**區段中，按一下**匯入應用程式定義**。  
  
4. 匯入應用程式定義在開啟頁面上，瀏覽至 Siebel_Account.xml，選取檔案，然後**開啟**。  
  
5. 按一下 **[匯入]**。  
  
6. 按一下 [確定] 。  
  
   匯入後應用程式，您可以看到您的應用程式，方法是前往**檢視應用程式**連結。 按一下 若要查看應用程式中的實體的應用程式名稱。  
  
## <a name="creating-web-parts"></a>建立 Web 組件  
 您現在必須建立 Web 組件在 SharePoint 網站來檢視和管理會擷取來自 Siebel 系統的商務資料。 Web 組件是資訊的可重複使用的元件，可以包含任何一種 Web 架構，包括分析、 共同作業和資料庫資訊。  
  
 在本教學課程中，Web 組件會針對所建立的商務資料目錄定義編輯器的方法執行個體。 Office SharePoint Server 提供針對特定用途的不同類型的 Web 組件。 我們將使用 Finder 方法執行個體，**商務資料清單**Web 組件。 此 Web 組件可讓您指定帳戶的商務元件上執行查詢的搜尋運算式。 本教學課程中，我們稱之為**查詢帳戶**Web 組件。  
  
 本節中的指示來建立這些 Web 組件。 建立 Web 組件的詳細資訊，請參閱 Microsoft Office SharePoint Server 2007 文件 （「 自訂商務資料清單、 Web 組件，以及網站 」），網址[ http://go.microsoft.com/fwlink/?LinkId=104131 ](http://go.microsoft.com/fwlink/?LinkId=104131)。  
  
 Web 組件會加入一個單一的 Web 組件頁面。 您必須新增網頁組件之前建立的 Web 組件頁面。 本教學課程中，呼叫網頁組件頁面**Siebel 帳戶**。  
  
### <a name="creating-a-web-part-page"></a>建立網頁組件  
 本節中的指示來建立網頁組件頁面。  
  
##### <a name="to-create-a-web-part-page"></a>若要建立網頁組件  
  
1. 啟動 SharePoint 3.0 管理中心。 按一下 **開始**，指向**所有程式**，指向**Microsoft Office Server**，然後按一下**SharePoint 3.0 管理中心**。  
  
2. 在左側的導覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。  
  
3. 在 共用服務管理頁面上，從右上角，按一下 **站台動作**，然後按一下**建立**。  
  
    ![若要建立的 web 組件 功能表](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")  
  
4. 在 [建立] 頁面下**網頁**區段中，按一下**網頁組件頁面**。  
  
5. 在 [新增網頁組件] 頁面中，執行下列作業：  
  
   1. 在 **名稱**欄位中，指定頁面的名稱。 本教學課程中，將名稱指定為`Siebel Account`。  
  
   2. 選取 **覆寫，如果檔案已經存在**核取方塊，如果您想要覆寫舊的畫面與您建立的網頁名稱相同。  
  
   3. 在 **版面配置**區段中，從**選擇版面配置範本**方塊中，選取 Web 組件頁面的版面配置。 本教學課程中，選取**完整的頁面上，垂直**。  
  
   4. 在 **儲存的位置**區段中**文件庫**清單中，選取**表單範本**。  
  
   5. 按一下 **[建立]**。 只要在建立之後下, 圖會顯示 Web 組件頁面。  
  
       ![空的 Web 組件頁面](../../adapters-and-accelerators/adapter-siebel/media/1fa218f5-de81-43be-b1b1-c46de422f112.gif "1fa218f5-de81-43be-b1b1-c46de422f112")  
  
      您現在必須在此頁面中新增不同的 Web 組件。  
  
### <a name="adding-a-business-data-list-web-part"></a>新增商務資料清單網頁組件  
 您現在必須新增網頁組件頁面的商務資料清單 Web 組件。 您將使用此 Web 組件，來查詢帳戶商務元件使用的搜尋運算式。 此 Web 組件會對應至您所建立的商務資料目錄定義編輯器 Finder 方法執行個體 (QueryAccount)。  
  
##### <a name="to-add-a-business-data-list-web-part"></a>若要將商務資料清單 Web 組件  
  
1.  在  **Siebel 帳戶**頁面上，於**標頭**區段中，按一下**新增網頁組件**。  
  
2.  在 **新增網頁組件**對話方塊中，於**商務資料**區段中，選取**商務資料清單**核取方塊，然後按一下**新增**。  
  
     ![若要建立商務資料 Web 組件的選項](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")  
  
3.  新增商務資料清單 Web 組件中，按一下**開啟 [工具] 窗格**連結。  
  
     ![Web 組件中開啟工具窗格](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")  
  
4.  在右窗格中，開啟 [商務資料清單] 工具窗格。 在**商務資料清單**區段中，如**型別**欄位中，按一下**瀏覽** 按鈕。  
  
     ![商務資料清單 工具窗格](../../adapters-and-accelerators/adapter-siebel/media/3b6e1576-03ce-4fc8-bf5a-7b414ef4408c.gif "3b6e1576-03ce-4fc8-bf5a-7b414ef4408c")  
  
5.  在 **商務資料型別選擇器**對話方塊中，選取**Siebel_Account_Instance**應用程式，，然後按一下**確定**。  
  
     ![選取的應用程式執行個體](../../adapters-and-accelerators/adapter-siebel/media/a658d06a-83a8-4e4b-9451-ce58e7ac3632.gif "a658d06a-83a8-4e4b-9451-ce58e7ac3632")  
  
6.  依序展開**外觀**節點，然後在**標題**欄位中，指定 Web 組件的標題。 此 Web 組件中，指定**Account List**。  
  
7.  在 商務資料清單 工具窗格中，按一下 **套用**，然後按一下**確定**。 商務資料清單 Web 組件現在看起來如下所示：  
  
     ![商務資料清單 」 Web 組件](../../adapters-and-accelerators/adapter-siebel/media/06dbb84a-38c3-4ece-b981-5aa7471909ed.gif "06dbb84a-38c3-4ece-b981-5aa7471909ed")  
  
    > [!NOTE]
    >  您也可以變更參數資料行出現的順序。 您可以這樣做，即可**編輯檢視**往右上角的 網頁組件的連結。  
  
8.  按一下 **結束編輯模式**從頁面的右上角。  
  
## <a name="next-steps"></a>後續步驟  
 擷取 Siebel 系統中的資料來測試 SharePoint 應用程式。 請參閱[步驟 4： 測試 SharePoint 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/step-4-test-your-sharepoint-application.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1：在 SharePoint 網站上呈現 Siebel 系統的資料](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)