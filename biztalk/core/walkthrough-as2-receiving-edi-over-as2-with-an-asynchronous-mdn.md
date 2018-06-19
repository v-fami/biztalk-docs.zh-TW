---
title: '逐步解說 (AS2): 使用非同步 MDN 透過 AS2 接收 EDI |Microsoft 文件'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3962e4-0525-4194-8cf1-b90664f1a139
caps.latest.revision: 40
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0dd9e94ff74adb4419f95b386861376bb424fd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22292398"
---
# <a name="walkthrough-as2-receiving-edi-over-as2-with-an-asynchronous-mdn"></a>逐步解說 (AS2)：使用非同步 MDN 透過 AS2 接收 EDI
本逐步解說提供一組逐步執行的程序，可建立透過 AS2 傳輸接收 EDI 訊息並傳回同步 MDN 的解決方案。  
  
## <a name="prerequisites"></a>必要條件  
 以下是執行此主題中之程序的必要條件：  
  
-   您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
-   執行逐步解說的電腦必須安裝 Internet Information Services (IIS) 7。  
  
-   若執行逐步解說的電腦是安裝 64 位元版本的 Windows，您必須確定 BizTalk 主機只標示為 32 位元。 您也必須確定 IIS 已將應用程式集區的「啟用 32 位元應用程式」設定為 True。 如需詳細資訊，請參閱[教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)。  
  
## <a name="how-the-solution-receives-an-edi-interchange-and-returns-an-asynchronous-mdn"></a>解決方案接收 EDI 交換並傳回非同步 MDN 的方式  
 解決方案會執行下列作業：  
  
1.  透過 HTTP 從交易夥伴接收包含 EDI 交換的 AS2 訊息，並從 EDIINT/AS2 解碼此交換。  
  
    > [!NOTE]
    >  這份清單中的事件可能不會按照所示的順序發生。  
  
2.  產生 MDN 回應，然後將它放置在 MessageBox 中。  
  
3.  動態傳送埠取用訊息 MDN。  
  
4.  將非同步訊息 MDN 傳回給交易夥伴。  
  
5.  將交換的 EDI 格式轉換為內部 XML 格式，然後將它放置在 MessageBox 中。  
  
6.  具有 PassThruTransmit 管線的傳送埠從 MessageBox 接收訊息 XML 檔案。  
  
7.  傳送埠將 EDI 交換 XML 檔案傳送至 Contoso 合作對象的資料夾。  
  
 下圖顯示這個解決方案的架構。  
  
 ![使用非同步 MDN 的 AS2 接收](../core/media/bts-configuring-the-receiving-of-edi-over-as2-with-an-asynchronous-mdnc.gif "bts_Configuring_the_Receiving_of_EDI_Over_AS2_with_an_Asynchronous_MDNc")  
  
## <a name="the-functionality-in-this-solution"></a>此解決方案中的功能  
 下列項目適用於本逐步解說的功能：  
  
-   不會產生 EDI 通知。 產生 EDI 通知中示範[(X12) 逐步解說： 接收 EDI 交換並傳送傳回通知](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)。 透過 AS2 傳輸傳送 EDI 通知述[逐步解說 (AS2): 使用非同步 MDN 透過 AS2 傳送的 EDI](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md)。  
  
-   這個解決方案是專為使用 X12 編碼 (而非 EDIFACT 編碼) 的交換所設計。  
  
    > [!NOTE]
    >  EDIFACT 編碼使用的組態與 X12 編碼使用的組態近乎平行。  
  
-   將針對內送交換執行 EDI 類型和擴充驗證。  
  
-   將會啟用 AS2 和 EDI 報告，而且將會儲存交易集，然後從交換狀態報告中檢視交易集。  
  
-   這個解決方案不會設定簽章、壓縮、加密或不可否認性資料庫中的訊息存放區。 如需有關設定這些屬性的程序，請參閱[設定 AS2 屬性](../core/configuring-as2-properties.md)。  
  
