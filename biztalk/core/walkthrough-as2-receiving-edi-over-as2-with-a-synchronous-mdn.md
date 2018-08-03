---
title: '逐步解說 (AS2): 使用同步 MDN 透過 AS2 接收 EDI |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b63395f-03f4-45e8-a68a-9bbbd8dfa344
caps.latest.revision: 53
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 971620284a8058663f7c054cd6286cbd01d81d84
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024012"
---
# <a name="walkthrough-as2-receiving-edi-over-as2-with-a-synchronous-mdn"></a>逐步解說 AS2)：使用同步 MDN 透過 AS2 接收 EDI
本逐步解說提供一組逐步執行的程序，可建立透過 AS2 傳輸接收 EDI 訊息並傳回同步 MDN 的解決方案。  

## <a name="prerequisites"></a>必要條件  
 下列是執行本主題所述程序的必要條件：  

- 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  

- 執行逐步解說的電腦必須安裝 Internet Information Services (IIS) 7。  

- 若執行逐步解說的電腦是安裝 64 位元版本的 Windows，您必須確定 BizTalk 主機只標示為 32 位元。 您也必須確定 IIS 已啟用 32 位元應用程式設定，應用程式集區設定為 **，則為 True**。 如需詳細資訊，請參閱 <<c0> [ 教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)。  

## <a name="how-the-solution-receives-an-edias2-message-and-returns-a-synchronous-mdn"></a>解決方案如何接收 EDI/AS2 訊息並傳回同步 MDN  
 這個解決方案會執行下列作業：  

1. 透過 HTTP 從交易夥伴 Fabrikam 接收包含 EDI 交換的 AS2 訊息，並從 EDIINT/AS2 解碼此交換。  

   > [!NOTE]
   >  這份清單中的事件可能不會按照所示的順序發生。  

2. 使用要求-回應接收埠將同步 MDN 傳回給交易夥伴。  

3. 將交換的 EDI 格式轉換為內部 XML 格式，然後將它放置在 MessageBox 中。  

4. 具有 PassThruTransmit 管線的 FILE 傳送埠接收訊息 XML 檔案。  

5. 傳送埠將 EDI 交換 XML 檔案傳送至 Contoso 合作對象的資料夾。  

   下圖顯示這個解決方案的架構。  

   ![使用同步 MDN 的 AS2 接收](../core/media/4ff20070-1c36-42e5-af14-832771d63b88.gif "4ff20070-1c36-42e5-af14-832771d63b88")  

## <a name="the-functionality-in-this-solution"></a>此解決方案中的功能  
 下列項目適用於本逐步解說的功能：  

-   不會產生 EDI 通知。 產生 EDI 通知所示[逐步解說 (X12)： 接收 EDI 交換和傳送，將通知傳回](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)。 傳送 EDI 通知，透過 AS2 傳輸所述[逐步解說 (AS2): 使用同步 MDN 透過 AS2 傳送的 EDI](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md)。  

-   這個解決方案是專為使用 X12 編碼 (而非 EDIFACT 編碼) 的交換所設計。  

    > [!NOTE]
    >  EDIFACT 編碼使用的組態與 X12 編碼使用的組態近乎平行。  

-   將針對內送交換執行 EDI 類型和擴充驗證。  

-   將會啟用 AS2 和 EDI 報告，而且將會儲存交易集，然後從交換狀態報告中檢視交易集。  

-   這個解決方案不會設定簽章、壓縮、加密或不可否認性資料庫中的訊息存放區。 如需有關設定這些屬性的程序，請參閱[設定 AS2 屬性](../core/configuring-as2-properties.md)。  

## <a name="configuring-and-testing-the-walkthrough"></a>設定和測試逐步解說  
 這個解決方案所需的程序包含下列步驟：  

- 使用必要的訊息結構描述來建置並部署 BizTalk 專案，因此 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用結構描述處理收到的交換。  

- 讓 BTS ISAPI 篩選器可用於接收 AS2 訊息。  

