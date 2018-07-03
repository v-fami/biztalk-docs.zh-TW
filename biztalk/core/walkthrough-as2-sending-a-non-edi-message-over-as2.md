---
title: '逐步解說 (AS2): 透過 AS2 傳送非 EDI 訊息 |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6120b81e-bdd5-44ad-9040-26be88c71258
caps.latest.revision: 33
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78da76298e4443acfafa1893e6e4c5bb946bfd2f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002463"
---
# <a name="walkthrough-as2-sending-a-non-edi-message-over-as2"></a>逐步解說 (AS2)：透過 AS2 傳送非 EDI 訊息
本逐步解說提供一組逐步執行的程序，建立透過 AS2 傳送非 EDI 訊息的解決方案。 本逐步解說會透過 AS2 傳送 PIDX 訊息。 此方案使用含一個 AS2Send 傳送管線和一個 AS2Receive 接收管線的雙向傳送埠。 您可以在單一電腦上，建立並測試此逐步解說中的整個解決方案。  
  
## <a name="prerequisites"></a>必要條件  
 以下是執行此主題中之程序的必要條件：  
  
- 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
- 執行逐步解說的電腦必須安裝 Internet Information Services (IIS) 7。  
  
- 若執行逐步解說的電腦是安裝 64 位元版本的 Windows，您必須確定 BizTalk 主機只標示為 32 位元。 您也必須確定 IIS 已將應用程式集區的「啟用 32 位元應用程式」設定為 True。 如需詳細資訊，請參閱 <<c0> [ 教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)。  
  
## <a name="how-the-solution-sends-a-non-edias2-message-and-returns-a-synchronous-mdn"></a>解決方案如何傳送非 EDI/AS2 訊息並傳回同步 MDN  
 解決方案會執行下列作業：  
  
1. 單向 FILE 接收埠從 Contoso 接收 XML 訊息。  
  
   > [!NOTE]
   >  這份清單中的事件可能不會按照所示的順序發生。  
  
2. 透過使用 XML 接收管線，接收埠會檢查訊息。 然後接收埠將測試訊息依原狀放入 MessageBox。  
  
3. 靜態雙向傳送埠取用 XML 訊息，並訂閱接收埠收到的所有訊息。  
  
4. Fabrikam 的雙向接收埠會使用 Fabrikam 虛擬目錄來接收 AS2 訊息。 接收管線解碼 AS2 訊息，然後將訊息置放在 MessageBox 中。  
  
5. 具有通過傳送管線的靜態單向傳送埠取用該 XML 訊息。  
  
6. 單向傳送埠將 XML 訊息傳送至本機資料夾。  
  
7. 與雙向接收埠相關聯的傳送埠會傳回同步 MDN。  
  
8. 與雙向傳送埠相關聯的接收埠接收 MDN，並將其置放在 MessageBox 中。  
  
9. 具有通過傳送管線的靜態單向傳送埠會拾取該 MDN。  
  