## <a name="configuring-and-testing-the-walkthrough"></a>設定和測試逐步解說  
 這個解決方案所需的程序包含下列步驟：  
  
-   使用必要的訊息結構描述來建置並部署 BizTalk 專案，因此 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用結構描述處理收到的交換。  
  
-   讓 BTS ISAPI 篩選器可用於接收 AS2 訊息。  
  
-   建立會從 Fabrikam 接收 AS2 訊息的 Contoso 虛擬目錄 (如接收位置中所設定)。  
  
-   建立會從 Contoso 接收 MDN 的 Fabrikam 虛擬目錄。  
  
-   指定 Contoso 和 Fabrikam 虛擬目錄不是由 Windows SharePoint Services 管理。  
  
-   建立靜態單向 HTTP 接收埠，以便讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 從交易夥伴接收包含 EDI 商業文件的 AS2 訊息。 將接收管線設定為 AS2EDIReceive 管線。  
  
-   建立動態單向 HTTP 傳送埠，以便讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送 MDN 來回應收到的 AS2 訊息。  
  
    > [!NOTE]
    >  這個傳送埠會訂閱以 EdiIntAS.IsAS2AsynchronousMDN 屬性 (由 AS2EdiReceive 管線設定為 True) 和相互關聯之 Token 為基礎的 MDN。 傳送埠必須是動態，才能將 MDN 傳送至訊息標頭內 Receipt-Delivery-Notification 一行中的地址。  
  
-   建立靜態單向 FILE 傳送埠，以將 EDI 內容 (XML 格式) 路由傳送至本機資料夾。 建立本機資料夾。  
  
-   為 Fabrikam 與 Contoso 建立合作對象 (交易夥伴)。  
  
-   為這兩個交易合作對象各建立一個商務設定檔。  
  
-   在 Fabrikam 與 Contoso 的商務設定檔之間建立 AS2 協議。 這個 AS2 協議包含的屬性將可用來傳送 AS2 訊息並接收回傳的同步 MDN。  
  
-   在 Fabrikam 與 Contoso 的商務設定檔之間建立 X12 協議，以便接收 X12 訊息。  
  
-   使用 AS2 教學課程檔案中隨附的 HTTP 傳送者公用程式，測試此解決方案。 這個公用程式會傳送測試 AS2 訊息，其中包含透過 AS2 傳輸的 EDI 交換。 這個公用程式會傳送測試 AS2 訊息，其中包含透過 AS2 傳輸的 EDI 交換 (AS2 教學課程中隨附的 X12_00401_864.edi)。 針對這個逐步解說使用的「HTTP 傳送者」和測試訊息與教學課程隨附的版本相同。  
  
### <a name="configuring-the-walkthrough"></a>設定逐步解說  
 本節說明設定逐步解說的程序。  
  
##### <a name="to-deploy-the-message-schema"></a>若要部署訊息結構描述  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟專案 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas\Schemas.btproj。  
  
    > [!NOTE]
    >  這個專案 (隨附於 AS2 教學課程) 包含了搭配測試訊息使用的 864 結構描述。  
  
    > [!NOTE]
    >  本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)， 如果沒有，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
2.  以滑鼠右鍵按一下**結構描述**專案在 [方案總管] 中，然後按一下**屬性**。 按一下**簽署** 索引標籤中的專案設計工具中，核取**簽署組件**核取方塊，然後從下拉式清單中，選取**新增**並提供必要的值，建立強式名稱金鑰檔案。 儲存變更，然後關閉專案屬性視窗。  
  
3.  建置並部署 Schemas.btproj。  
  
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
  
6.  在 要求限制 對話方塊中，選取**動詞**索引標籤，然後選取 **下列動詞命令的其中一個**。 輸入`POST`為動詞命令。  
  
7.  在**存取**索引標籤上，選取**指令碼**，然後按一下 **確定**。  
  
8.  按一下**確定**時提示您允許 ISAPI 延伸模組，請按一下 **是**。  
  
