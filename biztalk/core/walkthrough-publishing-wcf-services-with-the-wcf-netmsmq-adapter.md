---
title: "逐步解說： 使用發佈 WCF 服務 Wcf-netmsmq 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e623b6dc-32e5-467c-bb7d-68b7a75723c1
caps.latest.revision: "46"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38530cfdbde78e96fb41093c79b6a5d1bb8fd132
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2017
---
# <a name="walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter"></a>逐步解說： 使用發佈 WCF 服務 Wcf-netmsmq 配接器
  
> [!NOTE]
>  如需配接器的詳細資訊，請參閱[配接器在 BizTalk Server](../core/adapters-in-biztalk-server.md)。  
  
## <a name="introduction"></a>簡介
  
 在[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，協調流程可以發行成[!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]服務。 透過 BizTalk 接收位置、 協調流程可以公開[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]端點，使其由呼叫[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]用戶端。 **BizTalk WCF 服務發佈精靈**提供簡單的方式來公開協調流程做為接收位置。  
  
 Wcf-netmsmq 配接器會使用**NetMsmqBinding**提供支援使用 Microsoft Message Queuing (也稱為 MSMQ) 做為其基礎傳輸的繫結。 用戶端[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務傳送[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]MSMQ 的訊息佇列使用設定為使用 Wcf-netmsmq 配接器的接收位置。 配接器會收取[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]從 MSMQ 佇列的訊息轉換成[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]格式，然後將其寫入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫。  
  
 本逐步解說示範如何[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]用戶端主控台應用程式會使用 Wcf-netmsmq 配接器與通訊[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]透過 MSMQ 訊息佇列的.NET 主控台應用程式中裝載的服務。 它會示範如何發行使用 BizTalk WCF 服務發佈精靈的接收位置的中繼資料。 它也會示範如何設定 Web 應用程式來支援發佈中繼資料。  
  
 完成此逐步解說之後，您將會瞭解如何執行下列工作：  
  
-   從 Visual Studio 內使用**部署**命令，將 BizTalk 組件部署到本機執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 這樣會建立有組件填入其中的 BizTalk 應用程式。 BizTalk 組件包含資源資訊；例如，要在 BizTalk 方案中使用的協調流程、管線、結構描述和對應。  
  
-   從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，設定 Wcf-netmsmq 接收位置以裝載與發佈[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  
  
-   從**BizTalk WCF 服務發佈精靈**，建立 Web 應用程式，以發佈現有接收位置的中繼資料。 提交訊息到接收位置的用戶端會使用此中繼資料。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此範例中的步驟會確認您的環境會安裝下列先決條件：  
  
-   建置組件和執行部署程序中，與電腦執行此範例中，這兩種電腦需要 Microsoft Windows Server、.NET Framework 和 BizTalk Server。  
  
-   用來建置組件並執行部署程序的電腦需要 Microsoft Visual Studio。  
  
-   執行此範例的電腦需要[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器和[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]系統管理工具。 這些是 Microsoft 的安裝期間安裝的選項[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。  
  
-   在電腦上您用來執行管理工作，您必須以成員的使用者帳戶執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組，才能設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]內的應用程式設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此使用者帳戶也必須為管理主控件執行個體和其他工作可能需要的應用程式部署的本機系統管理員群組的成員。  
  
-   需要的任何電腦上[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]功能，完成的單次安裝程序[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]範例[http://go.microsoft.com/fwlink/?LinkId=135510](http://go.microsoft.com/fwlink/?LinkId=135510)。  
  
-   執行範例，並匯入繫結或.msi 檔案的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請確定主機不受信任的主機，或匯入將會失敗。  
  
-   您必須下載的逐步解說程式碼，並將它解壓縮到您的電腦。 這個逐步解說是整個屬於[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器逐步解說 」 套件。 您可以下載檔案**WCFAdapterWalkthroughs.exe**從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Developer Center [http://go.microsoft.com/fwlink/?LinkId=194140](http://go.microsoft.com/fwlink/?LinkId=194140)。  
  
## <a name="build-and-deploy-the-biztalk-solution-biztalkapp"></a>建置和部署 BizTalk 方案 BizTalkApp  
  
1.  擷取至 WCFNetMsmqAdapterPublishing.exe **C:\WCFNetMsmqAdapterPublishing**。  
  
2.  在 Visual Studio 中開啟**Wcfnetmsmqadapterpublishing**檔案。  
  
3.  在 [方案總管] 中，展開**[biztalkapp]**，然後開啟**OrderProcess.odx**檢閱。 範例協調流程接收訂單要求訊息，並只再傳回訂單回應訊息。  
  
4.  因為**[biztalkapp]**該組件必須安裝在 GAC 中，它將需要強式名稱金鑰檔案，以完成部署程序。 以滑鼠右鍵按一下**[biztalkapp]**專案，然後再按一下**屬性**。 在**屬性**頁面上，按一下**簽署**，然後選取**簽署組件**。 按一下向下的箭號，在**選擇強式名稱金鑰檔**下拉式清單中，按一下  **\<新增 >**輸入`keyfile.snk`中**金鑰檔名稱**文字方塊。 取消核取**保護我的密碼金鑰檔**，然後按一下**確定**。  
  
5.  按一下**部署**索引標籤，然後再變更**伺服器**屬性，如果您使用不同的資料庫伺服器的 「 BizTalk 管理 」 資料庫，除了**LOCALHOST**。  請確定**BizTalk 應用程式**值設定為**WCFNetMsmqAdapterPublishing**。 請確定**安裝到全域組件快取**設**True**。  
  
6.  在 [方案總管] 中，以滑鼠右鍵按一下**[biztalkapp]**專案，然後按一下**重建**。  
  
7.  在 [方案總管] 中，以滑鼠右鍵按一下**[biztalkapp]**，然後按一下**部署**。  
  
## <a name="configure-the-application"></a>設定應用程式  
  
1.  請確定您的 Microsoft Message Queuing (MSMQ) 已安裝的元件在您的電腦上，如下所示：  
  
    1.  按一下**啟動**，以滑鼠右鍵按一下**電腦**，然後按一下**管理**開啟**伺服器管理員**。  
  
    2.  展開**功能**節點。  如果**訊息佇列**是未安裝，以滑鼠右鍵按一下**功能**，然後選取**新增功能**。 檢查**訊息佇列**，按一下 **下一步**，然後按一下**安裝**該系統上安裝 MSMQ。  
  
2.  請確定 MSMQ 訊息佇列服務已啟動，如下所示使用 Wcf-netmsmq 配接器的電腦上：  
  
    1.  按一下**啟動**，指向 **系統管理工具**，然後按一下**服務**。  
  
    2.  在**服務**，請確定**狀態**的**訊息佇列**服務**已啟動**。 如果服務未啟動，以滑鼠右鍵按一下**訊息佇列**，然後按一下**啟動**。  
  
3.  建立目標佇列接收位置使用從中 Wcf-netmsmq 配接器會收取傳入[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]來自用戶端的訊息。  
  
    1.  按一下**啟動**，指向 **系統管理工具**，然後按一下**電腦管理**。  
  
    2.  在**電腦管理**，依序展開**服務和應用程式**，依序展開**訊息佇列**，以滑鼠右鍵按一下**私用佇列**，指向**新增**，然後按一下**私用佇列**。  
  
    3.  在**新增私用佇列** 對話方塊中，輸入`WCFNetMsmqAdapterPublishing`中**佇列名稱**文字方塊中，選取**交易式**核取方塊，然後**確定**.  
  
4.  建立範例應用程式的 WCF-NetMsmq 接收位置，如下所示：  
  
    1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 **BizTalk Server 管理**。  
  
    2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk 群組**，依序展開**應用程式**，展開**WCFNetMsmqAdapterPublishing**，以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下**單向接收埠。**  
  
    3.  在**接收埠屬性**對話方塊中，於**名稱**文字方塊中，輸入`WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder`，然後按一下**確定**。  
  
    4.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder**，指向**新增**，然後按一下**接收位置**.  
  
    5.  在**接收位置屬性**對話方塊中，於**名稱**文字方塊中，輸入`WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder.NetMsmq`。  
  
    6.  在**接收位置屬性**對話方塊中，於**傳輸**區段旁邊**類型**，選取**Wcf-netmsmq**從下拉式清單，然後按一下**設定**。  
  
    7.  在**Wcf-netmsmq 傳輸屬性**對話方塊**一般**索引標籤的**位址 (URI)**文字方塊中，輸入`net.msmq://localhost/private/WCFNetMsmqAdapterPublishing`。  
  
    8.  在**Wcf-netmsmq 傳輸屬性**對話方塊**繫結**索引標籤上，請確定**交易式**選取核取方塊。  
  
        > [!NOTE]
        >  因為您建立的目標佇列為交易式佇列，所以必須選取此核取方塊。 如果未選取此方塊，因為交易式接收位置的需求與基礎 MSMQ 佇列之間會有不一致的情形不會啟用接收位置。  
  
    9. 在**Wcf-netmsmq 傳輸屬性**對話方塊**安全性**索引標籤上，選取**無**從**安全性模式**下拉式清單.  
  
        > [!NOTE]
        >  本逐步解說假設電腦上已安裝 MSMQ 但停用 [!INCLUDE[btsAD](../includes/btsad-md.md)] 整合。 預設值為**WindowsDomain**，如**MSMQ 驗證模式**屬性時，才能使用[!INCLUDE[btsAD](../includes/btsad-md.md)]已啟用整合。  
  
    10. 在**接收位置屬性**對話方塊中，按一下 **確定**。  
  
5.  建立範例應用程式的 FILE 傳送埠。 此連接埠用來路由傳送來自服務的基礎協調流程從訂單回應。  
  
    1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**WCFNetMsmqAdapterPublishing**，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
    2.  在**傳送埠屬性**對話方塊中，於**名稱**文字方塊中，輸入`WCFNetMsmqAdapterPublishing.SendPurchaseOrder.File`。  
  
    3.  在**傳送埠屬性**對話方塊中，於**傳輸**區段旁邊**類型**，選取**檔案**從下拉式清單中，然後按一下**設定**。  
  
    4.  在**FILE 傳輸屬性**對話方塊**一般**索引標籤的**目的地資料夾**文字方塊中，輸入`C:\WCFNetMsmqAdapterPublishing\Out`，然後按一下 **[確定]**.  
  
    5.  在**傳送埠屬性**對話方塊中，按一下 **確定**。  
  
6.  指定範例應用程式的主控件名稱和繫結，如下所示：  
  
    1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**WCFNetMsmqAdapterPublishing**，依序展開**協調流程**，以滑鼠右鍵按一下範例協調流程，按一下**屬性**，按一下 **繫結**，並設定**主機**至**BizTalkServerApplication**或另一個適當的主機。  
  
    2.  在**協調流程屬性**對話方塊中，選取**WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder**從**接收埠**的下拉式清單**PurchaseOrderRequestPort**。  
  
    3.  在**協調流程屬性**對話方塊中，選取**WCFNetMsmqAdapterPublishing.SendPurchaseOrder.File**從**傳送埠/傳送埠群組**下拉式清單如**[wcfnetmsmqadapterpublishing.sendpurchaseorder.file]**。  
  
    4.  在**協調流程屬性**對話方塊中，按一下 **確定**儲存設定。  
  
## <a name="publish-the-metadata-for-the-wcf-netmsmq-receive-location"></a>發佈 Wcf-netmsmq 接收位置的中繼資料  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 **BizTalk WCF 服務發佈精靈**。  
  
2.  在**歡迎使用 BizTalk WCF 服務發佈精靈**頁面上，按一下**下一步**。  
  
3.  在**WCF 服務類型**頁面上，選取**中繼資料唯一端點 (MEX)**核取方塊以發行中繼資料的 WCFNetMsmq 接收位置。 選取**WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder.NetMsmq**從**發行中繼資料的接收位置**下拉式清單，然後按一下**下一步**。  
  
4.  在**建立 WCF 服務**頁面上，選取**BizTalk 協調流程發佈為 WCF 服務**，然後按一下**下一步**。  
  
5.  在**BizTalk 組件**頁面上，於**BizTalk 組件檔案 (\*.dll)** ] 文字方塊中，按一下 [**瀏覽**瀏覽至**C:\WCFNetMsmqAdapterPublishing\BizTalkApp\bin\Development**資料夾中，按兩下包含的組件範例協調流程來發行，然後按一下**下一步**。  
  
6.  在**協調流程和連接埠**頁面上，請確定**連接埠： PurchaseOrderRequestPort**節點已在頁面上，選取，然後按一下**下一步**。  
  
     接收埠的 MEX 會發行並由用戶端用來提交訊息至接收位置。  
  
7.  在**WCF 服務屬性**頁面上，於**WCF 服務的目標命名空間**文字方塊中，輸入您想要這個已發佈的 URI[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務所使用，，然後按一下**下一步**. 此逐步解說中，保留預設 URI `http://tempuri.org/`。  
  
8.  在**WCF 服務位置**頁面上，執行下列動作，以指定的位置[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務來建立，然後按一下**下一步**:  
  
    1.  在**位置**文字方塊中，輸入 Web 目錄名稱[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務執行，或按一下**瀏覽**，並選取 Web 目錄。 此逐步解說中，保留預設位置 (http://localhost/*\<BizTalk 組件名稱 >*) 中**位置**文字方塊。  
  
    2.  選取**允許匿名存取 WCF 服務**選項。 這個選項會新增已建立之虛擬目錄的匿名存取。 此選項必須加以選取，才可允許精靈將為該 Web 應用程式建立的匿名驗證。  
  
9. 在**WCF 服務摘要**頁面上，按一下**建立**建立[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  
  
10. 在**完成 BizTalk WCF 服務發佈精靈**頁面上，按一下**完成**。  
  
## <a name="configure-the-web-application-hosting-the-published-metadata-service"></a>設定裝載已發佈的中繼資料服務的 Web 應用程式  
  
1.  開啟命令提示字元，請移至**C:\inetpub\wwwroot\Microsoft.Samples.BizTalk.WCF.NetMsmqPublishing.BizTalkApp**資料夾其中**BizTalk WCF 服務發佈精靈**建立[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。 開啟**Web.config**檔案使用 [記事本]。  
  
2.  在記事本中，加入下列一行 **\<system.web >**項目：  
  
    ```  
    <trust level="Full" originUrl="" />  
    ```  
  
    > [!NOTE]
    >  這個設定是選擇性的。 它會授與 ASP.NET 應用程式裝載所發佈[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務的存取權限於作業系統安全性的任何資源。  
  
3.  使用 Internet Explorer 測試發佈的 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務，如下所示：  
  
    1.  按一下**啟動**，指向 **系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**。  
  
    2.  在 IIS 管理員中建立具有正確 BizTalk 資料庫權限的應用程式集區，以供此服務在其中執行。 以滑鼠右鍵按一下**應用程式集區**，按一下 **新增應用程式集區**，輸入應用程式集區的名稱，然後按一下**確定**。  
  
    3.  展開**應用程式集區**，以滑鼠右鍵按一下您剛在應用程式集區建立，並選取**進階設定**。 在下**處理序模型**區段中，輸入擁有存取權的帳戶[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫下**識別**欄位。  
  
    4.  展開**網站**，依序展開**Default Web Site**，然後展開 BizTalk WCF 服務發佈精靈所建立的 Web 應用程式。  
  
    5.  在 [IIS 管理員] 中，在中央窗格中，按一下**內容檢視**顯示應用程式的檔案。  
  
    6.  以滑鼠右鍵按一下**Microsoft_Samples_BizTalk_WCF_NetMsmqPublishing_BizTalkApp_OrderProcess_PurchaseOrderRequestPort.svc**服務檔**BizTalk WCF 服務發佈精靈**建立、，然後按一下**瀏覽**。 這會開啟 Internet Explorer 顯示**BizTalkServerInstance 服務**表示網頁的執行個體[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務正在執行。 此頁面會顯示完整的 WSDL 位址，您可以複製和搭配服務中繼資料工具 (svcutil.exe)，或從 Visual Studio 內擷取 proxy 程式碼和組態檔可以用來建立服務用戶端應用程式。  
  
    7.  將命令列，從的完整 WSDL 位址複製到剪貼簿**BizTalkServerInstance 服務**上一個步驟中 Internet Explorer 顯示的頁面。  
  
         **svcutil.exe http://localhost/Microsoft.Samples.BizTalk.WCF.NetMsmqPublishing.BizTalkApp/Microsoft_Samples_BizTalk_WCF_NetMsmqPublishing_BizTalkApp_OrderProcess_PurchaseOrderRequestPort.svc?wsdl**  
  
## <a name="build-the-client-application"></a>建置用戶端應用程式  
  
1.  開啟 Visual Studio 命令提示字元，以系統管理員身分，並移至**C:\WCFNetMsmqAdapterPublishing\WCFClient**資料夾。 這是您放置 proxy 類別和應用程式組態檔。  
  
2.  貼上整個 svcutil.exe 命令列，其中包含您在先前的程序中複製的完整 WSDL 位址，然後按 ENTER 鍵。 這會建立 proxy 類別， **BizTalkServiceInstance.cs**，和應用程式組態檔， **output.config**。命令提示字元視窗保持開啟以供使用期間最後一節。  
  
3.  在 Visual Studio，在 方案總管中以滑鼠右鍵按一下**WCFClient**，指向 **新增**，然後按一下**現有項目**。  
  
4.  在**加入現有項目**對話方塊中，瀏覽至**WCFClient**資料夾中，選取**所有檔案 (\*。\*)**中**檔案類型**下拉式清單中，選取**BizTalkServiceInstance.cs**和**output.config**檔案、，然後按一下 **新增**。  
  
5.  展開**WCFClient**，以滑鼠右鍵按一下**output.config**，按一下 **重新命名**，然後輸入`App.config`做為新的名稱。  
  
6.  按兩下**Program.cs**檢閱如何呼叫發佈[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務使用 svcutil.exe 所產生的 proxy 類別。  
  
7.  展開**參考**，然後確定**WCFClient**專案具有**System.ServiceModel.dll**參考。  
  
8.  以滑鼠右鍵按一下**WCFClient**專案，然後選取**建置**。 保持 Visual Studio 開啟，然後跳到下一節。  
  
## <a name="test-the-sample-solution-with-the-wcf-netmsmq-adapter"></a>測試範例解決方案使用 Wcf-netmsmq 配接器  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**WCFNetMsmqAdapterPublishing**應用程式，，然後按一下**啟動**。 在**啟動**對話方塊中，按一下 **啟動**。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**平台設定**，依序展開**主控件執行個體**，以滑鼠右鍵按一下**BizTalkServerApplication**或另一個適當的主控件執行個體，，然後按一下**重新啟動**。 雖然這個步驟並非必要，最好先確認此範例運作正常這一點。  
  
3.  在 Visual Studio 中，在**偵錯**功能表上，按一下 **啟動但不偵錯**執行 WCFClient 應用程式。 此傳送範例訊息給 Wcf-netmsmq 接收位置。 您會看到以下訊息，指出輸出訊息已傳送。  
  
     **呼叫送出作業上 Wcf-netmsmq 接收位置**  
  
     **按任意鍵關閉 WCF 用戶端應用程式**  
  
4.  按任意鍵關閉 WCFClient 應用程式。  
  
5.  在 Visual Studio 命令提示字元，請移至**C:\WCFNetMsmqAdapterPublishing\Out**資料夾，然後確定回應訊息傳送回 WCFClient 應用程式存在。  
  
6.  按兩下要開啟 Internet Explorer 和檢視中的 {GUID}.xml 檔案**OrderID**服務所處理的值。  
  
## <a name="see-also"></a>另請參閱  
 [設定 Wcf-netmsmq 接收位置](../core/how-to-configure-a-wcf-netmsmq-receive-location.md)   
 [WCF 配接器逐步解說](../core/wcf-adapter-walkthroughs.md)   
 [發佈 WCF 接收配接器的服務中繼資料](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)