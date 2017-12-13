---
title: "逐步解說： 使用 Wcf-nettcp 配接器使用訊息安全性模式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7f6e892-34ce-4132-8867-54cc3bbfe507
caps.latest.revision: "47"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 850d0ee715984c7465063addd778828c727e0233
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="walkthrough-using-the-message-security-mode-with-the-wcf-nettcp-adapter"></a>逐步解說： 使用訊息安全性模式，Wcf-nettcp 配接器
  
> [!NOTE]
>  如需配接器的詳細資訊，請參閱[配接器在 BizTalk Server](../core/adapters-in-biztalk-server.md)。  
  
## <a name="introduction"></a>簡介
  
 本逐步解說示範如何設定 Wcf-nettcp 配接器使用[!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]訊息安全性模式，來協助保護訊息傳輸的配接器會使用 Ws-security 規格。 此規格說明 SOAP 訊息通訊協定來完成機密性、 完整性和 SOAP 訊息層級驗證的增強功能。 訊息安全性模式要求的作業，例如加密/解密和簽章/驗證用途的安全性模式的組合視指定的服務憑證。  
  
 Wcf-nettcp 配接器會使用 NetTcpBinding 繫結之間的通訊[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]用戶端和[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]遠端服務。 該配接器可完整存取 SOAP 安全性、可靠性和交易功能。 它可讓協調流程和結構描述發行成[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務、 以及也可讓您使用外部 WCF 服務協調流程。 此配接器使用 TCP 傳輸，而且訊息具有二進位編碼。 Wcf-nettcp 配接器是由傳送配接器和接收配接器所組成。  
  
 本逐步解說示範如何使用 Active Directory 憑證服務建立訊息安全性模式的憑證。 您將建立的伺服器和用戶端憑證，然後設定 Wcf-nettcp 接收位置，以訊息安全性模式中使用的憑證。 使用[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]用戶端，您會將訊息傳送至該接收位置在根據 XML 加密語法和處理加密的狀態。  
  
 完成此逐步解說之後，您將會瞭解如何執行下列工作：  
  
-   使用 Active Directory 憑證服務來建立憑證要求和發行憑證，以完成程序。  
  
-   從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，設定 Wcf-nettcp 配接器使用訊息安全性模式。  
  
## <a name="prerequisites"></a>必要條件  
 執行此範例中的步驟會確保您的環境會安裝下列必要條件。  
  
-   建置組件，並執行部署程序的電腦和執行範例的電腦需要 Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，Microsoft [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]，與 Microsoft BizTalk Server。  
  
-   用來建置組件並執行部署程序的電腦需要 Microsoft Visual Studio。  
  
-   執行此範例的電腦需要[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器和[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]系統管理工具。 這些是 Microsoft BizTalk Server 安裝期間安裝的選項。  
  
-   在電腦上您用來執行管理工作，您必須以成員的使用者帳戶執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組，才能設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]內的應用程式設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此使用者帳戶也必須為管理主控件執行個體和其他工作可能需要的應用程式部署的本機系統管理員群組的成員。  
  
-   需要的任何電腦上[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]功能，完成的單次安裝程序[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]範例[http://go.microsoft.com/fwlink/?LinkId=135510](http://go.microsoft.com/fwlink/?LinkId=135510)。  
  
-   執行範例，並匯入繫結或.msi 檔案的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請確定主機不受信任的主機，或匯入將會失敗。  
  
-   在電腦上執行範例，確定已安裝的 Active Directory 憑證服務。  
  
-   您必須下載的逐步解說程式碼，並將它解壓縮到您的電腦。  這個逐步解說是整個屬於[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器逐步解說 」 套件。 您可以下載檔案**WCFAdapterWalkthroughs.exe**從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Developer Center [http://go.microsoft.com/fwlink/?LinkId=194140](http://go.microsoft.com/fwlink/?LinkId=194140)。  
  
## <a name="create-the-certificates-for-this-walkthrough"></a>建立這個逐步解說中的憑證  
  
1.  本節中您將會要求服務和用戶端憑證、 發行憑證，並將它們安裝到適當的儲存區。 Active Directory 憑證服務用來建立具有受信任的憑證鏈結的憑證。 如果您未遵照必要條件的要求安裝 Active Directory 憑證服務，請將 Active Directory 憑證服務安裝在您的電腦上。 如果已安裝，請移至步驟 2。  
  
    1.  按一下**啟動**，指向 **系統管理工具**，然後按一下 **伺服器管理員**。  
  
    2.  在下**伺服器管理員**] 節點，按一下 [**新增**，然後按一下**角色**。  
  
    3.  這會開啟**開始之前**對話方塊**新增角色精靈**。 按一下 **[下一步]**。  
  
    4.  上**選取伺服器角色**頁面上，選取**Active Directory 憑證服務**，按一下**下一步**，然後遵循螢幕指示以完成安裝。  
  
2.  建立服務驗證的憑證要求，如下所示：  
  
    1.  在 Internet Explorer 中瀏覽的網站`http://localhost/certsrv`。 在**歡迎**頁面上，按一下**要求憑證**，然後按一下 **進階的憑證要求**上**要求憑證**頁面。  
  
        > [!NOTE]
        >  當使用[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]與憑證授權單位要求憑證要求從[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]電腦，您可能會收到錯誤**「 為了完成憑證註冊，ca 的網站必須設定為使用 HTTPS驗證 」**。 如果發生這個錯誤，就必須設定使用 Web 憑證 (SSL) 註冊網站。 如需完成此工作的詳細資訊，請參閱下列連結：  
        >   
        >  [AD CS： 網頁註冊](http://technet.microsoft.com/library/cc732517.aspx)  
        >   
        >  [IIS 伺服器憑證安裝指示](http://msdn.microsoft.com/library/ms751408.aspx)  
  
    2.  在**進階憑證要求**頁面上，按一下**建立並提交一個要求向這個 CA**。  
  
    3.  在**進階憑證要求**頁面上，輸入`localhost`中**名稱**文字方塊中，選取**伺服器驗證憑證**從**需要的憑證類型**下拉式清單，然後按一下**送出**。  
  
3.  建立用戶端驗證的憑證要求，如下所示：  
  
    1.  在 Internet Explorer 中瀏覽的網站`http://localhost/certsrv`。 在**歡迎**頁面上，按一下**要求憑證**，然後按一下 **進階的憑證要求**上**要求憑證**頁面。  
  
    2.  在**進階憑證要求**頁面上，按一下**建立並提交一個要求向這個 CA**。  
  
    3.  在**進階憑證要求**頁面上，輸入`contoso`中**名稱**文字方塊中，選取**用戶端驗證憑證**從**需要的憑證類型**下拉式清單，然後按一下**送出**。  
  
    > [!NOTE]
    >  如果您網域控制站以外的電腦上執行 BizTalk Server，則會使用用戶端驗證憑證。 這將會在配接器的 [屬性] 對話方塊中設定。  
  
4.  使用 [憑證授權單位] 管理主控台來發出憑證，如下所示：  
  
    1.  按一下**啟動**，指向 **系統管理工具**，然後按一下 **憑證授權單位**。  
  
    2.  在**憑證授權單位**管理主控台中，展開 憑證授權單位的名稱，然後按兩下**擱置要求**。  
  
    3.  在右窗格中**憑證授權單位**管理主控台中，以滑鼠右鍵按一下 服務驗證憑證要求，指向**所有工作**，然後按一下 **問題**.  
  
    4.  在右窗格中**憑證授權單位**管理主控台中，以滑鼠右鍵按一下 用戶端驗證憑證要求，指向**所有工作**，然後按一下 **問題**.  
  
    5.  關閉**憑證授權單位**管理主控台。  
  
5.  在電腦上安裝該發出憑證，如下所示：  
  
    1.  在 Internet Explorer 中瀏覽的網站`http://localhost/certsrv`。  
  
    2.  在**歡迎**頁面上，按一下**檢視擱置的憑證要求狀態**。  
  
    3.  在**檢視擱置憑證要求的狀態**頁面上，按一下 伺服器驗證憑證。  
  
    4.  在**憑證核發**頁面上，按一下**安裝這個憑證**。  
  
    5.  在 Internet Explorer 中瀏覽的網站`http://localhost/certsrv`。  
  
    6.  在**歡迎**頁面上，按一下**檢視擱置的憑證要求狀態**。  
  
    7.  在**檢視擱置憑證要求的狀態**頁面上，按一下 用戶端驗證憑證。  
  
    8.  在**憑證核發**頁面上，按一下**安裝這個憑證**。  
  
6.  確定發出的憑證已正確安裝，如下所示：  
  
    1.  開啟 [Microsoft Management Console (MMC)]。 若要這樣做，請按一下**啟動**，按一下**執行**，型別`mmc`，然後按一下 **確定**。  
  
    2.  在 MMC 中，在**檔案**功能表上，按一下 **新增/移除嵌入式管理單元**。  
  
    3.  在 [新增/移除嵌入式管理單元] 對話方塊中，按一下 [新增]。  
  
    4.  在**新增獨立嵌入式管理單元**對話方塊中，選取**憑證**從**可用的獨立嵌入式管理單元**清單，然後再按**新增**.  
  
    5.  在**憑證嵌入式管理單元**對話方塊中，選取**我的使用者帳戶**選項，然後再按一下**完成**。  
  
    6.  關閉所有開啟的對話方塊。  
  
    7.  在 MMC 中，在 主控台根目錄 視窗中，展開 **憑證-目前使用者**，依序展開**個人**，展開**憑證**，並請確定憑證，您安裝在上一個步驟中會顯示。  
  
## <a name="create-the-biztalk-application-for-this-walkthrough"></a>建立這個逐步解說的 BizTalk 應用程式  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk 群組**，以滑鼠右鍵按一下**應用程式**，指向 **新增**，然後按一下 **應用程式**.  
  
3.  在**應用程式屬性**對話方塊**一般**索引標籤上，輸入`WcfMessageSecurity`，然後按一下**確定**。  
  
4.  使用 WCF-NetTcp 配接器建立 BizTalk 應用程式的接收位置，如下所示：  
  
    1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**WcfMessageSecurity**，以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下  **單向接收埠。**  
  
    2.  在**接收埠屬性**對話方塊中，於**名稱**文字方塊中，輸入`WcfMessageSecurity.OrderRequest.Receive`，然後按一下**確定**。 接收這個名稱是嚴格任意的連接埠，但此名稱的好處邏輯。  
  
    3.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收位置**，按一下 **新增**，然後按一下 **單向接收位置**。 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]用戶端會將[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]訊息至這個接收位置。 選取**WcfMessageSecurity.OrderRequest.Receive**接收埠，然後再按一下**確定**。  
  
    4.  在**接收位置屬性**對話方塊中，於**名稱**文字方塊中，輸入`WcfMessageSecurity.OrderRequest.Receive.NetTcp`。 這個名稱的接收位置任意嚴格，但此名稱的意義邏輯。  
  
    5.  在**接收位置屬性**對話方塊中，於**傳輸**區段旁邊**類型**，選取**Wcf-nettcp**從下拉式清單清單，然後再按**設定**。  
  
    6.  在**Wcf-nettcp 傳輸屬性**對話方塊**一般**索引標籤的**位址 (URI)**文字方塊中，輸入`net.tcp://localhost/WcfMessageSecurity`。  
  
    7.  在**Wcf-nettcp 傳輸屬性**對話方塊**安全性**索引標籤上，選取**訊息**從**安全性模式**下拉式清單清單，然後再選取**憑證**從**訊息用戶端認證類型**下拉式清單。 這會設定 Wcf-nettcp 配接器使用訊息安全性模式。  
  
    8.  設定用於訊息安全性模式的服務憑證。 在**Wcf-nettcp 傳輸屬性**對話方塊中，於**服務憑證**區段中，按一下**瀏覽**。 在**選取的服務憑證**對話方塊中，選取您在先前程序中安裝的伺服器驗證憑證，然後按一下**確定**以關閉對話方塊並儲存變更。  
  
    9. 關閉所有開啟的對話方塊。  
  
        > [!NOTE]
        >  若要驗證用戶端憑證，搭配[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]接收配接器，用戶端憑證的 CA 憑證鏈結必須安裝在執行主控件執行個體之電腦的受信任的根憑證授權單位憑證存放區如[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器。 因為這個逐步解說假設憑證服務已安裝在同一部電腦上[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]用戶端和[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器，您不需要在您的電腦上安裝的 CA 憑證鏈結。  
  
5.  建立 BizTalk 應用程式的 FILE 傳送埠。 這是要傳送的協調流程代表訂單要求輸出訊息到位置[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務。  
  
    1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**WcfMessageSecurity**，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**  
  
    2.  在**傳送埠屬性**對話方塊**一般**索引標籤的**名稱**文字方塊中，輸入`WcfMessageSecurity.OrderRequest.Send.FILE`。  
  
    3.  在**傳送埠屬性**對話方塊中，於**傳輸**區段旁邊**類型**，選取**檔案**從下拉式清單中，然後按一下**設定**。  
  
    4.  在**FILE 傳輸屬性**對話方塊**一般**索引標籤上，輸入`C:\WCFMessageSecurity\OrderRequestOut`中**目的地資料夾**文字方塊，然後再按一下**[確定]**.  
  
    5.  在**傳送埠屬性**對話方塊**篩選**索引標籤上，選取**BTS。ReceivePortName**如**屬性**欄位中，輸入`WcfMessageSecurity.OrderRequest.Receive`如**值**欄位，，然後按一下**確定**。 這個篩選條件運算式會路由傳送傳入[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]到用戶端的訊息**WcfMessageSecurity.OrderRequest.Receive**接收這個傳送埠的連接埠。  
  
## <a name="test-the-wcf-client-against-the-biztalk-application"></a>測試 WCF 用戶端針對 BizTalk 應用程式  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**WcfMessageSecurity**，然後按一下 **啟動**。 在**啟動**對話方塊中，按一下 **啟動**。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**平台設定**，依序展開**主控件執行個體**，以滑鼠右鍵按一下**BizTalkServerApplication**或另一個適當的主控件執行個體，，然後按一下 **重新啟動**。  
  
3.  建立名為的資料夾**C:\WCFMessageSecurity**如本逐步解說的工作資料夾。 逐步解說將檔案解壓縮至這個資料夾。  
  
4.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟**Wcfmessagesecurity**檔案**C:\WCFMessageSecurity**資料夾。  
  
5.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，展開**WcfClient**，然後開啟**Program.cs**檢閱。  
  
    -   用戶端傳送訊息至 Wcf-nettcp 接收位置，您在上一個程序中建立。  
  
    -   用戶端會建立與通道**NetTcpBinding**，並設定要使用憑證進行用戶端認證類型的繫結。  
  
    -   用戶端會設定要使用您安裝用戶端驗證之前程序中的用戶端驗證憑證的端點行為。  
  
    -   類別，**程式**，實作**IClientMessageInspector**和**IEndpointBehavior**介面，以顯示傳出[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]從這個訊息在命令提示字元的用戶端。  
  
6.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**WcfMessageSecurity**解決方案，，然後按一下**重建**。  
  
7.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**偵錯**功能表上，按一下 **啟動但不偵錯**執行 WcfClient，將傳送訊息至 Wcf-nettcp 接收位置。 出現的命令提示字元會顯示執行結果。  
  
    1.  在命令提示字元中，檢視訂單要求訊息。 請注意**OrderId**欄位和訊息的結構。  
  
    2.  在命令提示字元中，移至`C:\WCFMessageSecurity\OrderRequestOut`資料夾，然後確定所傳送的訂單要求訊息[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]用戶端會出現。  
  
    3.  關閉命令提示字元。