##### <a name="to-configure-the-contoso-web-page"></a>若要設定 Contoso 網頁  
  
1.  在 [IIS 管理員] 中，以滑鼠右鍵按一下**應用程式集區**選取**新增應用程式集區**。  
  
2.  在**新增應用程式集區**對話方塊方塊中，輸入**BizTalkAppPool**中**名稱**，然後選取 **.NET Framework v4.0.30210**中 **.NET framework 版本**下拉式清單。 按一下 **[確定]**。  
  
    > [!NOTE]
    >  版本號碼可能會依據電腦上安裝的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 版本而有所不同。  
  
3.  選取**應用程式集區**，在 功能檢視 中選取**BizTalkAppPool**，然後按一下 **進階設定**中**動作**窗格。  
  
4.  在**進階設定**對話方塊中，選取**識別**，然後按一下 [**省略符號 （...）** ] 按鈕。  
  
5.  在**應用程式集區識別**對話方塊中，選取**自訂帳戶**，然後按一下 **設定**。  
  
6.  輸入**使用者名**和**密碼**是 administrators 群組的成員的使用者帳戶，請輸入中的密碼**確認密碼**然後按一下  **確定**傳回給 IIS Manager 中的三倍。  
  
7.  在 [IIS 管理員] 中，開啟**網站**資料夾。 以滑鼠右鍵按一下**Default Web Site**節點，然後再選取**新增應用程式**。  
  
8.  在**新增應用程式**對話方塊方塊中，輸入**Contoso**中**別名**文字方塊，然後再按一下**選取**。  
  
9. 中**選取應用程式集區**對話方塊中，選取**BizTalkAppPool**按一下**確定**。  
  
10. 如**實體路徑**，按一下 **省略符號 （...）** 按鈕並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive。  
  
11. 按一下**測試設定**並確認沒有顯示在錯誤**測試連接** 對話方塊。 按一下 [關閉]，然後按一下 [確定]。  
  
12. 在 [IIS 管理員] 中，選取 Contoso 虛擬目錄和**功能檢視**，連按兩下**驗證**。  
  
13. 在**驗證**頁面上，選取**匿名驗證**並確認**狀態**是**啟用**。 如果**狀態**是**已停用**，按一下 **啟用**中**動作**窗格。  
  
##### <a name="to-configure-the-fabrikam-web-page"></a>若要設定 Fabrikam 網頁  
  
1.  在 [IIS 管理員] 中，開啟**網站**資料夾。 以滑鼠右鍵按一下**Default Web Site**節點，然後再選取**新增應用程式**。  
  
2.  在**新增應用程式**對話方塊方塊中，輸入**Fabrikam**中**別名**，然後按一下 **選取**。  
  
3.  中**選取應用程式集區**對話方塊中，選取**BizTalkAppPool**按一下**確定**。  
  
4.  如**實體路徑**，按一下 [**省略符號 （...）** 按鈕並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 tutorial\fabrikam]。  
  
5.  按一下**測試設定**並確認沒有顯示在錯誤**測試連接** 對話方塊。 按一下 [關閉]，然後按一下 [確定]。  
  
6.  在 [IIS 管理員] 中，選取 Contoso 虛擬目錄和**功能檢視**，連按兩下**驗證**。  
  
7.  在**驗證**頁面上，選取**匿名驗證**並確認**狀態**是**啟用**。 如果**狀態**是**已停用**，按一下 **啟用**中**動作**窗格。  
  
##### <a name="to-specify-that-your-virtual-directory-is-not-managed-by-windows-sharepoint-services"></a>若要指定虛擬目錄不是由 Windows SharePoint Services 管理  
  
1.  如果 Windows SharePoint Services 安裝在電腦上，按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下  **SharePoint 3.0 管理中心**。  
  
    > [!NOTE]
    >  如果設定逐步解說的相同電腦中安裝了 Windows SharePoint Services，就必須執行這個程序。 在此情況下，您必須指定 IIS 虛擬目錄不是由 Windows SharePoint Server 管理。  
  