- 建立會從 Fabrikam 接收 AS2 訊息的 Contoso 虛擬目錄 (如接收位置中所設定)。  

- 指定 Contoso 虛擬目錄不是由 Windows SharePoint Services 管理。  

- 建立靜態雙向 HTTP 接收埠，以便讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 從交易夥伴接收包含 EDI 交換的 AS2 訊息，並傳送 MDN 回應。 將接收管線設定為 AS2EDIReceive 管線，並將傳送管線設定為 AS2Send 管線。  

- 建立靜態單向 FILE 傳送埠，以將 EDI 內容 (XML 格式) 路由傳送至本機資料夾。 建立本機資料夾。  

- 為 Fabrikam 與 Contoso 建立合作對象 (交易夥伴)。  

- 為這兩個交易合作對象各建立一個商務設定檔。  

- 在 Fabrikam 與 Contoso 的商務設定檔之間建立 AS2 協議。 AS2 協議包含的屬性可用來傳送 AS2 訊息，並接收回傳的同步 MDN。  

- 在 Fabrikam 與 Contoso 的商務設定檔之間建立 X12 協議，以便接收 X12 訊息。  

- 使用 AS2 教學課程檔案中隨附的 HTTP 傳送者公用程式，測試此解決方案。 這個公用程式會傳送測試 AS2 訊息，其中包含透過 AS2 傳輸的 EDI 交換 (AS2 教學課程中隨附的 X12_00401_864-Sync.edi)。 您必須從教學課程中的版本同時修改 HTTP 傳送器和測試訊息。 下面相關章節將說明這些變更。  

### <a name="configuring-the-walkthrough"></a>設定逐步解說  
 本節說明設定逐步解說的程序。  

##### <a name="to-deploy-the-message-schema"></a>若要部署訊息結構描述  

1. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟專案 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas\Schemas.btproj。  

   > [!NOTE]
   >  這個專案 (隨附於 AS2 教學課程) 包含了搭配測試訊息使用的 864 結構描述。  

   > [!NOTE]
   >  本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)， 如果沒有，請參閱[如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  

2. 以滑鼠右鍵按一下**結構描述**在 [方案總管] 中專案，然後按一下**屬性**。 按一下 **簽署**索引標籤，在 專案設計工具中，核取**簽署組件**核取方塊，然後從下拉式清單中，選取**新增**，並提供必要的值，以建立強式名稱金鑰檔。 儲存變更，然後關閉專案屬性視窗。  

3. 建置並部署 Schemas.btproj。  

##### <a name="to-enable-the-bts-isapi-filter"></a>若要啟用 BTS ISAPI 篩選器  

1. 按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.  

   > [!TIP]
   >  視作業系統而定，[系統管理工具] 開始功能表選項可能無法使用。 在這種情況下，按一下**開始**，按一下**執行**，然後輸入`inetmgr`以開啟 Internet Information Services (IIS) 管理員。  

2. 選取根 Web 伺服器項目並在**功能檢視**，按兩下**處理常式對應**，然後在**動作**窗格中，按一下**新增的指令碼對應**.  

   > [!NOTE]
   >  在 Web 伺服器層級設定指令碼對應會使得此對應套用至所有子網站。 若要限制對應至特定網站或虛擬資料夾，請選取目標網站或資料夾，而不要選取 Web 伺服器。  

3. 在 **新增指令碼對應**對話方塊方塊中，輸入`BtsHttpReceive.dll`中**要求路徑**欄位。  

4. 在 **可執行檔**欄位中，按一下 **省略符號 （...）** 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive。 選取 BtsHttpReceive.dll，然後按一下**確定**。  

5. 請輸入`BizTalk HTTP Receive`中**名稱**欄位，，然後按一下**要求限制**。  

6. 在 **要求限制**對話方塊中，選取**動詞**索引標籤，然後選取**其中一個下列的指令動詞**。 輸入`POST`作為動詞。  

7. 在上**存取權**索引標籤上，選取**指令碼**，然後按一下 **確定**。  

8. 按一下  **確定**當系統提示您允許 ISAPI 延伸模組時，按一下**是**。  

##### <a name="to-configure-the-contoso-web-page"></a>若要設定 Contoso 網頁  

1. 在 [IIS 管理員] 中，以滑鼠右鍵按一下**應用程式集區**，然後選取**新增應用程式集區**。  

2. 在**新增的應用程式集區**對話方塊方塊中，輸入**BizTalkAppPool**中**名稱**，然後選取 **.NET Framework v4.0.30210**中 **.NET framework 版本**下拉式清單中。 按一下 [確定] 。  

   > [!NOTE]
   >  版本號碼可能會依據電腦上安裝的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 版本而有所不同。  

3. 選取 **應用程式集區**，在 功能檢視 中選取**BizTalkAppPool**，然後按一下**進階設定**中**動作**窗格。  

4. 在 [**進階設定]** 對話方塊中，選取**身分識別**，然後按一下 [**省略符號 （...）** ] 按鈕。  

5. 在 **應用程式集區身分識別**對話方塊中，選取**自訂帳戶**，然後按一下 **設定**。  

6. 輸入**使用者名**並**密碼**使用者帳戶，系統管理員群組的成員，請輸入中的密碼**確認密碼**，然後按一下  **確定**三次，以返回 IIS 管理員。  

7. 在 [IIS 管理員] 中，開啟**站台**資料夾。 以滑鼠右鍵按一下**Default Web Site**節點，，然後選取**新增應用程式**。  

8. 在 **新增應用程式**對話方塊方塊中，輸入**Contoso**中**別名**文字方塊中，然後按一下**選取**。  

9. 在 **選取應用程式集區** 對話方塊中，選取**BizTalkAppPool** ，按一下  **確定**。  

10. 針對**實體路徑**，按一下 **省略符號 （...）** 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive。  

11. 按一下 [**測試設定**，並確認沒有顯示在錯誤**測試連接**] 對話方塊。 按一下 [關閉]，然後按一下 [確定]。  

12. 在 [IIS 管理員] 中，選取 Contoso 虛擬目錄並在**功能檢視**，按兩下**驗證**。  

13. 在 **驗證**頁面上，選取**匿名驗證**，並確認**狀態**是**已啟用**。 如果**狀態**是**停用**，按一下 **啟用**中**動作**窗格。  

##### <a name="to-specify-that-your-virtual-directory-is-not-managed-by-windows-sharepoint-services"></a>若要指定虛擬目錄不是由 Windows SharePoint Services 管理  

1.  如果 Windows SharePoint Services 安裝在電腦上，按一下**開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **SharePoint 3.0 管理中心**。  

    > [!NOTE]
    >  如果設定逐步解說的相同電腦中安裝了 Windows SharePoint Services，就必須執行這個程序。 在此情況下，您必須指定 IIS 虛擬目錄不是由 Windows SharePoint Server 管理。  

2.  在上**管理中心**頁面的 **管理中心**，按一下 **應用程式管理**。  

3.  在 **應用程式管理**頁面上，按一下**定義管理的路徑**。  

4.  在 **定義管理的路徑**頁面的 **新增路徑**，然後在**路徑**文字方塊中，輸入**Contoso**。 底下**型別**，按一下**排除的路徑**，然後按一下**確定**。  

##### <a name="to-create-a-receive-port-to-receive-the-edi-over-as2-message-and-return-an-mdn"></a>若要建立接收埠以透過 AS2 訊息接收 EDI 並傳回 MDN  

1. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **要求-回應接收埠**。  

2. 將接收連接埠，再按一下**接收位置**在主控台樹狀目錄中。  

3. 按一下 **[新增]**。  

4. 接收位置命名，選取**HTTP** for**型別**，然後按一下**設定**。  

5. 針對**虛擬目錄加 ISAPI 延伸模組**，輸入`/Contoso/BTSHTTPReceive.dll`。  

6. 選取 **擱置失敗的要求**核取方塊，然後按一下**確定**。  

7. 針對**接收管線**，選取**AS2EDIReceive**。  

8. 針對**傳送管線**，選取**AS2Send**。  

9. 按一下  **確定**，然後按一下**確定**一次。  

10. 在 **接收位置**窗格中的 BizTalk Server 管理主控台中，以滑鼠右鍵按一下接收位置，並按一下**啟用**。  

##### <a name="to-create-a-send-port-to-send-the-edi-payload-to-a-local-folder"></a>若要建立傳送埠以將 EDI 內容傳送至本機資料夾  

1. 在 Windows 檔案總管中，建立本機資料夾，名為**EDI_to_Contoso**傳送 EDI 內容。  

2. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。  

3. 在 **傳送埠屬性**對話方塊中，將傳送埠，例如**Send_Payload**。 選取 **檔案**for**型別**，然後按一下**設定**。  

4. 在**FILE 傳輸屬性** 對話方塊中，如**目的地資料夾**中，瀏覽並選取**EDI_to_Contoso**您在步驟 1 中建立的資料夾。 離開**檔名**作為 **%MessageID%.xml**。 按一下 [確定] 。  

5. 針對**傳送管線**下拉式清單中，接受預設值**PassThruTransmit**。  

6. 按一下 **篩選器**在主控台樹狀目錄中。 針對**屬性**，輸入**BTS。MessageType**。 針對**運算子**，輸入**==**。 針對**值**，輸入您的訊息，訊息類型`http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_864`。  

7. 按一下 [確定] 。  

8. 在 **傳送埠**窗格[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下傳送埠，然後**啟動**。  

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

1.  以滑鼠右鍵按一下 **[fabrikam_profile]**，指向**新增**，然後按一下**協議**。  

2.  在 [**一般屬性**] 頁面上，如**名稱**文字方塊中，輸入協議的名稱。  

3.  從**通訊協定**下拉式清單中，選取**AS2**。  

4.  在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Contoso**。  

5.  在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。  

     您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向 AS2 協議。  

6.  在 **一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**。  

7.  在上執行下列工作**Fabrikam-> Contoso**  索引標籤。  

    1.  上**識別碼**頁面上，輸入值**AS2-從**並**AS2-以**。 針對**AS2-從**，輸入`Fabrikam`。 針對**AS2-To**，輸入`Contoso`。  

8.  在上執行下列工作**Contoso-> Fabrikam**  索引標籤。  

    > [!NOTE]
    >  在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。 若要成功建立協議，兩個單向協議索引標籤必須已定義的值**AS2_From**並**AS2-以**。  

    1.  上**識別碼**頁面上，輸入值**AS2-從**並**AS2-以**。 針對**AS2-從**，輸入`Contoso`。 針對**AS2-To**，輸入`Fabrikam`。  

9. 按一下 **[套用]**。  

10. 按一下 [確定] 。 中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。 預設會啟用新增的協議。  

##### <a name="to-create-an-x12-agreement-between-the-two-business-profiles"></a>若要建立兩個商務設定檔之間的 X12 協議  

1. 以滑鼠右鍵按一下 **[fabrikam_profile]**，指向**新增**，然後按一下**協議**。  

2. 在 [**一般屬性**] 頁面上，如**名稱**文字方塊中，輸入協議的名稱。  

3. 從**通訊協定**下拉式清單中，選取**X12**。  

4. 在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Contoso**。  

5. 在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。  

    您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向 X12 協議。  

6. 在 **一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，，然後選取 **儲存訊息內容 reporting**。  

7. 在上執行下列工作**Fabrikam-> Contoso**  索引標籤。  

   1. 上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，並**ISA8**) 對應到您的測試訊息中那些標頭欄位的值。  

      > [!NOTE]
      >  對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。 它會比對的值**ISA5**， **ISA6**， **ISA7**，以及**ISA8**交換標頭與協議屬性中。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 也解析協議。 若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。  
      > 
      > [!NOTE]
      >  針對此逐步解說中，設定**ISA5**要**ZZ**， **ISA6**至**7654321**， **ISA7**到**ZZ**，並**ISA8**要**1234567**。  

   2. 上**驗證**下方的頁面上**交換設定**區段中，確定**檢查 ISA13 是否重複**選項未核取。  

      > [!NOTE]
      >  清除**檢查 ISA13 是否重複**屬性可讓您接收相同訊息的多個執行個體。  

   3. 如果您使用其中一個隨附之標準結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請在**本機主機設定**頁面下**交易集設定**區段中，選取要用來將結構描述的命名空間處理內送交換。  


      |       使用       |                           以進行此動作                            |
      |----------------------|-----------------------------------------------------------------|
      |     **預設值**      |                選取欄中的核取方塊                |
      | **目標命名空間** | 選取  **<http://schemas.microsoft.com/BizTalk/EDI/X12/2006>**。 |

      > [!NOTE]
      >  設定屬性可以讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 判斷要用於處理內送 850 交換的結構描述。 如果交換的 GS02 和 ST01 值是輸入在格線行中，則將會使用同一行的目標命名空間來判斷要使用的結構描述。  

8. 在上執行下列工作**Contoso-> Fabrikam**  索引標籤。  

   > [!NOTE]
   >  在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。 若要成功建立協議，兩個單向協議索引標籤必須已定義的值**ISA5**， **ISA6**， **ISA7**，以及**ISA8**。  

   1.  上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，並**ISA8**) 對應到您的測試訊息中那些標頭欄位的值。  

       > [!NOTE]
       >  針對此逐步解說中，設定**ISA5**要**ZZ**， **ISA6**至**1234567**， **ISA7**到**ZZ**，並**ISA8**要**7654321**。  

