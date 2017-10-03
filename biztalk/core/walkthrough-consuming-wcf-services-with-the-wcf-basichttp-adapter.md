---
title: "逐步解說： 使用 Wcf-basichttp 配接器的 WCF 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d280198-ba55-4937-91c9-19d6d0ed3194
caps.latest.revision: "49"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c54646d106abe1824ce39de5a550f5f591bae882
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-consuming-wcf-services-with-the-wcf-basichttp-adapter"></a>逐步解說： 使用 Wcf-basichttp 配接器的 WCF 服務
  
> [!NOTE]
>  如需配接器的詳細資訊，請參閱[配接器在 BizTalk Server](../core/adapters-in-biztalk-server.md)。  
  
## <a name="introduction"></a>簡介
  
 在本逐步解說，您將使用[!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]服務裝載在網際網路資訊服務 (IIS) 使用 BizTalk 傳訊和 Wcf-basichttp 傳送配接器。 此配接器使用**BasicHttpBinding**繫結，以提供與 Web 服務，做為 Microsoft 之間的橋接器的舊版本相容的傳輸/通訊協定堆疊實作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]這項功能。 協調流程可以繫結至傳送埠使用[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器呼叫[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務，並且使用其功能，其邏輯商務程序內。  
  
 Wcf-basichttp 配接器是由傳送配接器和接收配接器所組成。 在此範例會使用僅此配接器的傳送端進行透過 HTTP 通訊協定的 WCF 服務要求[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  請求-回應傳送埠，傳送配接器傳送給[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務，並收到傳回的結果回應。  相反地，[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]接收配接器可以讓[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]要發行和從外部呼叫的協調流程[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]用戶端應用程式。 請參閱[發佈 WCF 服務](../core/publishing-wcf-services.md)如需詳細資訊。  
  
 完成此逐步解說之後，您將會瞭解如何執行下列工作：  
  
-   從[!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[vs2010](../includes/vs2010-md.md)]，使用**部署**命令來部署組件包含[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案和[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務的本機執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 這樣會建立有組件填入其中的 BizTalk 應用程式。  
  
-   從[!INCLUDE[vs2010](../includes/vs2010-md.md)]，使用**BizTalk WCF 服務使用精靈**產生[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]結構描述和類型使用時所需要[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。 您可以使用，並繫結至邏輯連接埠，就會一併產生空白的協調流程。 此協調流程會編譯和部署以及結構描述和類型。 但協調流程的工作流程處理是空白這裡，未在此範例中使用，因為這是只單純[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳訊實例。  
  
-   從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，設定使用 Wcf-basichttp 傳送埠以內容為基礎的路由。 您將設定**SOAPAction**標頭的目標[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務預期收到。  
  
-   從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，設定篩選條件運算式傳送任何 SOAP 錯誤訊息[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務可傳送到輸出資料夾。  
  
-   從網際網路資訊服務 (IIS) 管理員中設定 Web 應用程式裝載[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務來公開它的中繼資料。 啟用之後， **BizTalk WCF 服務使用精靈**可以取得此中繼資料來產生型別和結構描述存取[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此範例中的步驟會確認您的環境會安裝下列先決條件：  
  
-   建置組件，並執行部署程序的電腦和執行範例的電腦需要 Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，Microsoft [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]，與 Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。  
  
-   用來建置組件並執行部署程序的電腦需要 Microsoft [!INCLUDE[vs2010](../includes/vs2010-md.md)]。  
  
-   執行此範例的電腦需要[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器和[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]系統管理工具。 這些是 Microsoft 的安裝期間安裝的選項[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。  
  
-   在電腦上您用來執行管理工作，您必須以成員的使用者帳戶執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組，才能設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]內的應用程式設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此使用者帳戶也必須為管理主控件執行個體和其他工作可能需要的應用程式部署的本機系統管理員群組的成員。  
  
-   需要的任何電腦上[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]功能，完成的單次安裝程序[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]範例[http://go.microsoft.com/fwlink/?LinkId=135510](http://go.microsoft.com/fwlink/?LinkId=135510)。  
  
-   執行範例，並匯入繫結或.msi 檔案的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請確定主機不受信任的主機，或匯入將會失敗。  
  
-   您必須下載的逐步解說程式碼，並將它解壓縮到您的電腦。  這個逐步解說是整個屬於[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器逐步解說 」 套件。 您可以下載檔案**WCFAdapterWalkthroughs.exe**從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Developer Center[http://go.microsoft.com/fwlink/?LinkId=194140](http://go.microsoft.com/fwlink/?LinkId=194140)。  
  
## <a name="deploy-the-sample-wcf-service"></a>部署範例 WCF 服務  
  
1.  執行自動解壓縮**WCFBasicHttpSendAdapter.exe**檔案，並將檔案解壓縮到**C:\WCFBasicHttpSendAdapter**資料夾。  
  
2.  開啟**C:\WCFBasicHttpSendAdapter\WCFBasicHttpSendAdapter.sln**中[!INCLUDE[vs2010](../includes/vs2010-md.md)]。  
  
3.  在 [方案總管] 中，展開**BasicHttpWCFServiceConsuming**專案。 這個專案是[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]將傳送埠所呼叫的服務。 它會在受管理的主機環境中使用 Internet Information Services (IIS) 裝載。 在 IIS 中裝載使用訊息型啟用來管理啟用和服務的存留期。 展開**App_Code**，然後開啟**OrderProcess.cs**檢閱。 這[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務接收訂單要求訊息，透過**OrderRequest**方法。 OrderProcess.cs 檔案包含的介面 defition 和實作[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。 它只會傳回訂單回應訊息，透過**OrderResponse**方法。  
  
4.  檢閱 [orderprocess.svc] 檔案。 它只包含一個線條用來告知 IIS 以啟用用戶端應用程式的服務。  **@ServiceHost** 屬性會用來裝載服務是中的擴充點[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]程式設計模型。 使用處理站模式**ServiceHostFactory**建立的執行個體**ServiceHost**與執行個體[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]處理傳入要求的服務。 具現化這個執行個體根據**ServiceBehaviorAttribute.ConcurrencyMode**屬性，決定服務是否支援單一執行緒、 多重執行緒或可重新進入的呼叫。 具現化也由**ServiceBehavior.InstanceMode**屬性，決定如果只有一個執行個體將提供所有呼叫端 (singleton)，如果一個執行個體將會建立每個呼叫 （無狀態），或一個執行個體將會建立每個工作階段 （可設定狀態）。  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWcfServiceConsuming.OrderProcessServiceType" %>  
    ```  
  
5.  在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，在 [方案總管] 中，開啟**Web.config**檢閱。 在 IIS 中裝載時[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]裝載於主控台應用程式時，使用 Web.config 檔案而不做為 app.config 檔案設定服務。  
  
    -   請確定**httpGetEnabled**屬性\< **serviceMetaData**> 元素會設定為`true`以便**BizTalk WCF 服務使用精靈**可以取用的服務中繼資料。  
  
    -   請確定**模式**屬性\<**安全性**> 元素會設定為**無**。 因為本逐步解說使用**無**安全性模式中，Web 應用程式裝載此服務必須設定為允許匿名存取。  
  
6.  因為**Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWcfServiceConsuming**該組件必須安裝在 GAC 中，它將需要強式名稱金鑰檔案，以完成部署程序。 以滑鼠右鍵按一下**BasicHttpWcfServiceConsuming**專案，然後再按一下**屬性**。 在**屬性**頁面上，按一下**簽署**，然後選取**簽署組件**。 按一下向下的箭號，在**選擇強式名稱金鑰檔**下拉式清單中，按一下  **\<新增 >**，並輸入`keyfile.snk`中**金鑰檔名稱**文字方塊.  取消核取**保護我的密碼金鑰檔**，然後按一下 **確定**。  
  
7.  在 方案總管 中，以滑鼠右鍵按一下**BasicHttpWcfServiceConsuming**，然後按一下 **重建**。  
  
8.  使用 Windows 檔案總管 中，將複製的內容**C:\WCFBasicHttpSendAdapter\BasicHttpWCFServiceConsuming**至**C:\InetPub\wwwroot**資料夾。  
  
9. 將 Web 應用程式設定為裝載 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務，如下所示：  
  
    1.  按一下**啟動**，指向 **系統管理工具**，然後按一下 **網際網路資訊服務 (IIS) 管理員**。  
  
    2.  建立此服務會在其中執行的應用程式集區。 以滑鼠右鍵按一下**應用程式集區**，按一下 **新增應用程式集區...**，輸入應用程式集區的名稱，然後按一下**確定**。  
  
    3.  展開**應用程式集區**，以滑鼠右鍵按一下您剛在應用程式集區建立，並選取**進階設定**。 在下**處理序模型**區段中，輸入擁有存取權的帳戶[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫下**識別**欄位。  
  
    4.  展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下**BasicHttpWCFServiceConsuming**，然後按一下 **轉換成應用程式**建立此 Web 應用程式[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  
  
    5.  在**轉換成應用程式**對話方塊中，按一下 **選取**要選取稍早建立的應用程式集區，然後按一下**確定**。  
  
    6.  在 [功能檢視] 中按一下**驗證**圖示，並確定**匿名驗證**選項**啟用**。 這種情況支援[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務使用**無**安全性模式。  
  
10. 測試已發佈[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務，如下所示：  
  
    1.  在 [IIS 管理員] 中，展開**網站**，然後展開**BasicHttpWCFServiceConsuming**。  
  
    2.  在 IIS 管理員 中，在右窗格中，以滑鼠右鍵按一下**orderprocess.svc**，然後按一下 **瀏覽**。 這會開啟 Internet Explorer 顯示**OrderProcessServiceType 服務**頁面，表示您已成功建立執行[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。 此頁面還包含完整的 WSDL 位址，可讓您複製和搭配服務中繼資料工具 (svcutil.exe) 用來建立 Proxy 程式碼，以及一個組態檔，可用來開發服務的用戶端應用程式。  
  
    3.  將系統的完整 WSDL 位址複製到剪貼簿。 請勿複製**"svcutil.exe"**部分： **http://localhost/BasicHttpWcfServiceConsuming/OrderProcess.svc?wsdl**  
  
## <a name="add-the-schemas-and-types-for-the-wcf-basichttp-adapter-to-the-sample-biztalk-application"></a>將結構描述和 Wcf-basichttp 配接器的類型加入至範例 BizTalk 應用程式  
  
1.  因為配接器會呼叫[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務的方法需要從結構描述和類型如何呼叫該服務使用中繼資料的資訊。 **[Biztalkapp]**提供要使用的成品[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。 在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**[biztalkapp]**，按一下**新增**，然後按一下 **新增產生的項目**。  
  
2.  在**新增產生的項目**對話方塊中，於**範本**區段中，選取**取用 WCF 服務**，然後按一下 **新增**。  
  
3.  在**歡迎使用 BizTalk WCF 服務使用精靈**頁面上，按一下**下一步**。 此精靈將讀取中繼資料，並建立結構描述和類型。  
  
4.  在**中繼資料來源**頁面上，選取**中繼資料交換 (MEX) 端點**選項來取用中繼資料從 URL 已複製到剪貼簿中的上一個程序，然後按一下  **下一步**。  
  
5.  在**中繼資料端點**頁面上，您在前述程序中複製的完整 WSDL 位址貼上**中繼資料位址**下拉式清單，然後按一下**取得**取得中繼資料文件中的範例[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。 取得中繼資料可讓**下一步** 按鈕。 按 **[下一步]** ，繼續進行。  
  
6.  在**匯入 WCF 服務中繼資料摘要**頁面上，檢閱您的設定。 此對話方塊會顯示要匯入之中繼資料的命名空間、XSD 和 WSDL 摘要。 它也會顯示協調流程 (.odx)、 繫結 (.xml)，以及結構描述 (.xsd) 檔案將寫入其中的匯入程序。 按一下**匯入**建立 BizTalk 成品和使用範例使用的型別[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  
  
7.  在**完成 BizTalk WCF 服務使用精靈**頁面上，按一下**完成**。  
  
8.  在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，在 方案總管**BizTalk WCF 服務使用精靈**會產生下列檔案：  
  
    -   協調流程檔案**OrderProcessServiceType.odx**。 在此協調流程中有任何工作流程階段。 不過，無法新增到它，然後將它繫結至邏輯連接埠取用[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。 它包含重要的 BizTalk 類型，例如連接埠類型和多部分訊息類型，此範例中使用。 若要檢視這項資訊，請按兩下**OrderProcessServiceType.odx**協調流程。 按一下**檢視**，按一下 **其他視窗**，然後按一下**協調流程檢視**。 展開**類型**，依序展開**連接埠類型**，然後展開**IOrderProcess**。 您會看到**送出**方法。 展開該方法，您會看到**OrderRequest**和**OrderResponse**連接埠類型。 按一下每個連接埠類型並檢視其**描述**屬性瀏覽器和不同的 WSDL，請參閱中的欄位輸入和輸出訊息。 按一下**多部分訊息類型**並檢視**OrderRequest**和**OrderResponse**多部分訊息類型。 按一下其**描述**欄位，並檢視其 WDSL 訊息的每個訊息類型的名稱。  
  
    -   會產生兩個結構描述檔案。 第一個結構描述檔案 (**OrderProcessServiceType_biztalk_WCF_basichttpsendadapter_basichttpWCFserviceconsuming.xsd**) 定義的訊息類型範例[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務所使用。 它會使用**OrderID**欄位中都**OrderRequest**和**OrderResponse**呼叫。  
  
    -   第二個結構描述檔案 (**OrderProcessServiceType_schemas_microsoft_com_2003_10_Serialization.xsd**) 會匯出[DataContractSerializer](http://go.microsoft.com/fwlink/?LinkId=81722)類型、 元素和屬性命名空間、 http://schemas.microsoft.com/2003/10/Serialization/。  
  
    -   產生兩個繫結檔案，這將會稍後可用於建立 BizTalk 應用程式： **OrderProcessServiceType.BindingInfo.xml**和**orderprocessservicetype_custom.bindinginfo.xml 這**。 在一般情況下，您通常會使用非自訂繫結檔案。 但在某些罕見的情況下，您有使用自訂繫結檔案的自訂繫結項目。 自訂繫結項目會建立傳送埠的應用程式。 按兩下**OrderProcessServiceType.BindingInfo.xml**檔案，並搜尋**SendPort**定義行，以及檢閱檔案將會建立，當您匯入此繫結的傳送埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
        ```  
        <SendPort Name="WCFSendPort_OrderProcessServiceType_ServiceEndpoint" …  >  
        ```  
  
    -   這些檔案來進行傳送連接埠使用[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器使用範例[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務中繼資料中所述。  
  
## <a name="deploy-the-sample-biztalk-solution-biztalkapp"></a>部署範例 BizTalk 方案 BizTalkApp  
  
1.  部署 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式，如下所示：  
  
    1.  在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**[biztalkapp]**，然後按一下 **屬性**。  
  
    2.  在**專案設計工具**視窗中，按一下 **部署**索引標籤，然後再變更**伺服器**屬性，如果您使用不同的資料庫伺服器的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理資料庫。 請確認應用程式的名稱**WCFBasicHttpSendAdapter**。  
  
    3.  在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**[biztalkapp]**，然後按一下 **重建**。  
  
    4.  在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**[biztalkapp]**，然後按一下 **部署**。  這會將 Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BizTalkApp 組件部署至 GAC 中，並要成品[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]名為應用程式**WCFBasicHttpSendAdapter**。  
  
2.  依照下列說明設定 BizTalk 應用程式中的 WCF-BasicHttp 傳送埠：  
  
    1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
    2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk 群組**，依序展開**應用程式**，以滑鼠右鍵按一下**WCFBasicHttpSendAdapter**，指向**匯入**，然後按一下 **繫結**。  
  
    3.  在**匯入繫結**對話方塊中，移至**C:\WCFBasicHttpSendAdapter\BizTalkApp**資料夾中，選取**OrderProcessServiceType.BindingInfo.xml**，然後按一下**開啟**。 這是其中一個所建立的繫結檔案**BizTalk WCF 服務使用精靈**之前。 這會建立**WCFSendPort_OrderProcessServiceType_ServiceEndpoint**傳送埠。  
  
    4.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**WCFBasicHttpSendAdapter**，然後按一下 **傳送埠**。  
  
    5.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，在右窗格中，按兩下**WCFSendPort_OrderProcessServiceType_ServiceEndpoint**，這是藉由匯入繫結檔案[Orderprocessservicetype.bindinginfo.xml]。 這會開啟**傳送埠屬性** 對話方塊。  
  
    6.  在**傳送埠屬性**對話方塊中，按一下 **設定**。  
  
    7.  在**一般**索引標籤上檢閱**Address(URI)**欄位**http://localhost/BasicHttpWcfServiceConsuming/OrderProcess.svc**。 這是位址[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]Wcf-basichttp 配接器會呼叫的 IIS 中裝載的服務。  
  
    8.  檢閱的內容**SOAP 動作標頭/動作**文字方塊：  
  
        ```  
        <BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
          <Operation Name="Submit" Action="http://Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWcfServiceConsuming/IOrderProcess/Submit" />  
        </BtsActionMapping>  
        ```  
  
         此欄位指出傳出的 SOAP HTTP 要求訊息的目的。 這裡會送出在呼叫作業 IOrderProcess 介面 Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWcfServiceConsuming 命名空間中。  
  
        > [!NOTE]
        >  繫結檔**BizTalk WCF 服務使用精靈**會使用產生的動作對應格式**StaticAction**屬性。 使用時針對 WCF 傳送配接器傳送訊息至 WCF 服務內容架構路由，您需要設定**BTS。作業**動作對應格式用於內容為基礎的路由之欄位的管線元件中的屬性。 或者，您可以針對以內容為基礎的路由使用單一動作格式。 在本逐步解說，您可以使用單一動作格式。 如需單一動作格式和動作對應格式的詳細資訊，請參閱**Wcf-basichttp 傳輸屬性對話方塊、 傳送、 一般** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
    9. 按一下**確定**兩次以返回[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
3.  建立靜態單向接收埠和接收位置的檔案。 接收埠是一或多個接收位置的邏輯容器。 這是您將放置範例[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]訊息，將會收取的 File 配接器，並再傳送至[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  
  
    1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**WCFBasicHttpSendAdapter**，以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下  **單向接收埠**。  
  
    2.  在**接收埠屬性**對話方塊中，於**名稱**文字方塊中，輸入`WCFBasicSendAdapter.ReceivePurchaseOrder`，然後按一下**確定**。  
  
    3.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**WCFBasicHttpSendAdapter.ReceivePurchaseOrder**，指向 **新增**，然後按一下 **接收位置**.  
  
    4.  在**接收位置屬性**對話方塊中，於**名稱**文字方塊中，輸入`WCFBasicSendAdapter.ReceivePurchaseOrder.FILE`。  
  
    5.  在**接收位置屬性**對話方塊中，於**傳輸**區段旁邊**類型**，選取**檔案**從下拉式清單中，然後按一下 **設定**。  
  
    6.  在**FILE 傳輸屬性**對話方塊**一般**索引標籤的**接收資料夾**文字方塊中，輸入`C:\WCFBasicHttpSendAdapter\OrderRequestIn`，然後按一下 **確定**.  
  
    7.  在**接收位置屬性**對話方塊中，按一下 **確定**。  
  
4.  建立篩選器將訊息路由至 Wcf-basichttp 傳送檔案中的連接埠會接收您在上一個步驟中建立的位置。 連接埠相關聯的篩選條件就像是 SQL"where"子句中，如果評估為 true，訊息會指定該通訊埠。  
  
    1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**WCFBasicHttpSendAdapter**，按一下 **傳送埠**，然後按兩下**WCFSendPort_OrderProcessServiceType_ServiceEndpoint**。  
  
    2.  在**傳送埠屬性**對話方塊**篩選**索引標籤上，選取**BTS。ReceivePortName**中**屬性**欄位中，輸入`WCFBasicSendAdapter.ReceivePurchaseOrder`中**值**欄位，，然後按一下**確定**。 這個篩選條件運算式會路由傳送內送訊息從 WCFBasicSendAdapter.ReceivePurchaseOrder 接收這個 Wcf-basichttp 傳送埠的連接埠。  
  
5.  建立範例應用程式的兩個檔案傳送埠。 第一個傳送埠將訊息檔案的連接埠的輸出回應[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。 第二個傳送埠用來處理錯誤訊息從傳送[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務針對用戶端。  
  
    1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**WCFBasicHttpSendAdapter**，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下  **靜態單向傳送埠**。  
  
    2.  在**傳送埠屬性**對話方塊中，於**名稱**文字方塊中，輸入`WCFBasicSendAdapter.SendPurchaseOrder.FILE`。  
  
    3.  在**傳送埠屬性**對話方塊中，於**傳輸**區段類型，選取旁的**檔案**從下拉式清單，然後按一下**設定**.  
  
    4.  在**FILE 傳輸屬性**對話方塊**一般**索引標籤的**目的地資料夾**文字方塊中，輸入`C:\WCFBasicHttpSendAdapter\OrderResponseOut`，然後按一下  **確定**.  
  
    5.  在**傳送埠屬性**對話方塊**篩選**索引標籤上，選取**BTS。MessageType**中**屬性**欄位中，輸入`http://Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWCFServiceConsuming#OrderResponse`中**值**欄位來指定從範例回應訊息類型[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務，以及然後按一下 **確定**。 這個篩選條件運算式會從範例回應訊息路由傳送[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務，此檔案傳送埠。 傳送埠訂閱 OrderResponse 類型的訊息篩選條件屬性中指定該型別。 這是從回應訊息的訊息類型[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  
  
    6.  在**傳送埠屬性**對話方塊中，按一下 **確定**。  
  
    7.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**WCFBasicHttpSendAdapter**，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下  **靜態單向傳送埠**。  
  
    8.  在**傳送埠屬性**對話方塊中，於**名稱**文字方塊中，輸入`WCFAdapterErrorSend.FILE`。  
  
    9. 在**傳送埠屬性**對話方塊中，於**傳輸**區段旁邊**類型**，選取**檔案**從下拉式清單中，然後按一下**設定**。  
  
    10. 在**FILE 傳輸屬性**對話方塊**一般**索引標籤的**目的地資料夾**文字方塊中，輸入`C:\WCFBasicHttpSendAdapter\WCFAdapterErrorOut\`，然後按一下  **確定**.  
  
    11. 在**傳送埠屬性**對話方塊**篩選**索引標籤上，選取**WCF。IsFault**中**屬性**欄位中，輸入`True`中**值**欄位，，然後按一下**確定**。 應用程式中發生例外狀況或錯誤可以偵測檢查**WCF。IsFault**回呼叫端所傳送之訊息的屬性。 這個屬性會設定為**True**如果所傳送訊息的 SOAP 錯誤訊息。 這個篩選條件運算式會路由傳送來自範例錯誤訊息[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務，此檔案傳送埠。  
  
6.  指定範例應用程式的主控件名稱和繫結，如下所示：  
  
     在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**WCFBasicHttpSendAdapter**，依序展開**協調流程**，以滑鼠右鍵按一下**Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BizTalkApp.OrderProcessServiceTypeClient**協調流程中，按一下 **屬性**，按一下 **繫結**，設定**主機**至**[biztalkserverapplication]**，然後按一下 **確定**儲存設定。  
  
## <a name="test-the-sample-solution-with-the-wcf-basichttp-send-adapter"></a>測試範例解決方案使用 Wcf-basichttp 傳送配接器  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**WCFBasicHttpSendAdapter**，然後按一下 **啟動**。  
  
2.  在**啟動**對話方塊中，按一下 **啟動**。  
  
3.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**平台設定**，依序展開**主控件執行個體**，以滑鼠右鍵按一下**BizTalkServerApplication**或另一個適當的主控件執行個體，，然後按一下 **重新啟動**。  
  
4.  開啟命令提示字元，輸入**iisreset**回收 IIS 及其相依的服務，然後按下 ENTER。  
  
5.  在命令提示字元中，複製**C:\WCFBasicHttpSendAdapter\TestData\WCFBasicSendAdapter.OrderRequest.Sample.xml**至**C:\WCFBasicHttpSendAdapter\OrderRequestIn**資料夾。 此訊息會路由至雙向**WcfSendPort_OrderProcessServiceType_ServiceEndpoint**靜態請求-回應傳送埠。  傳送端的此雙向傳送埠呼叫**送出**方法[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]IIS 中裝載的服務。 結果會傳回到回應連接埠的**WcfSendPort_OrderProcessServiceType_ServiceEndpoint**傳送埠。  **WCFBasicSendAdapter.SendPurchaseOrder.FILE**傳送連接埠的訊息類型時，將會觸發的訂閱**http://Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWCFServiceConsuming#OrderResponse**。它會取得已成功處理的訊息，並寫出至**C:\WCFBasicHttpSendAdapter\OrderResponseOut**資料夾。  
  
6.  請檢查**C:\WCFBasicHttpSendAdapter\OrderResponseOut**來自回應訊息的資料夾[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  
  
7.  在命令提示字元中， **C:\WCFBasicHttpSendAdapter\TestData\WCFBasicSendAdapter.OrderRequest.Invalid.xml**至**C:\WCFBasicHttpSendAdapter\OrderRequestIn**資料夾。 此訊息包含無效的命名空間，因此 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務會傳回錯誤訊息。  
  
8.  請檢查**C:\WCFBasicHttpSendAdapter\WCFAdapterErrorOut**包含錯誤訊息，從 XML 檔案的資料夾[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。 查看\< **g**> 欄位顯示為無效的訊息本文的錯誤訊息的原因。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 使用發佈 WCF 服務 Wcf-basichttp 配接器](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)   
 [如何使用 BizTalk WCF 服務使用精靈來取用 WCF 服務](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)   
 [指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md)