---
title: '逐步解說 (AS2): 使用同步 MDN 透過 AS2 傳送 EDI |Microsoft 文件'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 21891d29-eb22-4b31-9258-14b72ae675dc
caps.latest.revision: 34
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4953e0f3cdc5373d20497d1510fafd9f24991c30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22292342"
---
# <a name="walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn"></a>逐步解說 (AS2)：使用同步 MDN 透過 AS2 傳送 EDI
本逐步解說提供一組逐步執行的程序，建立使用同步 MDN 透過 AS2 傳送 EDI 訊息的解決方案。 您可以在單一電腦上，建立並測試此逐步解說中的整個解決方案。  
  
## <a name="prerequisites"></a>必要條件  
 以下是執行此主題中之程序的必要條件：  
  
-   您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
-   執行逐步解說的電腦必須安裝 Internet Information Services (IIS) 7。  
  
-   若執行逐步解說的電腦是安裝 64 位元版本的 Windows，您必須確定 BizTalk 主機只標示為 32 位元。 您也必須確定 IIS 已將應用程式集區的「啟用 32 位元應用程式」設定為 True。 如需詳細資訊，請參閱[教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)。  
  
## <a name="how-the-solution-sends-an-edias2-message-and-returns-a-synchronous-mdn"></a>解決方案如何傳送 EDI/AS2 訊息並傳回同步 MDN  
 解決方案會執行下列作業：  
  
1.  單向 FILE 接收埠從 Contoso 接收 EDI 交換。  
  
    > [!NOTE]
    >  這份清單中的事件可能不會按照所示的順序發生。  
  
2.  藉由使用通過接收管線，接收埠會將測試訊息保留原狀置放在 MessageBox 中。  
  
3.  靜態雙向傳送埠會拾取 EDI 交換，並將其編碼為 AS2 格式。  
  
4.  傳送埠會透過 AS2 傳輸，將 AS2 編碼 EDI 交換傳送到 Fabrikam 合作對象。  
  
5.  Fabrikam 的雙向接收埠會使用 Fabrikam 虛擬目錄來接收 AS2 訊息。 接收管線會解碼來自 AS2 的 EDI 交換，然後將 EDI 交換置放在 MessageBox 中。  
  
6.  與雙向接收埠相關聯的傳送埠會傳回同步 MDN。  
  
7.  與雙向傳送埠相關聯的接收埠接收 MDN，並將其置放在 MessageBox 中。  
  
8.  具有通過傳送管線的靜態單向傳送埠會拾取該 MDN。  
  
9. 單向傳送埠會將 MDN 傳送至本機資料夾。  
  
10. 具有通過傳送管線的靜態單向傳送埠會拾取該 EDI 訊息。  
  
11. 單向傳送埠會將 EDI 訊息傳送至本機資料夾。  
  
 下圖顯示這個解決方案的架構。  
  
 ![使用同步 MDN 的 AS2 傳送](../core/media/270d24b7-3b5d-45cc-ba06-6c9f74717194.gif "270d24b7-3b5d-45cc-ba06-6c9f74717194")  
  
## <a name="the-functionality-in-this-solution"></a>此解決方案中的功能  
 下列項目適用於本逐步解說的功能：  
  
-   這個逐步解說是處理 AS2 功能，而非 EDI 功能。 因此，與 AS2 處理有關的所有連接埠都是使用 AS2Receive 或 AS2Send 管線，而非 AS2EdiReceive 或 AS2EdiSend。 與 AS2 處理無關的連接埠，則使用 PassThruReceive 或 PassThruTransmit 管線。  
  
-   沒有啟用狀態報告。  
  
-   這個解決方案不會設定簽章、壓縮、加密或不可否認性資料庫中的訊息存放區。 如需有關設定這些屬性的程序，請參閱[設定 AS2 屬性](../core/configuring-as2-properties.md)。  
  
## <a name="configuring-and-testing-the-walkthrough"></a>設定和測試逐步解說  
 這個解決方案所需的程序包含下列步驟：  
  
-   使用必要的訊息結構描述來建置並部署 BizTalk 專案，因此 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用結構描述處理收到的交換。  
  
-   讓 BTS ISAPI 篩選器可用於接收 AS2 訊息。  
  
-   建立 Fabrikam 虛擬目錄，用於接收 Contoso 的 AS2 訊息，如接收位置中所設定。  
  
