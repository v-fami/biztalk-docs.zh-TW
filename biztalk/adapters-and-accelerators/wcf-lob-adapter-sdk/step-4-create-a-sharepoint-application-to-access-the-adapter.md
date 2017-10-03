---
title: "步驟 4： 建立 Sharepoint 應用程式存取配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2d8c398-370a-4c62-961d-0eab6066ad5a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3360bbdf5ae5a6a8dde9851c544342ea6a6bc1cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-a-sharepoint-application-to-access-the-adapter"></a>步驟 4： 建立 Sharepoint 應用程式存取配接器
![步驟 4 之 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **若要完成的時間：** 15 分鐘  
  
 在此步驟中您會需要您使用商務資料目錄定義編輯器工具所建立的應用程式定義檔，並匯入 Microsoft Office SharePoint Server。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您應該已經建立應用程式檔案中所述[步驟 3： 建立應用程式定義檔](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md)。  
  
-   Microsoft Single Sign-on 服務必須執行。  
  
## <a name="how-to-create-a-sharepoint-application"></a>如何建立 SharePoint 應用程式  
 建立 SharePoint 應用程式包含下列步驟：  
  
-   在 SharePoint 中建立的單一登入 (SSO) 應用程式。  
  
-   建立共用服務提供者，並匯入應用程式定義檔。  
  
-   建立 Web 組件頁面，並加入 Web 組件。  
  
 本主題示範如何執行這些步驟。  
  
## <a name="creating-an-sso-application-in-sharepoint"></a>在 SharePoint 中建立的 SSO 應用程式  
 若要從 SharePoint 應用程式回應配接器傳遞使用者認證，您必須設定 SSO 應用程式對應至使用者帳戶或群組。  
  
#### <a name="manage-server-settings-for-single-sign-on"></a>管理伺服器設定為單一登入  
  
1.  啟動 SharePoint 3.0 管理中心。 在**啟動**功能表上，指向**所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在上方導覽列中，按一下 **作業**。  
  
3.  在 [作業] 頁面中**安全性組態**區段中，按一下**管理設定單一登入**。  
  
4.  在 管理的設定單一登入頁面上，在**伺服器設定**區段中，按一下**管理伺服器設定**。  
  
5.  請確定此頁面上的資訊正確安裝單一登入。 如需有關這些作業的詳細資訊，請參閱 「 設定單一登入 (Office SharePoint Server) >，網址[http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291)。  
  
#### <a name="manage-settings-for-enterprise-application-definitions"></a>管理企業應用程式定義的設定  
  
1.  在 SharePoint 管理中心 的上方導覽列上，按一下**作業**。  
  
2.  在 [作業] 頁面中**安全性組態**區段中，按一下**進行單一登入的管理設定**。  
  
3.  在 管理的設定單一登入頁面上，在**企業應用程式定義設定**區段中，按一下**管理企業應用程式定義的設定**。  
  
4.  管理企業應用程式定義] 頁面上，按一下 [**新項目**。  
  
5.  建立企業應用程式定義 頁面上，設定**顯示名稱**欄位設為**EchoSSO**，然後設定**應用程式名稱**欄位設為**EchoSSO**。 此值應該符合您在中指定的 SecondarySsoApplicationId[步驟 3： 建立應用程式定義檔](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md)。  
  
6.  在**連絡電子郵件地址**欄位中輸入您的電子郵件地址，然後再按一下**確定**。  
  
#### <a name="manage-account-information-for-enterprise-application-definitions"></a>管理企業應用程式定義的帳戶資訊  
  
1.  在 SharePoint 管理中心 的上方導覽列上，按一下**作業**。  
  
2.  在 [作業] 頁面中**安全性組態 > 一節**，按一下**管理設定單一登入**。  
  
3.  在 管理的設定單一登入頁面上，在**企業應用程式定義設定**區段中，按一下**管理的帳戶資訊的企業應用程式定義**。  
  
4.  管理帳戶資訊的企業應用程式定義，在選取**EchoSSO**從**企業應用程式定義**清單。  
  
5.  在**群組帳戶名稱**欄位中，輸入將用來保護此應用程式定義的 Windows 群組。 例如， **DOMAIN\Domain 使用者**。  
  
6.  按一下 **[設定]**。  
  
7.  在提供 EchoSSO 帳戶資訊 頁面上，在**Username**欄位類型**testuser**，然後在**密碼**欄位類型**testpassword**.  
  
8.  按一下**確定**，然後按一下 **完成**。  
  
## <a name="creating-a-shared-services-provider-and-importing-the-application-definition-file"></a>建立共用服務提供者並匯入應用程式定義檔  
 共用服務提供者 (SSP) 是共用的服務和其支援資源的邏輯群組。 您可以使用 SharePoint 管理中心主控台，以建立 SSP。 這個範例適用於任何 ssp。 如需建立 SSP 的詳細資訊，請參閱 「 章概觀： 建立及設定共用服務提供者 」 在[http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119)。  
  
### <a name="to-import-the-application-definition-file"></a>若要匯入應用程式定義檔  
  
1.  啟動 SharePoint 3.0 管理中心。 在**啟動**功能表上，指向**所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側瀏覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。  
  
3.  在**商務資料目錄**區段中，按一下**匯入應用程式定義**。  
  
4.  在匯入應用程式定義 頁面上，按一下 **瀏覽**，然後選取 EchoWS.xml 檔案。  
  
5.  按一下**匯入**，然後按一下 **確定**。  
  
## <a name="creating-web-parts"></a>建立 Web 組件  
 您現在必須在您要使用編輯器中建立商務資料目錄定義的方法執行個體的 SharePoint 網站中建立 Web 組件。 Web 組件是資訊的可重複使用的元件，可以包含任何一種 Web 架構，包括分析、 共同作業，和資料庫資訊。  
  
#### <a name="to-create-a-web-part-page"></a>若要建立 Web 組件頁面  
  
1.  啟動 SharePoint 3.0 管理中心。 在**啟動**功能表上，指向**所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側瀏覽窗格中，按一下您匯入應用程式定義檔的 SSP 的名稱。  
  
3.  在右上角的 共用服務管理 頁面上，按一下 **網站動作**，然後按一下 **建立**。  
  
     ![建立網站動作](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/13f43659-ef61-48db-ac19-2d553367ec7e.gif "13f43659-ef61-48db-ac19-2d553367ec7e")  
  
4.  在**建立**頁面上，於**網頁**區段中，按一下**Web 組件頁面**。  
  
5.  在新的 Web 組件 頁面上，在**名稱**欄位中，輸入**EchoPart**，然後選取**整頁、 垂直**從**選擇版面配置範本**清單。  
  
6.  按一下 **[建立]**。  
  
#### <a name="to-add-a-business-data-web-part"></a>若要將商務資料 Web 組件  
  
1.  按一下**新增網頁組件**。  
  
2.  在**新增網頁組件**對話方塊中，選取**商務資料清單**，然後按一下 **新增**。  
  
     ![商務資料清單](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/cd9e6bc8-c37e-49d2-9eaa-77246bb593df.gif "cd9e6bc8-c37e-49d2-9eaa-77246bb593df")  
  
3.  按一下**開啟工具窗格**。  
  
4.  在右窗格中，開啟 [商務資料清單] 工具窗格。 在**商務資料清單** 區段中，針對**類型**欄位中，按一下**瀏覽** 按鈕。  
  
     ![選取類型](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a054ed0e-0880-4154-9050-a00da356a4f6.gif "a054ed0e-0880-4154-9050-a00da356a4f6")  
  
5.  在**商務資料型別選擇器**對話方塊中，選取**EchoWSLob_Instance**應用程式，，然後按一下**確定**。  
  
6.  商務資料清單] 工具窗格中，按一下 [**確定**。  
  
7.  您會看到可讓您輸入要傳遞至 EchoGreetings 方法問候語值的欄位。 問候語欄位中輸入資料，然後按一下**抓取資料**。 這會叫用回應配接器裝載於 IIS 的 EchoGreetings 方法，並傳回回應。  
  
     ![EchoGreetings 清單](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/f5a22fcd-2ae6-4384-9879-f0abd0255325.gif "f5a22fcd-2ae6-4384-9879-f0abd0255325")  
  
    > [!NOTE]
    >  名稱資料行不包含使用者資訊，但只會顯示 BDC。名稱。 這是因為 BDC 預期只有簡單的記錄結構，並不會顯示 [名稱] 欄位所表示的複雜結構。  
  
8.  按一下**結束編輯模式**從頁面的右上角。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 您已使用 SharePoint 3.0 管理中心 來匯入應用程式定義，並建立使用這個定義，叫用 EchoGreetings 作業的回應配接器的 Web 組件。  
  
## <a name="next-steps"></a>後續步驟  
 完成本教學課程。 如需使用商務資料目錄，請參閱 「 商務資料目錄 」 在[http://go.microsoft.com/fwlink/?LinkId=119921](http://go.microsoft.com/fwlink/?LinkId=119921)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 3： 裝載在 IIS 中的回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)