2.  在**管理中心**頁面的 **管理中心**，按一下 **應用程式管理**。  
  
3.  在**應用程式管理**頁面上，按一下**定義管理的路徑**。  
  
4.  在**定義管理的路徑**頁面的 **新增路徑**，請在**路徑**文字方塊中，輸入**Contoso**。 在下**類型**，按一下**排除的路徑**，然後按一下**確定**。  
  
5.  針對 Fabrikam 虛擬目錄重複步驟 4。  
  
##### <a name="to-create-a-receive-port-to-receive-the-edi-interchange-over-as2-from-fabrikam"></a>若要建立接收埠以透過 AS2 接收來自 Fabrikam 的 EDI 交換  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠**。  
  
2.  將接收連接埠，再按一下**接收位置**在主控台樹狀目錄中。  
  
3.  按一下 **[新增]**。  
  
4.  接收位置命名，選取**HTTP**如**類型**，然後按一下 **設定**。  
  
5.  如**虛擬目錄加 ISAPI 延伸模組**，輸入`/Contoso/BTSHTTPReceive.dll`。  
  
6.  選取**擱置失敗的要求**核取方塊，然後按一下**確定**。  
  
7.  如**接收管線**，選取**AS2EDIReceive**。  
  
8.  按一下**確定**，然後按一下 **確定**一次。  
  
