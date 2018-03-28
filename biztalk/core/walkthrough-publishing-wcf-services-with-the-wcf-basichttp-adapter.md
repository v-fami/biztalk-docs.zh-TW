---
title: 逐步解說： 使用發佈 WCF 服務 Wcf-basichttp 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tutorials, publishing
- WCF adapters, tutorials
- publishing, WCF services
- WCF-BasicHttp adapters, tutorials
- publishing, tutorials
- WCF services, publishing
- tutorials, WCF adapters
ms.assetid: 43b76215-9cb0-47ab-a085-c4cf265410f9
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca976d2e965d781de352a010bd4ef8c16e712ffb
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter"></a>逐步解說： 使用發佈 WCF 服務 Wcf-basichttp 配接器
## <a name="introduction"></a>簡介  
 本逐步解說[!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]服務為使用 BizTalk WCF 服務發佈精靈和 Wcf-basichttp 配接器的 BizTalk 協調流程。 BizTalk 協調流程會出現另一個 Web 服務之類的外部用戶端或[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]應用程式中，做為[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務公開[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]使用 Wcf-basichttp 配接器的端點。 Wcf-basichttp 配接器是由傳送配接器和接收配接器所組成。 在此範例會使用只有此配接器的接收端來接收 WCF 服務要求，透過 HTTP 或 HTTPS 通訊協定，從[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]用戶端應用程式。  
  
 Wcf-basichttp 配接器會使用**BasicHttpBinding**繫結至提供的傳輸/通訊協定堆疊實作，與初始版本相容的 Web 服務來服務之間的橋樑[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]功能。 它提供通訊與傳統的 asmx Web 服務和用戶端符合 ws-i-Basic Profile 1.1，使用 HTTP 或 HTTPS 傳輸使用文字編碼。 使用 Wcf-basichttp 配接器不能利用進階的 Web 通訊功能所支援的 WS-* 通訊協定。 如果您需要這麼做，請使用 Wcf-wshttp 配接器。  
  
 本逐步解說會示範如何建立 Wcf-basichttp 接收位置，以做為協調流程發佈[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  您將設定網際網路資訊服務 (IIS) 提供的外掛式主控[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  用戶端應用程式呼叫發佈[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]做為範例的方式可能外部用戶端呼叫已發佈的協調流程[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]網際網路以使用其功能的服務。  
  
 完成此逐步解說之後，您將會瞭解如何執行下列工作：  
  
-   從 Visual Studio 內使用**部署**命令，將部署[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務的本機執行個體的 BizTalk 組件內 BizTalk 協調流程的形式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 從 Visual Studio 的部署會建立包含資源，例如協調流程、 管線、 結構描述的組件中會填入，並將對應至 BizTalk 解決方案中使用的 BizTalk 應用程式。  
  
-   在部署後，BizTalk 協調流程是可用來設定和控制透過[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 在本逐步解說中，您會設定 WCF-BasicHttp 接收位置接受傳送到 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務的內送訊息，而該服務是由 [BizTalk [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務發佈精靈] 所建立的。 接收位置是由 IIS 中 BizTalk 外掛式主控件所裝載，並是用來做為 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務，以取得內送要求。  
  
> [!NOTE]
>  在本逐步解說，您將使用 BizTalk WCF 發佈精靈 」 和/或 BizTalk Web 服務發佈精靈發佈 BizTalk 協調流程和結構描述為[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務使用[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器。 若要將協調流程和結構描述發佈為 Web 服務與 SOAP 配接器中，您使用 **BizTalk WCF 發佈精靈** 和/或 **BizTalk Web 服務發佈精靈**。  
  
## <a name="prerequisites"></a>必要條件  
 執行這個範例中的步驟會確保您的環境會安裝下列必要條件︰  
  
-   建置組件和執行部署程序中，與電腦執行此範例中，這兩種電腦需要 Microsoft Windows Server 2008 SP2 和/或 Windows Server 2008 R2、 Microsoft.NET Framework 4，與 Microsoft BizTalk Server。  
  
-   用來建置組件並執行部署程序的電腦需要 Microsoft Visual Studio。  
  
-   執行此範例的電腦需要[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器和[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]系統管理工具。 這些是 Microsoft BizTalk Server 安裝期間安裝的選項。  
  
-   在電腦上您用來執行管理工作，您必須以成員的使用者帳戶執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組，才能設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]內的應用程式設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此使用者帳戶也必須管理主控件執行個體，並可能需要其他工作的應用程式部署的本機 Administrators 群組成員。  
  
-   需要的任何電腦上[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]功能，完成的單次安裝程序[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]範例[ http://go.microsoft.com/fwlink/?LinkId=135510 ](http://go.microsoft.com/fwlink/?LinkId=135510)。  
  
-   執行範例，並匯入繫結或.msi 檔案的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請確定主機不受信任的主機，或匯入將會失敗。  
  
-   您必須下載逐步解說程式碼，並將它解壓縮到您的電腦。 這個逐步解說是整個屬於[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器逐步解說 」 套件。 您可以下載檔案**WCFAdapterWalkthroughs.exe**從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Developer Center [ http://go.microsoft.com/fwlink/?LinkId=194140 ](http://go.microsoft.com/fwlink/?LinkId=194140)。  
  
### <a name="to-deploy-the-sample-biztalk-solution-biztalkapp"></a>部署範例 BizTalk 方案 BizTalkApp  
  
1.  執行自動解壓縮 **WCFBasicHttpReceiveAdapter.exe** 檔案，並將檔案解壓縮到 **C:\WCFBasicHttpReceiveAdapter** 資料夾。  
  
2.  在 Microsoft Visual Studio 中開啟 **C:\WCFBasicHttpReceiveAdapter\WCFBasicHttpReceiveAdapter.sln** 檔案。  
  
3.  **Microsoft.Samples.BizTalk.WCFBasicHttpReceiveAdapter.BizTalkApp**組件包含[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協調流程、 對應，以及兩個結構描述。 它必須安裝在 GAC 中，將需要強式名稱金鑰檔案才能成立。 以滑鼠右鍵按一下 **[biztalkapp]** 專案，然後按一下 **屬性**。 在 **屬性** 頁面上，按一下 **簽署**, ，然後選取 **簽署組件**。 按一下向下的箭號，在**選擇強式名稱金鑰檔**下拉式清單中，按一下  **\<新增\>**，並輸入`keyfile.snk`中**金鑰檔名稱**文字方塊。 取消核取 **保護我的密碼金鑰檔**, ，然後按一下  **確定**。  
  
4.  在 [方案總管] 中，以滑鼠右鍵按一下 **[biztalkapp]** 專案，然後再按一下 **重建**。  
  
    > [!NOTE]
    >  請勿嘗試 **建置方案**, ，或建置 **WCFClient** 應用程式。 **WCFClient** 尚未準備好要建置在此範例中的點。  
  
5.  展開 **[biztalkapp]**, ，然後開啟 **DeliveryProcess.odx** 檢閱。 在協調流程會採用[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]使用 Wcf-basichttp 配接器透過 HTTP 要求。 它透過使用傳輸地圖修改要求，並送出一次使用相同的回應[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器。  
  
    1.  此協調流程已將發行 Wcf-basichttp 配接器的邏輯要求-回應連接埠。 並會於稍後的步驟中繫結到實體連接埠。  
  
    2.  以滑鼠右鍵按一下最上層節點 **DeliveryProcess.odx** 設計工具的視窗，然後選取 **屬性**。 請確定 **型別修飾詞** 連接埠類型 屬性是 **公用**。  
  
6.  在 方案總管 中，以滑鼠右鍵按一下 **biztalkapp**, ，然後按一下  **屬性**。  
  
    1.  如果未在本機裝載 BizTalk 管理資料庫，修改 **伺服器** 屬性，如果您使用不同的資料庫伺服器。 按一下 [ **部署** ] 索引標籤，然後再修改 **伺服器** 屬性以指向資料庫伺服器。  
  
    2.  請確定 **應用程式名稱** 屬性設定為 **WCFBasicHttpReceiveAdapter**。 這是 BizTalk 解決方案的部署位置的 BizTalk 應用程式的名稱。  
  
    3.  在 方案總管 中，以滑鼠右鍵按一下 **biztalkapp**, ，然後按一下  **部署**。 如果不在本機上部署您可能需要設定為允許遠端連接的 SQL Server。 如需詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=194141 ](http://go.microsoft.com/fwlink/?LinkId=194141)。  
  
### <a name="to-publish-the-sample-orchestration-by-using-the-biztalk-wcf-service-publishing-wizard"></a>若要使用 BizTalk WCF 服務發佈精靈發佈範例協調流程  
  
1.  在此步驟中，您將會採用新部署的協調流程組件，並將其發佈做為 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務。 若要這樣做，請按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk WCF 服務發佈精靈**.  
  
2.  在 **歡迎使用 BizTalk WCF 服務發佈精靈** 頁面上，按一下 **下一步**。  
  
3.  在**WCF 服務類型**頁面上，執行下列動作，以指定的型別[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]發行、 服務和 BizTalk 端點接收[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]訊息，然後再按一下**下一步**:  
  
    1.  選取**服務端點**選項，這表示您將發行[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務從協調流程的組件中。 選取 **Wcf-basichttp** 從 **配接器名稱 （傳輸類型）** 下拉式清單。  
  
    2.  選取**啟用中繼資料端點**核取方塊讓[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]接收由 IIS 裝載的位置發佈其[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務中繼資料。 選取此核取方塊設定**httpGetEnabled**屬性\< **serviceMetadata** \>元素`true`Web.Config 中。這個中繼資料的擷取是發生在 HTTP/GET 要求請求該中繼資料時。 稍後您將使用 SvcUtil.exe 工具來取得這項資料來產生 proxy 類別，用來呼叫用戶端程式碼[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  
  
    3.  選取 **下列應用程式中的建立 BizTalk 接收位置** 選項來建立接收埠與對應至 Wcf-basichttp 配接器的每個產生的.svc 檔案位置。 選擇 BizTalk 應用程式名稱、 **WCFBasicHttpReceiveAdapter**, ，其中的接收埠和位置，將會產生，然後按一下 **下一步**。  
  
         精靈會建立繫結檔案 Binding.XML，以表示相關聯的接收位置。 這個檔案位於 Web 目錄中，可以稍後再透過手動匯入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
        > [!NOTE]
        >  如果您沒有選取部署的 BizTalk 應用程式，在這裡會選取預設的應用程式。  
  
4.  在 **建立 WCF 服務** 頁面上，選取 **BizTalk 協調流程發佈為 WCF 服務**, ，然後按一下  **下一步**。 這將會發佈在下個步驟中指定做為 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務的協調流程。  
  
5.  選取包含要發佈的協調流程的組件。 在 **BizTalk 組件** 頁面上，於 **BizTalk 組件檔案 (\*.dll)**  文字方塊中，按一下  **瀏覽** 瀏覽至 **C:\WCFBasicHttpReceiveAdapter\BizTalkApp\bin\Development** 資料夾中，按兩下 **Microsoft.Samples.BizTalk.WCFBasicHttpReceiveAdapter.BizTalkApp** 包含範例協調流程的組件發行時，按一下  **開啟**, ，然後按一下  **下一步**。  
  
6.  在 **協調流程和連接埠** 頁面上，請確定 **連接埠︰ DeliveryRequestPort** 在頁面上，選取節點，然後再按一下 **下一步**。 選取此節點表示其對應的更高層級節點也會選取。 而連接埠就會以裝載 WCF-BasicHttp 配接器的要求-回應接收位置來發佈。  
  
7.  在**WCF 服務屬性**頁面上，於**目標**命名空間的**WCF 服務**文字方塊中，輸入您想要這個已發佈的 URI[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務使用，並然後按一下 **下一步**。 此逐步解說中，保留預設 URI"**http://tempuri.org/"**的目標命名空間中[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務文字方塊。  
  
8.  在**WCF 服務位置**頁面上，執行下列動作，以指定的位置[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務來建立，然後按一下**下一步**:  
  
    1.  在**位置**文字方塊中，輸入 Web 目錄名稱[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務執行，或按一下**瀏覽**，並選取 Web 目錄。 此逐步解說中，因為組件名稱與虛擬目錄相同，保留預設位置 (**http://localhost/Microsoft.Samples.BizTalk.WCFBasicHttpReceiveAdapter.BizTalkApp**) 中**位置**文字方塊。  
  
    2.  選取 **允許匿名存取 WCF 服務** 選項，然後再按一下 **下一步**。 這個選項會允許對所建立虛擬目錄的匿名存取。 因為本逐步解說會使用傳輸安全性模式與不需要驗證，這個選項就必須選取以允許匿名驗證，此精靈將建立的 Web 應用程式。  
  
9. 在**WCF 服務摘要**頁面上，按一下**建立**建立[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。 這個步驟會建立接收埠，讓指定的協調流程可以透過指定的 Web 目錄而使用。  
  
10. 在 **完成 BizTalk WCF 服務發佈精靈** 頁面上，按一下 **完成**。  
  
### <a name="to-enable-the-sample-biztalk-application"></a>若要啟用範例 BizTalk 應用程式  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**應用程式**，展開**WCFBasicHttpReceiveAdapter**，展開**協調流程**，以滑鼠右鍵按一下**DeliveryProcess**協調流程中，按一下 **屬性**，然後設定繫結資訊，如下所示：  
  
    1.  在 **協調流程屬性** 對話方塊中，按一下 **繫結**, ，然後設定 **主機** 至 **BizTalkServerApplication**。  
  
    2.  在 **協調流程屬性** 對話方塊中選取的接收埠 **DeliveryRequestPort** 繫結。 這個逐步解說中，選取接收埠，BizTalk[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務發佈精靈中先前的程序，建立，然後按一下 **確定**。  
  
3.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**WCFBasicHttpReceiveAdapter**，按一下**啟動**，然後按一下 [**啟動**中**開始應用程式**] 對話方塊。  
  
### <a name="to-configure-the-web-application-hosting-the-published-wcf-service"></a>若要設定裝載所發佈 WCF 服務的 Web 應用程式  
  
1.  按一下  **啟動**, ，指向  **系統管理工具**, ，然後按一下  **網際網路資訊服務 (IIS) 7.0 管理員**。  
  
2.  在 IIS 管理員中，展開 **網站**, ，依序展開 **預設的網站**, ，然後展開 Web 應用程式 **Microsoft.Samples.BizTalk.WCFBasicHttpReceiveAdapter.BizTalkApp** ， **BizTalk WCF 服務發佈精靈** 建立。  
  
3.  建立此服務會在其中執行的應用程式集區。 以滑鼠右鍵按一下 **應用程式集區**, ，按一下  **新增應用程式集區**, ，輸入應用程式集區的名稱，然後按一下 **確定**。  
  
4.  展開 **應用程式集區**, ，以滑鼠右鍵按一下您剛在應用程式集區建立，並選取 **進階設定**。 在下**處理序模型**區段中，輸入擁有存取權的帳戶[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫下**識別**欄位。  
  
5.  在 IIS 管理員中，按一下  **內容檢視**。  在右窗格中，以滑鼠右鍵按一下[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務.svc 檔案， **BizTalk WCF 服務發佈精靈**建立，，然後按一下 **瀏覽**。 此時會開啟 Internet Explorer 顯示一個頁面，表示您已成功建立執行中的 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務。 此頁面還包含完整的 WSDL 位址，而您可以在擷取可用來建立服務之用戶端應用程式的 Proxy 程式碼和組態檔時，複製並使用此位址來搭配服務中繼資料工具 (svcutil.exe) 以執行該擷取作業。  
  
6.  將 SvcUtil.exe 命令列，在 Internet Explorer 上一個步驟中所顯示的頁面上的完整 WSDL 位址複製到剪貼簿。  
  
### <a name="to-create-the-proxy-class-for-the-sample-wcf-client-application-wcfclient"></a>若要建立範例 WCF 用戶端應用程式 WCFClient 的 Proxy 類別  
  
1.  建立 Proxy 類別，讓 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 用戶端範例應用程式可以呼叫 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務。 雖然不需要手動撰寫程式碼是很複雜，因此建議您建立 proxy 的 proxy。 開啟 **Visual Studio 命令提示字元** 並移至 **C:\WCFBasicHttpReceiveAdapter\WCFClient** 資料夾放置 proxy 類別和應用程式組態檔的位置。  
  
2.  貼上 **svcutil.exe** 命令列的完整 WSDL 位址，您在先前的程序中複製，然後按 enter **Enter** 來建立 proxy 類別和應用程式組態檔。 此命令列建立 **BizTalkServiceInstance.cs** proxy 類別和 **output.config** 應用程式組態檔。  
  
3.  在 Visual Studio 中，在 方案總管中以滑鼠右鍵按一下 **WCFClient**, ，指向  **新增**, ，然後按一下  **現有項目**。  
  
4.  在 **加入現有項目**  對話方塊中，瀏覽至 **WCFClient** 資料夾中，選取 **所有檔案 (\*。\*)** 中 **檔案類型** 下拉式清單中，選取 **BizTalkServiceInstance.cs** 和 **output.config** 檔案，然後按一下 **新增**。  
  
5.  **WCFClient** 專案中，展開 **參考**, ，然後確定 **WCFClient** 專案具有 **System.ServiceModel** 做為其中一個參考。  
  
6.  展開 **WCFClient** 專案中，以滑鼠右鍵按一下 **output.config**, ，按一下  **重新命名**, ，然後輸入 **App.config** 讓新的名稱。  
  
7.  按兩下**Program.cs**檢閱如何呼叫發佈[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務使用所產生的 proxy 類別**Svcutil.exe**。 具現化和叫用呼叫[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務似乎是簡化的程式碼使用中的本機呼叫**Microsoft_Samples_BizTalk_WCFBasicHttpReceiveAdapter_BizTalkApp_DeliveryProcess_DeliveryRequestPortClient**類別。 沒有其他程式碼才能進行遠端呼叫[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  
  
8.  在 Visual Studio 中，在 **偵錯** ] 功能表上，按一下 [ **啟動但不偵錯** 執行 WCFClient。 用戶端程式碼建立 DeliveryItem 訊息，並會呼叫[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務，傳遞位址、 ProductID、 和數量。  
  
    ```  
    DeliveryItem deliveryRequestItem = new DeliveryItem();  
    deliveryRequestItem.Address = "One Microsoft Way";  
    deliveryRequestItem.ProductID = "00A120c";  
    deliveryRequestItem.Amount = "300";  
    DeliveryRequestPortClient deliveryProcessClient = new DeliveryRequestPortClient("BasicHttpBinding_ITwoWayAsync");  
    DeliveryItem1 deliveryConfirmation = deliveryProcessClient.Submit(deliveryRequestItem);  
    ```  
  
     如果用戶端成功接收回應訊息回已發佈[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務，它會傳遞確認編號 （串連的 ProductID 和位址） 顯示回應訊息中。  
  
     **送出作業呼叫 deliveryRequestItem**  
  
     **傳回傳遞確認編號︰ 00A120c300One Microsoft Way**  
  
     **請按任意鍵繼續...**  
  
## <a name="see-also"></a>另請參閱  
 [如何使用 BizTalk WCF 服務發佈精靈協調流程發佈為 WCF 服務](../core/publish-orchestrations-as-wcf-services--biztalk-wcf-service-publishing-wizard.md)