-   指定 Fabrikam 虛擬目錄不是由 Windows SharePoint Services 管理。  
  
-   建立單向 FILE 接收埠，接收要透過 AS2 傳輸來傳送的 EDI 測試訊息。 建立本機資料夾，接收測試訊息。  
  
-   建立靜態雙向 HTTP 傳送埠，以便讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送包含 EDI 商務文件的 AS2 訊息給 Fabrikam，並接收 MDN 回應。 將傳送管線設定為 AS2Send 管線，並將接收管線設定為 AS2Receive 管線。  
  
-   建立雙向 HTTP 接收埠，以便讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收 AS2 訊息及傳送 MDN 回應。 設定接收管線為 AS2Receive 管線，並設定傳送管線為 AS2Send 管線。 設定接收位置，以透過 Fabrikam 虛擬目錄接收 AS2 訊息。  
  
    > [!NOTE]
    >  此解決方案適用於單一電腦，因此，用於傳送 AS2 訊息 (來自 Contoso) 的雙向傳送埠和用於接收 AS2 訊息 (做為 Fabrikam) 的雙向接收埠，皆位於相同電腦上。  
  
-   建立靜態單向 FILE 傳送埠 (具有通過傳送管線)，以將 MDN 路由傳送至本機資料夾。 建立本機資料夾。  
  
-   建立靜態單向 FILE 傳送埠 (具有通過傳送管線)，以將訊息內容路由傳送至本機資料夾。 建立本機資料夾。  
  
    > [!NOTE]
    >  如果您沒有傳送埠可以訂閱訊息內容，那麼訊息內容就會擱置在 MessageBox 中。  
  
-   為 Fabrikam 與 Contoso 建立合作對象 (交易夥伴)。  
  
-   為這兩個交易合作對象各建立一個商務設定檔。  
  
-   在 Fabrikam 與 Contoso 的商務設定檔之間建立 AS2 協議。 AS2 協議應包含傳送 AS2 訊息及接收同步回傳之 MDN 的屬性。  
  
-   使用測試 EDI 交換以測試逐步解說。  
  
    > [!NOTE]
    >  對於測試訊息，您可以使用 EDI 介面開發人員教學課程中所使用的 SamplePO.txt 檔案。 該檔案隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\SDK\EDI Interface Developer Tutorial\ 資料夾中。 這是 X12 850 訊息。  
  
### <a name="configuring-the-walkthrough"></a>設定逐步解說  
 本節說明設定逐步解說的程序。  
  
##### <a name="to-deploy-the-message-schema"></a>若要部署訊息結構描述  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。  
  
    > [!NOTE]
    >  本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)， 如果沒有，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
2.  以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **現有項目**。 若要使用 SamplePO.txt 檔案來測試您的解決方案，請移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 資料夾。 選取 X12_00401_850.xsd 結構描述，然後按一下**新增**。  
  
    > [!NOTE]
    >  若要使用不同的 EDI 結構描述，請移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_SchemaEDI 資料夾。 如果 EDI 結構描述尚未解壓縮至 XSD_SchemaEDI 資料夾，執行**MicrosoftEdiXSDTemplates.exe** XSD_SchemaEDI 資料夾結構描述解壓縮至預設資料夾中的檔案。  
  
3.  設定組件金鑰檔案，然後建置並部署組件。  
  
##### <a name="to-enable-the-bts-isapi-filter"></a>若要啟用 BTS ISAPI 篩選器  
  
1.  按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**.  
  
    > [!TIP]
    >  視作業系統而定，[系統管理工具] 開始功能表選項可能無法使用。 在這種情況下，按一下**啟動**，按一下 **執行**，並輸入`inetmgr`以開啟 網際網路資訊服務 (IIS) 管理員。  
  
2.  選取根 Web 伺服器項目和**功能檢視**，按兩下 **處理常式對應**然後在 動作 窗格按一下**新增指令碼對應**。  
  
    > [!NOTE]
    >  在 Web 伺服器層級設定指令碼對應會使得此對應套用至所有子網站。 若要限制對應至特定網站或虛擬資料夾，請選取目標網站或資料夾，而不要選取 Web 伺服器。  
  
3.  在**新增指令碼對應**對話方塊方塊中，輸入`BtsHttpReceive.dll`中**要求路徑**欄位。  
  