9. 在**接收位置**窗格[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下接收位置，然後**啟用**。  
  
##### <a name="to-create-a-dynamic-send-port-to-send-the-mdn-to-fabrikam"></a>若要建立動態傳送埠以將 MDN 傳送至 Fabrikam  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **動態單向傳送埠**。  
  
2.  在**傳送埠屬性**對話方塊、 傳送埠的名稱。  
  
3.  如**傳送管線**，選取**AS2Send**。  
  
4.  在主控台樹狀目錄中，選取**篩選**。 如**屬性**，輸入**EdiIntAS.IsAS2AsynchronousMDN**;**運算子**，輸入 **==** ; 以及**值**，輸入**True**。  
  
5.  按一下 **[確定]**。  
  
##### <a name="to-create-a-send-port-to-send-the-edi-payload-to-a-local-folder"></a>若要建立傳送埠以將 EDI 內容傳送至本機資料夾  
  
1.  在 Windows 檔案總管，建立名為的 Contoso 本機資料夾**EDI_to_Contoso**來傳送 EDI 內容。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊中，將傳送埠，例如**Send_Payload**。 選取**檔案**如**類型**，然後按一下 **設定**。  
  
4.  在**FILE 傳輸屬性**對話方塊中，針對**目的地資料夾**、 瀏覽並選取**EDI_to_Contoso**您在步驟 1 中建立的資料夾。 保留**檔案名稱**為 **%MessageID%.xml**。 按一下 **[確定]**。  
  
5.  接受預設值是**PassThruTransmit**如**傳送管線**。  
  
6.  按一下**篩選**在主控台樹狀目錄中。 如**屬性**，輸入**BTS。MessageType**。 如**運算子**，輸入 **==** 。 如**值**，輸入您的訊息，訊息類型`http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_864`。  
  
7.  按一下 **[確定]**。  
  
8.  在**傳送埠**窗格[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下傳送埠，然後**啟動**。  
  
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
  
1.  以滑鼠右鍵按一下**fabrikam_profile**，指向 **新增**，然後按一下 **協議**。  
  
2.  在**一般屬性** 頁面上，針對**名稱**文字方塊中，輸入協議的名稱。  
  
3.  從**通訊協定**下拉式清單中，選取**AS2**。  
  
4.  在**第二個夥伴** 區段中，從**名稱**下拉式清單中，選取**Contoso**。  
  
5.  在**第二個夥伴** 區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。  
  
     您會發現兩個新的索引標籤取得旁新增**一般** 索引標籤。每個索引標籤各用於設定一個單向 AS2 協議。  
  
6.  在**一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**。  
  
7.  在上執行下列工作**Fabrikam-> Contoso**  索引標籤。  
  
    1.  在**識別碼**頁面上，輸入的值**AS2-從**和**AS2-要**。 如**AS2-從**，輸入`Fabrikam`。 如**AS2-To**，輸入`Contoso`。  
  
    2.  在**驗證**頁面上，選取**對驗證與 MDN 使用協議設定，而非訊息標頭**核取方塊  
  
    3.  在**通知 (Mdn)** 頁面上，執行下列動作：  
  
        1.  選取**要求 MDN**核取方塊。  
  
        2.  請確定**要求簽署的 MDN**核取方塊。  
  
        3.  選取**要求非同步 MDN**核取方塊。  
  
        4.  在**回條傳遞選項 (URL)** 文字方塊中，輸入`http://localhost/Fabrikam/Default.aspx?Destination=_MDNToFabrikam`。  
  
8.  在上執行下列工作**Contoso-> Fabrikam**  索引標籤。  
  
    > [!NOTE]
    >  在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。 若要成功地建立協議，兩個單向協議索引標籤必須已定義的值**AS2-從**和**AS2-要**。  
  
    1.  在**識別碼**頁面上，輸入的值**AS2-從**和**AS2-要**。 如**AS2-從**，輸入`Contoso`。 如**AS2-To**，輸入`Fabrikam`。  
  
9. 按一下 **[套用]**。  
  
10. 按一下 **[確定]**。 新增的協議會列在**協議**區段**合作對象與商務設定檔**窗格。 預設會啟用新增的協議。  
  
##### <a name="to-create-an-x12-agreement-between-the-two-business-profiles"></a>若要建立兩個商務設定檔之間的 X12 協議  
  
1.  以滑鼠右鍵按一下**fabrikam_profile**，指向 **新增**，然後按一下 **協議**。  
  
2.  在**一般屬性** 頁面上，針對**名稱**文字方塊中，輸入協議的名稱。  
  
3.  從**通訊協定**下拉式清單中，選取**X12**。  
  
4.  在**第二個夥伴** 區段中，從**名稱**下拉式清單中，選取**Contoso**。  
  
5.  在**第二個夥伴** 區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。  
  
     您會發現兩個新的索引標籤取得旁新增**一般** 索引標籤。每個索引標籤各用於設定一個單向 X12 協議。  
  
6.  在**一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，然後選取**儲存報告的訊息內容**。  
  
7.  在上執行下列工作**Fabrikam-> Contoso**  索引標籤。  
  
    1.  在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。  
  
        > [!NOTE]
        >  對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。 它會比對的值**ISA5**， **ISA6**， **ISA7**，和**ISA8**交換標頭與協議屬性中。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 來解析協議。 若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。  
  
        > [!NOTE]
        >  這個逐步解說中，設定**ISA5**至**ZZ**， **ISA6**至**7654321**， **ISA7**至**ZZ**，和**ISA8**至**1234567**。  
  
    2.  在**驗證**頁面**交換設定**區段中，請確定**檢查重複的 ISA13**未選項。  
  
        > [!NOTE]
        >  清除**檢查重複的 ISA13**屬性可讓您接收相同訊息的多個執行個體。  
  
    3.  如果您使用隨附之標準結構描述的其中一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上**本機主機設定**頁面**交易集設定**區段中，選取要用於結構描述的命名空間處理內送交換。  
  
        |使用|動作|  
        |--------------|----------------|  
        |**預設值**|選取欄中的核取方塊|  
        |**目標命名空間**|選取 [ `http://schemas.microsoft.com/BizTalk/EDI/X12/2006`]。|  
  
        > [!NOTE]
        >  設定屬性可以讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 判斷要用於處理內送 850 交換的結構描述。 如果交換的 GS02 和 ST01 值是輸入在格線行中，則將會使用同一行的目標命名空間來判斷要使用的結構描述。  
  
    4.  在**信封**頁面**交易集設定**區段中，執行下列動作：  
  
        |使用|動作|  
        |--------------|----------------|  
        |**預設值**|選取**預設**。 **注意：** 當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **GS7**，和**GS8**可用即使值**交易類型**，**版本/版次**，和**目標命名空間**都不符合訊息。|  
        |**交易類型**|例如，選取您的測試訊息的訊息類型**864-文字訊息**。|  
        |**版本/版次**|輸入**00401**。|  
        |**目標命名空間**|選取**http://schemas.microsoft.com/BizTalk/EDI/X12/2006**。|  
        |**GS1**|確認已選取測試訊息的訊息類型，例如**TX-簡訊 (864)**。|  
        |**GS2**|輸入**01**。|  
        |**GS3**|輸入**7654321**。|  
        |**GS4**|選取您想要的日期格式。 選取**CCYYMMDD**。 **注意：** 您必須在下拉式清單中選取值，不只是按一下欄位以顯示預設值。 如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。|  
        |**GS5**|選擇您要的時間格式。 選取 **[hhmmssdd]**。|  
        |**GS7**|選取**T-Transportation Data Coordinating Committee (TDCC)**。|  
        |**GS8**|請確認已輸入 EDI 版本做**00401**。|  
  
8.  在上執行下列工作**Contoso-> Fabrikam**  索引標籤。  
  
    > [!NOTE]
    >  在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。 若要成功地建立協議，兩個單向協議索引標籤必須已定義的值**ISA5**， **ISA6**， **ISA7**，和**ISA8**。  
  
    1.  在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。  
  
        > [!NOTE]
        >  這個逐步解說中，設定**ISA5**至**ZZ**， **ISA6**至**1234567**， **ISA7**至**ZZ**，和**ISA8**至**7654321**。  
  
9. 按一下 **[套用]**。  
  
10. 按一下 **[確定]**。 新增的協議會列在**協議**區段**合作對象與商務設定檔**窗格。 預設會啟用新增的協議。  
  
### <a name="testing-the-walkthrough"></a>測試逐步解說  
 本節提供關於如何測試逐步解說的資訊。  
  
##### <a name="to-test-the-solution"></a>測試方案  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender 資料夾中的 Sender.csproj 專案。  
  
2.  在 HttpSender.cs 中，確定下列程式碼行未標記為註解 (緊接在 //Request Asynchronous MDN 註解行底下)：  
  
    ```  
    Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864.edi", FileMode.Open, FileAccess.Read);  
    ```  
  
3.  確定下列程式碼行已標記為註解 (緊接在 //Request Synchronous MDN 註解行底下)：  
  
    ```  
    Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864-Sync.edi", FileMode.Open, FileAccess.Read);  
    ```  
  
4.  建置這個專案。  
  
5.  在 Windows 檔案總管中，移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial。 在 [記事本] 中開啟 X12_00401_864.edi。 刪除定義 Disposition-Notification-Options 標頭的一行，然後儲存檔案。  
  
6.  在 Windows 檔案總管 中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug，然後執行**Sender.exe**。  
  
    > [!NOTE]
    >  這時執行 Sender.exe 會將訊息 X12_00401_864.edi 傳送至 Contoso 虛擬目錄 (BTS http 接收位置)。  
  
7.  開啟為傳送 EDI 內容所建立的 Contoso 本機資料夾 (\EDI_to_Contoso)。 確認資料夾中有 .XML 檔案。 開啟這個 XML 檔案，並確認它包含 864 交易集。  
  
8.  開啟要將 MDN 傳回到的 Fabrikam 本機資料夾。 在 Windows 檔案總管 中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_MDNToFabrikam。 在記事本中開啟訊息檔案並確認 MDN。 確認 MDN 的 AS2-From 是 Contoso，而 AS2-To 則是 Fabrikam。  
  
9. 在 [記事本] 中開啟測試訊息 X12_00401_864.edi，並確認 \EDI_to_Contoso 本機資料夾中輸出訊息的交易集對應至 X12_00401_864.edi 輸入訊息的交易集。  
  
## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)