10. 單向傳送埠會將 MDN 傳送至本機資料夾。  
  
    下圖顯示這個解決方案的架構。  
  
    ![傳送非&#45;透過 AS2 的 EDI 訊息](../core/media/57b7dc54-b8e8-462e-98d1-9cddedd14107.gif "57b7dc54-b8e8-462e-98d1-9cddedd14107")  
  
## <a name="the-functionality-in-this-solution"></a>此解決方案中的功能  
 下列項目適用於本逐步解說的功能：  
  
-   本逐步解說是處理 AS2 功能。 因此，與 AS2 處理有關的所有連接埠都是使用 AS2Receive 或 AS2Send 管線。 與 AS2 處理無關的連接埠，則使用 XMLReceive 或 PassThruTransmit 管線。  
  
-   本逐步解說會使用 XML 測試訊息。  
  
    > [!NOTE]
    >  您必須提供 XML 測試訊息和測試訊息的結構描述。  
  
-   沒有啟用狀態報告。  
  
-   這個解決方案不會設定簽章、壓縮、加密或不可否認性資料庫中的訊息存放區。 如需有關設定這些屬性的程序，請參閱[設定 AS2 屬性](../core/configuring-as2-properties.md)。  
  
## <a name="configuring-and-testing-the-walkthrough"></a>設定和測試逐步解說  
 這個解決方案所需的程序包含下列步驟：  
  
- 使用必要的訊息結構描述來建置並部署 BizTalk 專案，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用結構描述處理收到的訊息。  
  
- 讓 BTS ISAPI 篩選器可用於接收 AS2 訊息。  
  
- 建立 Fabrikam 虛擬目錄，用於接收 Contoso 的 AS2 訊息，如接收位置中所設定。  
  
- 指定 Fabrikam 虛擬目錄不是由 Windows SharePoint Services 管理。  
  
- 建立單向 FILE 接收埠，以接收要透過 AS2 傳輸來傳送的 XML 測試訊息。 建立本機資料夾，接收測試訊息。  
  
- 建立靜態請求-回應 HTTP 傳送埠、將傳送管線設定為 AS2Send 管線，以及將接收管線設定為 AS2Receive 管線。 連接埠將 AS2 訊息傳送到 Fabrikam，並接收 Fabrikam 的 MDN 回應，然後將它放到 MessageBox。  
  
- 建立雙向 HTTP 接收埠，以便讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收 AS2 訊息及傳送 MDN 回應。 設定接收管線為 AS2Receive 管線，並設定傳送管線為 AS2Send 管線。 設定接收位置，以透過 Fabrikam 虛擬目錄接收 AS2 訊息。  
  
  > [!NOTE]
  >  測試解決方案位於單一電腦上，因此，用於傳送 AS2 訊息 (自 Contoso 寄出) 的雙向傳送埠和用於接收 AS2 訊息 (由 Fabrikam 接收) 的雙向接收埠，皆位於相同電腦上。  
  
- 建立靜態單向 FILE 傳送埠 (具有通過傳送管線)，將訊息 XML 內容路由傳送至本機資料夾。 建立本機資料夾。  
  
  > [!NOTE]
  >  如果您沒有傳送埠可以訂閱訊息內容，那麼訊息內容就會擱置在 MessageBox 中。  
  
- 建立靜態單向 FILE 傳送埠 (具有通過傳送管線)，以將 MDN 路由傳送至本機資料夾。 建立本機資料夾。  
  
- 為 Fabrikam 與 Contoso 建立合作對象 (交易夥伴)。  
  
- 為這兩個交易合作對象各建立一個商務設定檔。  
  
- 在 Fabrikam 與 Contoso 的商務設定檔之間建立 AS2 協議。 AS2 協議應包含傳送 AS2 訊息及接收同步回傳之 MDN 的屬性。  
  
- 使用 XML 測試訊息測試逐步解說。  
  
### <a name="configuring-the-walkthrough"></a>設定逐步解說  
 本節說明設定逐步解說的程序。  
  
##### <a name="to-deploy-the-test-message-schema"></a>若要部署測試訊息結構描述  
  
1. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。  
  
   > [!NOTE]
   >  本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)， 如果沒有，請參閱[如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
2. 以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下**現有項目**。 若要使用 XML 檔案測試您的解決方案，請移至包含 XML 測試訊息之 XSD 結構描述的本機資料夾，然後選取該 XSD 檔案。 按一下 **[加入]**。  
  
3. 設定組件金鑰檔案，然後建置並部署組件。  
  
##### <a name="to-enable-the-bts-isapi-filter"></a>若要啟用 BTS ISAPI 篩選器  
  
1. 按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.  
  
   > [!TIP]
   >  視作業系統而定，[系統管理工具] 開始功能表選項可能無法使用。 在這種情況下，按一下**開始**，按一下**執行**，然後輸入`inetmgr`以開啟 Internet Information Services (IIS) 管理員。  
  
2. 選取根 Web 伺服器項目並在**功能檢視**，按兩下**處理常式對應**，然後在 動作 窗格中的，按一下 **新增指令碼對應**。  
  
   > [!NOTE]
   >  在 Web 伺服器層級設定指令碼對應會使得此對應套用至所有子網站。 若要限制對應至特定網站或虛擬資料夾，請選取目標網站或資料夾，而不要選取 Web 伺服器。  
  
3. 在 **新增指令碼對應**對話方塊方塊中，輸入`BtsHttpReceive.dll`中**要求路徑**欄位。  
  
4. 在 **可執行檔**欄位中，按一下 **省略符號 （...）** 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive。 選取 BtsHttpReceive.dll，然後按一下**確定**。  
  
5. 請輸入`BizTalk HTTP Receive`中`Name`欄位，，然後按一下**要求限制**。  
  
6. 在 **要求限制**對話方塊中，選取**動詞**索引標籤，然後選取**其中一個下列的指令動詞**。 輸入`POST`作為動詞。  
  
7. 在上**存取權**索引標籤上，選取**指令碼**，然後按一下 **確定**。  
  
8. 按一下  **確定**當系統提示您允許 ISAPI 延伸模組時，按一下**是**。  
  
##### <a name="to-configure-the-fabrikam-web-page"></a>若要設定 Fabrikam 網頁  
  
1. 在 [IIS 管理員] 中，以滑鼠右鍵按一下**應用程式集區**，然後選取**新增應用程式集區**。  
  
2. 在**新增應用程式集區**對話方塊方塊中，輸入**BizTalkAppPool**中**名稱**，然後選取 **.NET Framework v4.0.30210**中 **.NET framework 版本**下拉式清單。 按一下 [確定] 。  
  
   > [!NOTE]
   >  版本號碼可能會依據電腦上安裝的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 版本而有所不同。  
  
3. 選取**應用程式集區**，請在**功能檢視**選取**BizTalkAppPool**，然後按一下**進階設定**中**動作**窗格。  
  
4. 在 [**進階設定]** 對話方塊中，選取**識別**，然後按一下省略符號 （...） 按鈕。  
  
5. 在 **應用程式集區身分識別**對話方塊中，選取**自訂帳戶**，然後按一下 **設定**。  
  
6. 輸入**使用者名**並**密碼**使用者帳戶，系統管理員群組的成員，請輸入中的密碼**確認密碼**，然後按一下  **確定**三次，以返回 IIS 管理員。  
  
7. 在 [IIS 管理員] 中，開啟**站台**資料夾。 以滑鼠右鍵按一下**Default Web Site**節點，，然後選取**新增應用程式**。  
  
8. 在 **新增應用程式**對話方塊方塊中，輸入**Fabrikam**中**別名**，然後按一下**選取**。  
  
9. 在 **選取應用程式集區** 對話方塊中，選取**BizTalkAppPool** ，按一下  **確定**。  
  
10. 按一下省略符號 （...） 按鈕並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]針對 HttpReceive**實體路徑**。  
  