4.  在**可執行檔**欄位中，按一下**省略符號 （...）** 按鈕並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive。 選取 BtsHttpReceive.dll，然後按一下**確定**。  
  
5.  輸入`BizTalk HTTP Receive`中`Name`欄位，，然後按一下**要求限制**。  
  
6.  在**要求限制**對話方塊中，選取**動詞**索引標籤，然後選取 **下列動詞命令的其中一個**。 輸入`POST`為動詞命令。  
  
7.  在**存取**索引標籤上，選取**指令碼**，然後按一下 **確定**。  
  
8.  按一下**確定**時提示您允許 ISAPI 延伸模組，請按一下 **是**。  
  
##### <a name="to-configure-the-fabrikam-web-page"></a>若要設定 Fabrikam 網頁  
  
1.  在 [IIS 管理員] 中，以滑鼠右鍵按一下**應用程式集區**選取**新增應用程式集區**。  
  
2.  在**新增應用程式集區**對話方塊方塊中，輸入**BizTalkAppPool**中**名稱**，然後選取 **.NET Framework v4.0.30210**中 **.NET framework 版本**下拉式清單。 按一下 **[確定]**。  
  
    > [!NOTE]
    >  版本號碼可能會依據電腦上安裝的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 版本而有所不同。  
  
3.  選取**應用程式集區**，請在**功能檢視**選取**BizTalkAppPool**，然後按一下 **進階設定**中**動作**窗格。  
  
4.  在**進階設定**對話方塊中，選取**識別**，然後按一下省略符號 （...） 按鈕。  
  
5.  在**應用程式集區識別**對話方塊中，選取**自訂帳戶**，然後按一下 **設定**。  
  
6.  輸入**使用者名**和**密碼**是 administrators 群組的成員的使用者帳戶，請輸入中的密碼**確認密碼**然後按一下  **確定**傳回給 IIS Manager 中的三倍。  
  
7.  在 [IIS 管理員] 中，開啟**網站**資料夾。 以滑鼠右鍵按一下**Default Web Site**節點，然後再選取**新增應用程式**。  
  
8.  在**新增應用程式**對話方塊方塊中，輸入**Fabrikam**中**別名**，然後按一下 **選取**。  
  
9. 中**選取應用程式集區**對話方塊中，選取**BizTalkAppPool**按一下**確定**。  
  
10. 按一下省略符號 （...） 按鈕並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive 的**實體路徑**。  
  
11. 按一下**測試設定**並確認沒有顯示在錯誤**測試連接** 對話方塊。 按一下 [關閉]，然後按一下 [確定]。  
  
12. 在 [IIS 管理員] 中，選取 Fabrikam 虛擬目錄和**功能檢視**，連按兩下**驗證**。  
  
13. 在**驗證**頁面上，選取**匿名驗證**並確認**狀態**是**啟用**。 如果**狀態**是**已停用**，按一下 **啟用**中**動作**窗格。  
  
##### <a name="to-specify-that-your-virtual-directory-is-not-managed-by-windows-sharepoint-services"></a>若要指定虛擬目錄不是由 Windows SharePoint Services 管理  
  
1.  如果 Windows SharePoint Services 安裝在電腦上，按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下  **SharePoint 3.0 管理中心**。  
  
    > [!NOTE]
    >  如果設定逐步解說的相同電腦中安裝了 Windows SharePoint Services，就必須執行這個程序。 在此情況下，您必須指定 IIS 虛擬目錄不是由 Windows SharePoint Server 管理。  
  
2.  在**管理中心**頁面的 **管理中心**，按一下 **應用程式管理**。  
  
3.  在**應用程式管理**頁面上，按一下**定義管理的路徑**。  
  
4.  在**定義管理的路徑**頁面的 **新增路徑**，請在**路徑**文字方塊中，輸入`Fabrikam`。 在下**類型**，按一下**排除的路徑**，然後按一下**確定**。  
  
##### <a name="to-create-a-receive-port-to-receive-the-edi-test-message"></a>若要建立接收埠以接收 EDI 測試訊息  
  
1.  在 Windows 檔案總管中，建立本機資料夾，以接收來自 Contoso 的 EDI 交換。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠**。  
  
