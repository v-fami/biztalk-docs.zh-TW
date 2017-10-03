---
title: "步驟 3： 建立應用程式定義檔 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 843fafdb-571e-4da4-ad04-7dc7f23e03ac
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce22a63e8267c36c1306974caa0faa5f9aa6be4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-an-application-definition-file"></a>步驟 3： 建立應用程式定義檔
![步驟 4 之 3](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **若要完成的時間：** 15 分鐘  
  
 Microsoft Office SharePoint Server 中的商務資料目錄功能會公開，並從特定業務 (LOB) 應用程式的資料合併至入口網站。 將此資料合併到您的入口網站，您必須建立 Microsoft Office SharePoint Server 可以使用應用程式定義檔。  
  
 在此步驟中，您可以使用 商務資料目錄定義編輯器工具，適用於 Microsoft Office SharePoint Server 2007 SDK，建立商務資料目錄應用程式定義檔。 這個定義檔描述回應配接器的 EchoGreetings 方法，並將在稍後步驟中用來啟用 SharePoint 與配接器通訊。  
  
 您正在建立 Microsoft Office SharePoint Server 應用程式的目的是讓您叫用回應配接器的 EchoGreetings 方法，並使用 SharePoint Web 組件將回應傳回。  
  
## <a name="prerequisites"></a>必要條件  
 您應已完成[步驟 2： 部署 Web 專案](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md)。 您也必須可以存取到商務資料目錄定義編輯器，它會安裝為 Microsoft Office SharePoint Server 2007 SDK 的一部分。 您可以下載從 SDK [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130)。  
  
## <a name="creating-an-application-definition-file"></a>建立應用程式定義檔  
 本主題提供逐步指示來建立 SharePoint 商務資料目錄連接使用 IIS 中裝載 WCF 配接器的應用程式定義檔。  
  
#### <a name="to-connect-to-the-wcf-adapter-service-and-create-entities"></a>連接到 WCF 配接器服務，並建立實體  
  
1.  從**開始 功能表**，指向 **所有程式**，然後按一下  **Microsoft 商務資料目錄定義編輯器**。  
  
2.  在工具列上，按一下  **LOB 系統**。  
  
3.  在 [新增 LOB 系統] 視窗中，按一下**連接到 Webservice**。  
  
4.  在**URL**方塊中，輸入 WCF 服務的 URL。 這個 URL 必須以下列格式：`https://machinename/EchoWeb/EchoOutboundContract.svc?wsdl`  
  
5.  按一下 **[連接]**。  
  
6.  若要查看可用的作業，請按一下**新增 Web 方法** 索引標籤。您應該會看到 EchoGreetings 方法。 將方法拖曳至設計介面。  
  
7.  按一下 **[確定]**。  
  
8.  在**輸入 LOB 系統的名稱**對話方塊內輸入名稱**LOB 系統名稱**方塊。 針對此範例中，輸入**EchoWSLOB**，然後按一下 **確定**。  
  
9. 展開**EchoWSLob**  節點，然後展開**實體**節點。 選取**Entity0**並在屬性窗格中輸入**EchoGreetings**做為值**名稱**屬性。  
  
     ![實體名稱](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/942e7853-451e-4cf5-8884-09fb7d8dc19d.gif "942e7853-451e-4cf5-8884-09fb7d8dc19d")  
  
## <a name="specify-user-name-and-password-headers-for-the-method"></a>指定使用者名稱和密碼標頭方法  
 在呼叫的 WCF 配接器時，您可能必須提供使用者認證將會傳遞至 LOB 系統。 在[步驟 1： 建立 Web 專案中使用配接器服務開發精靈](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md)，您回應配接器設定為需要 MyUserHeader 和 MyPassHeader 欄位中，提供使用者名稱和密碼資訊。 您現在必須使用這個應用程式定義檔相同的欄位名稱。  
  
#### <a name="to-specify-user-name-and-password-headers"></a>若要指定使用者名稱和密碼標頭  
  
1.  在 中繼資料物件 窗格中，依序展開**EchoGreetings**  節點，然後展開**方法**節點。  
  
2.  按一下**EchoGreetings**節點並在 [屬性] 窗格中，按一下省略符號**（...）**按鈕**屬性**欄位。  
  
3.  在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在**名稱**欄位屬性 窗格的 型別**HttpHeaderUserName**。  
  
     ![指定使用者名稱標頭欄位](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/8da4d1b7-0792-407a-ba93-ba749138dd14.gif "8da4d1b7-0792-407a-ba93-ba749138dd14")  
  
4.  在**PropertyValue**欄位中，輸入**MyUserHeader**。  
  
5.  按一下**新增**，並在屬性窗格中輸入**HttpHeaderPassword** [名稱] 欄位中，然後輸入**MyPassHeader**如**PropertyValue**欄位。  
  
6.  按一下 **[確定]**。  
  
## <a name="set-up-single-sign-on-for-connecting-to-the-echo-adapter"></a>連接到回應配接器設定單一登入設定  
 SharePoint 會使用從單一登入的資訊以驗證值填入 MyUserHeader 和 MyPassHeader。 若要以單一登入連結此應用程式定義檔，您必須提供 SecondarySsoApplicationId。  
  
#### <a name="to-set-the-secondaryssoapplicationid-property"></a>若要設定 SecondarySsoApplicationId 屬性  
  
1.  在 中繼資料物件 窗格中，依序展開**EchoWSLOB**  節點，然後展開**執行個體**節點。  
  
2.  按一下**EchoWSLOB_Instance**，在 [屬性] 窗格中，按一下省略符號**（...）**按鈕**屬性**欄位。  
  
3.  在 [PropertyView 集合編輯器] 視窗中，按一下**新增**，然後在 [屬性] 窗格中，輸入**SecondarySsoApplicationId**中**名稱**欄位。  
  
4.  在**PropertyValue**欄位中，輸入**EchoSSO**。  
  
     ![設定 SecondarySsoApplicationId](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/68e6be61-77af-46b1-8ff0-b8538c526228.gif "68e6be61-77af-46b1-8ff0-b8538c526228")  
  
5.  按一下 **[確定]**。  
  
## <a name="create-input-filters-and-default-values"></a>建立輸入篩選器和預設值  
 應用程式定義檔必須是可接受使用者輸入可傳遞至 Web 服務。 若要這麼做，您必須執行下列的工作集：  
  
#### <a name="to-create-a-filter-and-map-it-to-the-greeting-parameter"></a>若要建立篩選器，並將它對應至問候語參數  
  
1.  在 中繼資料物件 窗格中，依序展開**EchoWSLOB**  節點，然後展開**方法**節點。  
  
2.  展開**EchoGreetings**方法，以滑鼠右鍵按一下**篩選**，然後按一下 **加入篩選條件**。  
  
3.  在 [屬性] 窗格中，輸入**問候語**中**名稱**欄位。  
  
     ![設定篩選器名稱](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/74036b9e-7eec-4156-b238-840e67a2f00c.gif "74036b9e-7eec-4156-b238-840e67a2f00c")  
  
4.  在 中繼資料物件 窗格中，依序展開**EchoWSLOB**  節點，然後展開**方法**節點  
  
5.  展開**EchoGreetings**方法，然後展開**參數**節點。  
  
6.  展開**問候語**] 節點，然後展開 [第二個**問候語**節點。  
  
7.  按一下**greetingText**  節點，然後在 屬性 窗格中，選取**問候語**從**FilterDescriptor**清單。  
  
#### <a name="to-create-a-finder-method-instance-for-the-echogreetings-method"></a>若要建立 Finder 方法執行個體 EchoGreetings 方法  
  
1.  在 中繼資料物件 窗格中，依序展開**EchoWSLOB**  節點，然後展開**方法**節點。  
  
2.  展開**EchoGreetings**方法，以滑鼠右鍵按一下**執行個體**，然後按一下 **新增方法執行個體**開啟 建立方法執行個體 視窗。  
  
3.  在 [建立方法執行個體] 視窗中，按一下**Finder**的**方法執行個體類型**，然後選取**傳回**的**傳回 TypeDescriptor**.  
  
     ![建立方法執行個體](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a932a7a0-c004-46bf-af5c-cc7392bafa43.gif "a932a7a0-c004-46bf-af5c-cc7392bafa43")  
  
4.  按一下 **[確定]**。  
  
5.  在 [屬性] 窗格中，輸入**EchoGreetings_Instance**中**名稱**欄位。  
  
#### <a name="to-set-default-parameters"></a>若要設定預設參數  
  
1.  在 中繼資料物件 窗格中，依序展開**EchoWSLOB**  節點，然後展開**方法**節點。  
  
2.  展開**EchoGreetings**方法，然後展開**執行個體**節點。  
  
3.  選取**EchoGreetings_Instance**方法執行個體，並在 [屬性] 窗格中，按一下省略符號按鈕 （...） 中的**DefaultValues**欄位。  
  
4.  在 [編輯] 視窗中，依序展開**問候語**] 節點，然後展開 [第二個**問候語**節點。 展開**名稱**節點，直到完全顯示樹狀結構。  
  
5.  在 [編輯] 視窗中設定欄位值，如下所示：  
  
    |設定此項|為此值|  
    |--------------|-------------|  
    |**id**|GUID 值，例如 27829ed4-583a-40 c 4 ad87 fb8cdd9dc98d。|  
    |**sentDateTime**|目前的日期和時間，例如 05/15/08 上午 9:12|  
    |**名字**|第一個|  
    |**middleName**|Middle|  
    |**lastName**|最後一個|  
  
     ![預設參數](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/70250957-9680-48ce-8bce-420ff18bb47a.gif "70250957-9680-48ce-8bce-420ff18bb47a")  
  
6.  按一下 [ **關閉**]。  
  
### <a name="to-export-the-application-definition-file"></a>若要匯出應用程式定義檔  
  
1.  在 [中繼資料物件] 窗格中，以滑鼠右鍵按一下**EchoWSLOB**節點，然後再按一下**匯出**。  
  
2.  將檔案儲存為 EchoWS.xml。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 商務資料目錄定義編輯器工具具有用於建立應用程式定義檔，可以匯入 Microsoft Office SharePoint Server 2007 以啟用您在 IIS 中裝載的配接器的連線。  
  
## <a name="next-steps"></a>後續步驟  
 您現在必須建立在此步驟中建立的應用程式定義檔為基礎的 SharePoint 應用程式。 請參閱[步驟 4： 建立 Sharepoint 應用程式存取配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-create-a-sharepoint-application-to-access-the-adapter.md)如需相關指示。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 3： 裝載在 IIS 中的回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)