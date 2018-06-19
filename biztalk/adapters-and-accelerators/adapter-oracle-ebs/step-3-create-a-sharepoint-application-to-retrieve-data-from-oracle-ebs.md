---
title: 步驟 3： 建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eaa16011-9284-4ccf-8132-9c1e14cc6aa7
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fe9d6fc34fa039bb4b3861deb35fb51524180ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217198"
---
# <a name="step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-e-business-suite"></a>步驟 3： 建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料
![步驟 4 之 3](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **若要完成的時間：** 15 分鐘  
  
 **目標：** 您現在必須匯入應用程式定義檔，在 Microsoft Office SharePoint Server 中，並在設定應用程式來擷取 Oracle E-business Suite 中的資料。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您應已建立的應用程式定義檔中所述[步驟 2： 建立應用程式定義檔的 Oracle E-business Suite 成品](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md)。  
  
-   Microsoft Single sign-on 服務必須執行。  
  
 
  
##  <a name="SSO"></a>在 SharePoint 中建立的 SSO 應用程式  
 若要從 SharePoint 應用程式存取 Oracle E-business Suite 中的資料，您必須設定 Oracle E-business Suite 使用者對應的 SharePoint 使用者的 SSO 應用程式。 在 SharePoint 中建立的 SSO 應用程式包含下列步驟：  
  
1.  **管理伺服器設定的單一登入**。 在此步驟中，您可以指定使用者帳戶可管理和設定單一登入服務。 您可以在 [管理伺服器設定] 頁面上。 此選項可從 SharePoint 管理中心主控台。 如需這個步驟的詳細資訊，請參閱 「 設定單一登入 Office SharePoint Server 2007 的 」 一節[http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291)。  
  
2.  **管理企業應用程式定義設定**。 在此步驟中，您會設定企業應用程式定義的設定。 您可以從企業應用程式定義 頁面上管理設定。 此選項可從 SharePoint 管理中心主控台。  
  
    1.  在 [管理中心] 的上方導覽列上，按一下**作業**。  
  
    2.  在 [作業] 頁面中**安全性組態**區段中，按一下**管理設定單一登入**。  
  
    3.  在 管理的設定單一登入頁面上，在**企業應用程式定義設定**區段中，按一下**管理企業應用程式定義設定**。  
  
    4.  在 [管理企業應用程式定義] 頁面提供的值**顯示名稱**，**應用程式名稱**，而**連絡電子郵件地址**欄位。  
  
        > [!IMPORTANT]
        >  如**應用程式名稱**欄位中，請確定您指定相同的 SSO 應用程式名稱所指定**SecondarySsoApplicationId**時建立應用程式定義檔中，做為變數中所述[步驟 2： 建立應用程式定義檔的 Oracle E-business Suite 成品](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md)。  
  
    5.  將其他欄位保留為預設值，然後按一下**確定**。  
  
3.  **管理企業應用程式定義的帳戶資訊**。 在此步驟中，您可以啟用個別使用者或群組，從 SharePoint 連接至企業應用程式。 基本上，在此步驟中您對應個別使用者或群組到使用者在 LOB 系統。 您也可以指定要連接至 LOB 系統的認證。 您可以從企業應用程式定義 頁面上的管理帳戶資訊。 此選項可從 SharePoint 管理中心主控台。 如需這個步驟的詳細資訊，請參閱 「 管理企業應用程式定義的帳戶資訊 」 一節[http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291)。  
  
##  <a name="SSP"></a>建立共用的服務提供者  
 共用服務提供者是共用的服務和其支援資源的邏輯群組。 您可以使用 SharePoint 管理中心主控台，以建立 SSP。  
  
 建立 SSP 時，您必須定義的網站 請記住的連接埠號碼和您所建立的網站位址。 您將這個網站來匯入商務資料目錄應用程式定義。  
  
 如需建立 SSP 的詳細資訊，請參閱 「 章概觀： 建立及設定共用服務提供者 」 在[http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119)。  
  
##  <a name="Import"></a>匯入應用程式定義檔  
 您必須立即匯入應用程式定義檔的 ssp。  
  
#### <a name="to-import-the-application-definition-file"></a>若要匯入應用程式定義檔  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側瀏覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。  
  
3.  在**商務資料目錄**區段中，按一下**匯入應用程式定義**。  
  
4.  匯入應用程式定義頁面上，開啟時，請瀏覽至 Employee.xml，選取檔案，然後**開啟**。  
  
5.  按一下 **[匯入]**。  
  
6.  應用程式定義檔匯入成功後，按一下 **確定**。  
  
     因為匯入應用程式定義檔，MS_SAMPLE_EMPLOYEE，建立的應用程式會出現。  
  
     ![在 SharePoint 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/media/b0695720-0113-49dc-8eb6-c685aceada6c.gif "b0695720-0113-49dc-8eb6-c685aceada6c")  
  
## <a name="next-steps"></a>後續步驟  
 現在，您就準備好要建立 Web 組件來建立 SharePoint 網站，以檢視及搜尋會從 Oracle E-business Suite 擷取商務資料。 我們將建立 a:  
  
-   商務資料清單網頁組件顯示 MS_SAMPLE_EMPLOYEE 介面資料表中的員工記錄。 請參閱[案例 1： 使用商務資料清單網頁組件顯示資料](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)。  
  
-   搜尋方塊 」 Web 組件 MS_SAMPLE_EMPLOYEE 介面資料表上執行全文檢索搜尋。 請參閱[案例 2： 使用搜尋方塊 」 Web 組件搜尋](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程： 從 SharePoint 網站上的 Oracle E-business Suite 中呈現的資料](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)