3.  接收埠命名為**RecvISAFromCont**，然後按一下 **接收位置**在主控台樹狀目錄中。  
  
4.  按一下 **[新增]**。  
  
5.  接收位置命名，選取**檔案**如**類型**，然後按一下 **設定**。  
  
6.  如**接收資料夾**，輸入您在步驟 1 中建立的資料夾名稱。  
  
7.  如**檔案遮罩**，輸入檔案的副檔名。 如果您使用 SamplePO.txt 檔案做為測試訊息，輸入 **\*.txt**。 按一下 **[確定]**。  
  
8.  如**接收管線**，接受預設值是**PassThruReceive**。  
  
9. 按一下**確定**，然後按一下 **確定**一次。  
  
10. 按一下**接收位置** 節點，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。  
  
##### <a name="to-create-a-two-way-send-port-to-send-the-edi-interchange-over-as2-to-fabrikam-and-receive-an-mdn-response"></a>建立雙向傳送埠以透過 AS2 傳送 EDI 交換到 Fabrikam 並接收 MDN 回應  
  
1.  > [!NOTE]
    >  靜態雙向傳送埠會拾取 EDI 交換，並將其編碼為 AS2 格式。 然後會透過 AS2 傳輸，將 AS2 編碼 EDI 交換傳送到 Fabrikam 合作對象。 接著，與雙向傳送埠相關聯的接收埠會接收來自 Fabrikam 的 MDN，並將其置放在 MessageBox 中。  
  
     在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態請求-回應傳送埠**。  
  
2.  在**傳送埠屬性**對話方塊、 傳送埠的名稱。 此解決方案中，命名為傳送埠**SendISAToFab_RecMDN**。  
  
3.  在**傳輸**區段中，選取**HTTP**如**類型**，然後按一下 **設定**。  
  
4.  在**HTTP 傳輸屬性**對話方塊中，針對**目的地 URL**，輸入**http://localhost/Fabrikam/BTSHttpReceive.dll**。  
  
5.  清除**啟用區塊編碼**，然後按一下 **確定**。  
  
6.  在**傳送管線**，選取**AS2Send**。  
  
7.  在**接收管線**，選取**AS2Receive**。  
  
8.  在主控台樹狀目錄中，選取**篩選**。 如**屬性**，輸入**BTS。ReceivePortName**;**運算子**，輸入 **==** ; 以及**值**輸入將接收 EDI 接收埠的名稱交換 (`RecvISAFromCont`)。  
  
9. 按一下 **[確定]**。  
  
10. 按一下**傳送埠**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下您的傳送埠，然後按一下 **啟動**。  
  
##### <a name="to-create-a-two-way-receive-port-to-receive-the-as2-message-and-return-an-mdn"></a>建立雙向接收埠以接收 AS2 訊息並傳回 MDN  
  