11. 按一下 [**測試設定**，並確認沒有顯示在錯誤**測試連接**] 對話方塊。 按一下 [關閉]，然後按一下 [確定]。  
  
12. 在 [IIS 管理員] 中，選取 Fabrikam 虛擬目錄並在**功能檢視**，按兩下**驗證**。  
  
13. 在 **驗證**頁面上，選取**匿名驗證**，並確認**狀態**是**已啟用**。 如果**狀態**是**停用**，按一下 **啟用**中**動作**窗格。  
  
##### <a name="to-specify-that-your-virtual-directory-is-not-managed-by-windows-sharepoint-services"></a>若要指定虛擬目錄不是由 Windows SharePoint Services 管理  
  
1.  如果 Windows SharePoint Services 安裝在電腦上，按一下**開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **SharePoint 3.0 管理中心**。  
  
    > [!NOTE]
    >  如果設定逐步解說的相同電腦中安裝了 Windows SharePoint Services，就必須執行這個程序。 在此情況下，您必須指定 IIS 虛擬目錄不是由 Windows SharePoint Server 管理。  
  
2.  在上**管理中心**頁面的 **管理中心**，按一下 **應用程式管理**。  
  
3.  在 **應用程式管理**頁面上，按一下**定義管理的路徑**。  
  
4.  在 **定義管理的路徑**頁面的 **加入新路徑**，請在**路徑**文字方塊中，輸入`Fabrikam`。 底下**型別**，按一下**排除的路徑**，然後按一下**確定**。  
  