9. 按一下 **[套用]**。  

10. 按一下 [確定] 。 中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。 預設會啟用新增的協議。  

### <a name="testing-the-walkthrough"></a>測試逐步解說  
 本節提供關於如何測試逐步解說的資訊。  

##### <a name="to-test-the-solution"></a>測試方案  

1. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender 資料夾中的 Sender.csproj 專案。  

2. 在 HttpSender.cs 中，將下列一行標記為註解 (緊接在 //Request Asynchronous MDN 註解行底下)：  

   ```  
   Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864.edi", FileMode.Open, FileAccess.Read);  
   ```  

3. 將下列一行標記為註解 (緊接在 //Request Synchronous MDN 註解行底下)：  

   ```  
   Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864-Sync.edi", FileMode.Open, FileAccess.Read);  
   ```  

4. 建置這個專案。  

5. 在 Windows 檔案總管中，移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial。 在 [記事本] 中開啟 X12_00401_864-Sync.edi。 刪除定義 Disposition-Notification-Options 標頭的一行，然後儲存檔案。  

6. 開啟命令視窗。 移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug。 執行**Sender.exe**。  

   > [!NOTE]
   >  這時執行 Sender.exe 會將訊息 X12_00401_864-sync.edi 傳送至 Contoso 虛擬目錄 (BTS HTTP 接收位置)。  

7. 確認命令視窗中已顯示 MDN。 確認 MDN 的 AS2-From 是 Contoso，而 AS2-To 則是 Fabrikam。  

   > [!NOTE]
   >  Sender.exe 會將 MDN 顯示在命令視窗中。  

8. 開啟為傳送 EDI 內容所建立的 Contoso 本機資料夾 (**\EDI_to_Contoso**)。 確認資料夾中有 .XML 檔案。 開啟這個 XML 檔案，並確認它包含 864 交易集。  

9. 在 [記事本] 開啟測試訊息 X12_00401_864-Sync.edi，並確認的交易集在輸出訊息中**\EDI_to_Contoso**本機資料夾對應於 X12_00401_864-Sync.edi 輸入中設定的交易訊息。  

## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)