1.  > [!NOTE]
    >  Fabrikam 的雙向接收埠會使用 Fabrikam 虛擬目錄來接收 AS2 訊息。 接收管線會解碼來自 AS2 的 EDI 交換，然後將 EDI 交換置放在 MessageBox 中。 與雙向接收埠相關聯的傳送埠會傳回同步 MDN。  
  
     在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台] **BizTalk Application 1** ] 節點，以滑鼠右鍵按一下**接收埠**，指向 [**新增**，然後按一下 [ **要求回應接收埠**。  
  
2.  接收埠命名為**RecvAS2ForFab**，然後按一下 **接收位置**在主控台樹狀目錄中。  
  
3.  按一下 **[新增]**。  
  
4.  在**接收位置屬性**對話方塊中，名稱您接收位置中，選取**HTTP**如**類型**，然後按一下 **設定**。  
  
5.  在**HTTP 傳輸屬性**對話方塊方塊中，輸入 **/Fabrikam/BTSHttpReceive.dll**如**虛擬目錄加 ISAPI 延伸模組**。 清除**成功時傳回相互關聯控制代碼**選取**擱置失敗的要求**。 按一下 **[確定]**。  
  
6.  選取**AS2Receive**如**接收管線**，和**AS2Send**如**傳送管線**。 按一下**確定**，然後按一下 **確定**一次。  
  
7.  按一下**接收位置** 節點，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。  
  
##### <a name="to-create-a-send-port-to-send-the-edi-payload-to-a-local-folder"></a>若要建立傳送埠以將 EDI 內容傳送至本機資料夾  
  
1.  在 Windows 檔案總管中，建立本機資料夾，以便將 EDI 交換傳送至此本機資料夾。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊中，將傳送埠為**SendEDIMsg**。 選取**檔案**如**類型**，然後按一下 **設定**。  
  
4.  在**FILE 傳輸屬性**對話方塊中，針對**目的地資料夾**，輸入您為 EDI 內容所建立的本機資料夾。  
  
5.  如**檔案名稱**，輸入檔案名稱。 如果您使用 SamplePO.txt 檔案做為測試訊息，輸入 **%MessageID%.txt**。 按一下 **[確定]**。  
  
6.  接受預設值是**PassThruTransmit**如**傳送管線**。  
  
7.  按一下**篩選**在主控台樹狀結構，並加入挑選 EDI 內容的篩選條件屬性。 在第一行，如**屬性**，輸入**BTS。ReceivePortName**;**運算子**，輸入 **==** ;**值**，輸入接收 AS2 的接收埠名稱訊息 (`RecvAS2ForFab`); 以及**分組**，接受**和**。 在第二行，如**屬性**，輸入**EdiIntAS.IsAS2PayloadMessage**;**運算子**，輸入 **==** ; 以及**值**，輸入**True**。  
  
8.  按一下 **[確定]**。  
  
9. 按一下**傳送埠** 節點，以滑鼠右鍵按一下傳送埠，然後**啟動**。  
  
##### <a name="to-create-a-send-port-to-send-the-mdn-to-a-local-folder"></a>若要建立傳送埠以將 MDN 傳送至本機資料夾  
  
1.  在 Windows 檔案總管中，建立本機資料夾，以便將 MDN 傳送至此本機資料夾。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊中，將傳送埠為**SendMDN**。 選取**檔案**如**類型**，然後按一下 **設定**。  
  
4.  在**FILE 傳輸屬性**對話方塊中，針對**目的地資料夾**，輸入您要建立為 MDN 傳送目標的本機資料夾。  
  
5.  如**檔案名稱**，輸入 **%MessageID%.msg**。按一下**確定**。  
  
6.  接受預設值是**PassThruTransmit**如**傳送管線**。  
  
7.  按一下**篩選**在主控台樹狀目錄中。 如**屬性**，輸入**BTS。SPName**;**運算子**，輸入 **==** ;**值**，輸入傳送 AS2 訊息的傳送埠的名稱 (`SendISAToFab_RecMDN`);和**分組**，接受**和**。 第二行，如**屬性**，輸入**EdiIntAS.IsAS2MdnResponseMessage**;**運算子**，輸入 **==** ;**值**，輸入**True**。  
  
8.  按一下 **[確定]**。  
  
9. 按一下**傳送埠** 節點，以滑鼠右鍵按一下傳送埠，然後**啟動**。  
  
##### <a name="to-create-a-party-and-a-business-profile-for-fabrikam"></a>若要為 Fabrikam 建立合作對象與商務設定檔  
  
1.  以滑鼠右鍵按一下**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下 **合作對象**。  
  
2.  輸入的名稱中的合作對象**名稱**文字方塊，然後再按一下**確定**。  
  
    > [!NOTE]
    >  藉由選取**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定正在建立的合作對象為相同的組織同時裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. 據此，建立協議時將會啟用或停用某些屬性。 不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。  
  
3.  以滑鼠右鍵按一下合作對象名稱，指向**新增**，然後按一下 **商務設定檔**。  
  
4.  在**設定檔屬性**對話方塊**一般**頁面上，輸入 **[fabrikam_profile]** 中**名稱**文字方塊。  
  
    > [!NOTE]
    >  當您建立合作對象時，會同時建立設定檔。 您可以重新命名再使用該設定檔，而不需建立新設定檔。 若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。 在**一般**頁面上，指定設定檔的名稱。  
  
##### <a name="to-create-a-party-and-a-business-profile-for-contoso"></a>若要為 Contoso 建立合作對象與商務設定檔  
  
1.  以滑鼠右鍵按一下**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下 **合作對象**。  
  
2.  輸入的名稱中的合作對象**名稱**文字方塊，然後再按一下**確定**。  
  
    > [!NOTE]
    >  藉由選取**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定正在建立的合作對象為相同的組織同時裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. 據此，建立協議時將會啟用或停用某些屬性。 不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。  
  
3.  以滑鼠右鍵按一下合作對象名稱，指向**新增**，然後按一下 **商務設定檔**。  
  
4.  在**設定檔屬性**對話方塊**一般**頁面上，輸入 **[contoso_profile]** 中**名稱**文字方塊。  
  
    > [!NOTE]
    >  當您建立合作對象時，會同時建立設定檔。 您可以重新命名再使用該設定檔，而不需建立新設定檔。 若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。 在**一般**頁面上，指定設定檔的名稱。  
  
##### <a name="to-create-an-as2-agreement-between-the-two-business-profiles"></a>若要建立兩個商務設定檔之間的 AS2 協議  
  
1.  以滑鼠右鍵按一下**contoso_profile**，指向 **新增**，然後按一下 **協議**。  
  
2.  在**一般屬性** 頁面上，針對**名稱**文字方塊中，輸入協議的名稱。  
  
3.  從**通訊協定**下拉式清單中，選取**AS2**。  
  
4.  在**第二個夥伴** 區段中，從**名稱**下拉式清單中，選取**Fabrikam**。  
  
5.  在**第二個夥伴** 區段中，從**設定檔**下拉式清單中，選取**fabrikam_profile**。  
  
     您會發現兩個新的索引標籤取得旁新增**一般** 索引標籤。每個索引標籤各用於設定一個單向 AS2 協議。  
  
6.  在上執行下列工作**Contoso-> Fabrikam**  索引標籤。  
  
    1.  在**識別碼**頁面上，輸入的值**AS2-從**和**AS2-要**。 如**AS2-從**，輸入`Contoso`。 如**AS2-To**，輸入`Fabrikam`。  
  
    2.  在**通知 (Mdn)** 頁面上，執行下列動作：  
  
        1.  選取**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**核取方塊。  
  
            > [!NOTE]
            >  檢查**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**所需的測試本逐步解說，因為則只會傳回的 MDN 放入 MessageBox。 而您也才可以建立傳送埠訂閱 MDN、將 MDN 傳送到本機目錄，好讓您確認 AS2 傳輸。  
  
        2.  選取**要求 MDN**核取方塊。  
  
        3.  請確定**要求簽署的 MDN**核取方塊。  
  
        4.  保留**要求非同步 MDN**清除。  
  
        5.  在**配置通知至**，輸入任何值。 在 AS2 處理期間並不會使用這個欄位值，但還是必須在該欄位中輸入值。  
  
    3.  在**傳送埠**頁面上，將會傳送 EDI 交換給 Fabrikam 的雙向傳送埠產生關聯。 在**傳送埠**方格下方**名稱**資料行，按一下空白儲存格，然後從下拉式清單中，選取 傳送埠**SendISAToFab_RecMDN**。  
  
7.  在上執行下列工作**Fabrikam-> Contoso**  索引標籤。  
  
    > [!NOTE]
    >  在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。 若要成功地建立協議，兩個單向協議索引標籤必須已定義的值**AS2_From**和**AS2-要**。  
  
    1.  在**識別碼**頁面上，輸入的值**AS2-從**和**AS2-要**。 如**AS2-從**，輸入`Fabrikam`。 如**AS2-To**，輸入`Contoso`。  
  
8.  按一下 **[套用]**。  
  
9. 按一下 **[確定]**。 新增的協議會列在**協議**區段**合作對象與商務設定檔**窗格。 預設會啟用新增的協議。  
  
### <a name="testing-the-walkthrough"></a>測試逐步解說  
 本節提供關於如何測試逐步解說的資訊。  
  
##### <a name="to-test-the-solution"></a>測試方案  
  
1.  在 Windows 檔案總管中，移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial。 複製**SamplePO.txt**檔案。  
  
2.  貼上**SamplePO.txt**您要建立從 Contoso 接收測試訊息的本機資料夾的檔案。  
  
3.  移至您建立用來傳送 EDI 內容的本機資料夾。 確認該資料夾包含 EDI 檔案。 開啟檔案和原始測試訊息，並確認其內容是相同的。  
  
4.  移至您建立用來做為結果 MDN 之傳送目標的本機資料夾。 確認該資料夾包含一個檔案，開啟該檔案並確認是否為 MDN 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)