##### <a name="to-create-a-receive-port-to-receive-the-test-message"></a>若要建立接收埠以接收測試訊息  
  
1. 在 Windows 檔案總管中，建立本機資料夾，以接收來自 Contoso 的 EDI 交換。  
  
2. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠**。  
  
3. 在 [**接收埠屬性**] 對話方塊中，接收埠命名為**RecvXMLFromCont**。  
  
4. 按一下 **接收位置**在主控台樹狀目錄中，然後按一下**新增**。  
  
5. 接收位置命名，選取**檔案**for**型別**，然後按一下**設定**。  
  
6. 針對**接收資料夾**，輸入您在步驟 1 中建立資料夾的名稱。  
  
7. 在 **檔案遮罩**，輸入 **\*.xml**，然後按一下**確定**。  
  
8. 在 接收管線中，選取**XMLReceive**。  
  
   > [!NOTE]
   >  如果您使用另一個非 EDI 以外的檔案類型，XML 中，輸入**PassThruTranmit**。  
  
9. 按一下  **確定**，然後按一下**確定**一次。  
  
10. 按一下 **接收位置**節點，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。  
  
##### <a name="to-create-a-send-port-to-send-the-as2-message-to-fabrikam"></a>建立傳送埠以將 AS2 訊息傳送至 Fabrikam  
  
1. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態請求-回應傳送埠**。  
  
   > [!NOTE]
   >  如果使用 [BizTalk Application 1]，您必須在 [BizTalk Application 1] 中加入「BizTalk EDI 應用程式」的參考，讓應用程式使用其成品。 如需詳細資訊，請參閱 <<c0> [ 如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
2. 在 [**傳送埠屬性**] 對話方塊中，將傳送埠命名為**SendToFab_RecvMDN**。  
  
3. 在 **傳輸**區段中，選取**HTTP**如**類型**，然後按一下 **設定**。  
  
4. 在 [ **HTTP 傳輸屬性**] 對話方塊中，如**目的地 URL**，輸入**http://localhost/Fabrikam/BTSHttpReceive.dll**。  
  
5. 清除**啟用區塊編碼**。 按一下 [確定] 。  
  
6. 針對**傳送管線**，選取**AS2Send**。  
  
7. 針對**接收管線**，選取**AS2Receive**。  
  
8. 在主控台樹狀目錄中，選取**篩選器**。 針對**屬性**，輸入**BTS。ReceivePortName**; 對於**運算子**，輸入**==**; 及針對**值**輸入將接收 EDI 接收埠的名稱交換 (`RecvXMLFromCont`)。  
  
   > [!NOTE]
   >  如果您要傳送 PIDX 訊息，您可以建立篩選的篩選條件運算式的訊息類型 (**PIDX**)。  
  
9. 如果您想要套用對應來轉換 XML 文件，請按一下**輸出對應**在主控台樹狀目錄中。 請輸入**來源文件**輸出對應中，選取**地圖**，然後輸入**目標文件**。 按一下 [確定] 。  
  
10. 按一下 [確定] 。  
  
11. 按一下 **傳送埠**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下您的傳送埠，然後**啟動**。  
  
##### <a name="to-create-a-receive-port-to-receive-the-as2-message-and-return-an-acknowledgment"></a>若要建立接收埠以接收 AS2 訊息並傳回通知  
  
1. 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，底下**BizTalk Application 1** ] 節點，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下 [ **要求回應接收埠**。  
  
2. 接收埠命名為**RecvAS2Msg**，然後按一下**接收位置**在主控台樹狀目錄中。  
  
3. 按一下 **[新增]**。  
  
4. 中**接收位置屬性**對話方塊中，名稱您接收位置中，選取**HTTP**如**型別**，然後按一下**設定**。  
  
5. 在  **HTTP 傳輸屬性**對話方塊方塊中，輸入 **/Fabrikam/BTSHttpReceive.dll** for**虛擬目錄加 ISAPI 延伸模組**。 清除**成功時傳回相互關聯控制代碼**，然後選取**擱置失敗的要求**。 按一下 [確定] 。  
  
6. 選取**AS2Receive** for**接收管線**，並**AS2Send**如**傳送管線**。 按一下  **確定**，然後按一下**確定**一次。  
  
7. 按一下 **接收位置**節點，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。  
  
##### <a name="to-create-a-send-port-to-send-the-test-xml-payload-to-a-local-folder"></a>若要建立傳送埠以將測試 XML 內容傳送至本機資料夾  
  
1. 在 Windows 檔案總管中，建立本機資料夾，以便將 EDI 交換傳送至此本機資料夾。  
  
2. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。  
  
3. 在 **傳送埠屬性**對話方塊中，將傳送埠作為**SendXMLPayload**。 選取 **檔案**for**型別**，然後按一下**設定**。  
  
4. 在 [ **FILE 傳輸屬性**] 對話方塊中，如**目的地資料夾**，輸入您建立之 EDI 內容的本機資料夾。  
  
5. 針對**檔案名**，輸入檔案名稱。 如果您使用的 XML 檔案做為測試訊息，請輸入 **%MessageID%.xml**。 按一下 [確定] 。  
  
6. 接受預設值是**PassThruTransmit** for**傳送管線**。  
  
7. 按一下 **篩選器**在主控台樹狀結構，並加入挑選 EDI 內容的篩選屬性。 在第一行，如**屬性**，輸入**BTS。ReceivePortName**; 對於**運算子**，輸入**==**; 對於**值**，輸入接收的 AS2 接收埠的名稱訊息 (`RecvAS2Msg`); 至於**分組**，接受**和**。 在第二行，如**屬性**，輸入**EdiIntAS.IsAS2PayloadMessage**; 對於**運算子**，輸入**==**; 以及**值**，輸入 **，則為 True**。  
  
8. 按一下 [確定] 。  
  
9. 按一下 **傳送埠**節點，以滑鼠右鍵按一下您的傳送埠，然後**開始**。  
  
##### <a name="to-create-a-send-port-to-send-the-mdn-to-a-local-folder"></a>若要建立傳送埠以將 MDN 傳送至本機資料夾  
  
1. 在 Windows 檔案總管中，建立本機資料夾，以便將 MDN 傳送至此本機資料夾。  
  
2. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。  
  
3. 在 **傳送埠屬性**對話方塊中，將傳送埠作為**SendMDNToContoso**。 選取 **檔案**for**型別**，然後按一下**設定**。  
  
4. 在 [ **FILE 傳輸屬性**] 對話方塊中，如**目的地資料夾**，輸入您要建立為 MDN 傳送目標的本機資料夾。  
  
5. 針對**檔名**，輸入 **%MessageID%.msg**。按一下 **確定**。  
  
6. 接受預設值是**PassThruTransmit** for**傳送管線**。  
  
7. 按一下 **篩選器**在主控台樹狀目錄中。 針對**屬性**，輸入**BTS。SPName**; 對於**運算子**，輸入**==**; 對於**值**，輸入傳送 AS2 訊息的傳送埠的名稱 (`SendToFab_RecvMDN`);至於**分組**，接受**和**。 在第二行中，如**屬性**，輸入**EdiIntAS.IsAS2MdnResponseMessage**。 針對**運算子**，輸入**==**。 針對**值**，輸入 **，則為 True**。  
  
8. 按一下 [確定] 。  
  
9. 按一下 **傳送埠**節點，以滑鼠右鍵按一下您的傳送埠，然後**開始**。  
  
##### <a name="to-create-a-party-and-a-business-profile-for-fabrikam"></a>若要為 Fabrikam 建立合作對象與商務設定檔  
  
1. 以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。  
  
2. 輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。  
  
   > [!NOTE]
   >  藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. 據此，建立協議時將會啟用或停用某些屬性。 不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。  
  
3. 以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。  
  
4. 在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**fabrikam_profile**中**名稱**文字方塊。  
  
   > [!NOTE]
   >  當您建立合作對象時，會同時建立設定檔。 您可以重新命名再使用該設定檔，而不需建立新設定檔。 若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。 在 **一般**頁面上，指定設定檔的名稱。  
  
##### <a name="to-create-a-party-and-a-business-profile-for-contoso"></a>若要為 Contoso 建立合作對象與商務設定檔  
  
1. 以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。  
  
2. 輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。  
  
   > [!NOTE]
   >  藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. 據此，建立協議時將會啟用或停用某些屬性。 不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。  
  
3. 以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。  
  
4. 在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**contoso_profile**中**名稱**文字方塊。  
  
   > [!NOTE]
   >  當您建立合作對象時，會同時建立設定檔。 您可以重新命名再使用該設定檔，而不需建立新設定檔。 若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。 在 **一般**頁面上，指定設定檔的名稱。  
  
##### <a name="to-create-an-as2-agreement-between-the-two-business-profiles"></a>若要建立兩個商務設定檔之間的 AS2 協議  
  
1.  以滑鼠右鍵按一下 **[contoso_profile]**，指向**新增**，然後按一下**協議**。  
  
2.  在 [**一般屬性**] 頁面上，如**名稱**文字方塊中，輸入協議的名稱。  
  
3.  從**通訊協定**下拉式清單中，選取**AS2**。  
  
4.  在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Fabrikam**。  
  
5.  在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**fabrikam_profile**。  
  
     您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向 AS2 協議。  
  
6.  在上執行下列工作**Contoso-> Fabrikam**  索引標籤。  
  
    1.  上**識別碼**頁面上，輸入值**AS2-從**並**AS2-以**。 針對**AS2-從**，輸入`Contoso`。 針對**AS2-To**，輸入`Fabrikam`。  
  
    2.  在 **通知 (Mdn)** 頁面上，執行下列動作：  
  
        1.  選取 **針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**核取方塊。  
  
            > [!NOTE]
            >  檢查**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**所需的測試此逐步解說中，因為則只會傳回的 MDN 放入 MessageBox。 而您也才可以建立傳送埠訂閱 MDN、將 MDN 傳送到本機目錄，好讓您確認 AS2 傳輸。  
  
        2.  選取 **的 要求 MDN**核取方塊。  
  
        3.  請確定**要求簽署的 MDN**核取方塊。  
  
        4.  離開**要求非同步 MDN**清除。  
  
        5.  在 **配置通知到**，輸入任何值。 在 AS2 處理期間並不會使用這個欄位值，但還是必須在該欄位中輸入值。  
  
    3.  在 **傳送埠**頁面上，建立將用來傳送 EDI 交換給 Fabrikam 的雙向傳送埠的關聯。 在 **傳送埠**格線底下**名稱**資料行中，按一下空白儲存格，並從下拉式清單中，選取 傳送埠**SendToFab_RecvMDN**。  
  
7.  在上執行下列工作**Fabrikam-> Contoso**  索引標籤。  
  
    > [!NOTE]
    >  在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。 若要成功建立協議，兩個單向協議索引標籤必須已定義的值**AS2_From**並**AS2-以**。  
  
    1.  上**識別碼**頁面上，輸入值**AS2-從**並**AS2-以**。 針對**AS2-從**，輸入`Fabrikam`。 針對**AS2-To**，輸入`Contoso`。  
  
8.  按一下 **[套用]**。  
  
9. 按一下 [確定] 。 中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。 預設會啟用新增的協議。  
  
### <a name="testing-the-walkthrough"></a>測試逐步解說  
 本節提供關於如何測試逐步解說的資訊。  
  
##### <a name="to-test-the-solution"></a>測試方案  
  
1.  在 [Windows 檔案總管] 中，將 XML 測試檔案貼入到您為了接收 Contoso 測試訊息而建立的本機資料夾。  
  
2.  移至您建立用來傳送 XML 內容的本機資料夾。 確認該資料夾包含 XML 檔案。 開啟檔案和原始測試訊息，並確認其內容是相同的。  
  
3.  移至您建立用來做為結果 MDN 之傳送目標的本機資料夾。 確認該資料夾包含一個檔案，開啟該檔案並確認是否為 MDN 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)   
 [透過 AS2 從傳送端處理外寄非 EDI 訊息](../core/send-side-processing-of-an-outgoing-non-edi-message-over-as2.md)