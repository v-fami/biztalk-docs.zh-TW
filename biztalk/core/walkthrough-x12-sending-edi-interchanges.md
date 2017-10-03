---
title: "逐步解說 (X12)： 傳送 EDI 交換 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05533821-b9eb-44bc-af65-b6fb0b545137
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc29d8739aeff07241c1491ba7ae96dcf7260372
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-x12-sending-edi-interchanges"></a>逐步解說 (X12)：傳送 EDI 交換
本逐步解說提供一組逐步執行的程序，來使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 建立可傳送 EDI 交換的解決方案。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
## <a name="how-the-solution-sends-edi-interchanges"></a>解決方案如何傳送 EDI 交換  
 解決方案會執行下列作業：  
  
1.  單向 FILE 接收埠會從 Fabrikam 接收 EDI 訊息。  
  
2.  這個接收埠會使用 EdiReceive 管線來檢查訊息並將其轉換成 XML。 然後接收埠會將測試訊息拖曳到 MeassageBox。  
  
3.  靜態的單向傳送埠會從 MessageBox 拾取 XML 訊息。  
  
4.  靜態的單向傳送埠會依據訊息結構描述驗證 EDI 訊息、序列化 EDI 訊息成 EDI 交換，然後再將 EDI 訊息傳送到交易夥伴 Contoso 的本機資料夾。  
  
## <a name="the-functionality-in-this-solution"></a>此解決方案中的功能  
 本逐步解說使用下列功能：  
  
-   本逐步解說中不會測試通知的接收。 若要了解如何接收通知，請參閱示範[(X12) 逐步解說： 接收 EDI 交換並傳送傳回通知](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)  
  
-   這個解決方案是專為使用 X12 編碼 (而非 EDIFACT 編碼) 的交換所設計。  
  
    > [!NOTE]
    >  用於 HIPAA 與 EDIFACT 編碼的組態，與用於 X12 編碼的組態近乎相同。  
  
-   將針對外寄交換執行 EDI 類型和擴充驗證。  
  
-   這個解決方案使用靜態單向傳送埠與 FILE 傳輸類型。  
  
    > [!NOTE]
    >  您可以使用靜態雙向傳送埠以傳送交換並接收通知，來取代靜態單向傳送埠。 也可以使用動態單向傳送埠以傳送交換。 如需有關如何使用動態傳送埠的詳細資訊，請參閱[設定動態傳送埠以傳送 EDI 交換和通知](../core/configuring-a-dynamic-send-port-to-send-edi-interchanges-and-acknowledgments.md)。  
  
    > [!NOTE]
    >  您可以使用 HTTP 配接器和 AS2 傳輸。 如需有關如何執行這項作業的詳細資訊，請參閱[逐步解說 (AS2): 使用同步 MDN 透過 AS2 傳送的 EDI](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md)或[逐步解說 (AS2): 使用非同步 MDN 透過 AS2 傳送的 EDI](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md)。  
  
-   EDI 報告將會啟用，並會儲存交易集，以從交換狀態報告進行檢視。  
  
-   基於測試的目的，解決方案使用接收位置以接收測試訊息。  
  
 下圖顯示這個解決方案的架構，其中使用靜態單向傳送埠。  
  
 ![傳送 EDI 交換](../core/media/6915024c-687c-4076-a730-3f7b9d2db7fb.gif "6915024c-687c-4076-a730-3f7b9d2db7fb")  
  
## <a name="configuring-and-testing-the-walkthrough"></a>設定和測試逐步解說  
 這個解決方案所需的程序包含下列步驟：  
  
-   將必要的訊息結構描述加入 BizTalk 專案，然後建置並部署此專案，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用該結構描述來處理輸出交換。  
  
-   建立接收埠和位置以供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收 EDI 交換。 此接收位置繫結至檔案資料夾，而 Fabrikam 會在此資料夾放置要傳送給 Contoso 的 EDI 交換。 接收位置將使用 EdiReceive 接收管線。  
  
-   建立傳送埠以供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送 EDI 交換至 Contoso。 在此逐步解說中，您將建立靜態單向傳送埠。  
  
-   為 Fabrikam 與 Contoso 建立合作對象 (交易夥伴)。  
  
-   分別為兩個交易夥伴建立商務設定檔。  
  
-   設定讓訊息收得到的 EDI 屬性，以建立這兩個設定檔之間的協議。  
  
-   使用測試 EDI 交換以測試逐步解說。  
  
    > [!NOTE]
    >  對於測試訊息，您可以使用 EDI 介面開發人員教學課程中所使用的 SamplePO.txt 檔案。 該檔案隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ 資料夾中。 這是 X12 850 訊息。  
  
### <a name="configuring-the-walkthrough"></a>設定逐步解說  
 本節說明設定逐步解說的程序。  
  
##### <a name="to-deploy-the-message-schema"></a>若要部署訊息結構描述  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。  
  
    > [!NOTE]
    >  本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)， 如果沒有，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
2.  以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **現有項目**。 移至結構描述所在的資料夾 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI，然後按兩下該結構描述。  
  
    > [!NOTE]
    >  如果 EDI 結構描述尚未解壓縮至 \XSD_Schema\EDI 資料夾，執行**MicrosoftEdiXSDTemplates.exe** \XSD_Schema\EDI 資料夾，將結構描述解壓縮至預設資料夾中的檔案。  
  
    > [!NOTE]
    >  如果您使用 EDI 介面開發人員教學課程中所用的 SamplePO.txt 檔案，則必須使用隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 資料夾中的 X12_00401_850.xsd 結構描述。 您不得使用 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema 資料夾中的 X12 850 結構描述。  
  
3.  將組件金鑰檔案加入專案，然後建置並部署組件。  
  
##### <a name="to-create-a-one-way-receive-port-for-fabrikam-to-receive-the-edi-interchange"></a>建立單向接收埠 (供 Fabrikam 使用) 以接收 EDI 交換  
  
1.  在 Windows 檔案總管中，建立本機資料夾，以接收交換。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠**。  
  
3.  將接收連接埠，再按一下**接收位置**在主控台樹狀目錄中。  
  
4.  按一下 **[新增]**。  
  
5.  接收位置命名，選取**檔案**如**類型**，然後按一下 **設定**。  
  
6.  輸入的資料夾**接收資料夾**，並輸入 **\*.txt**對於檔案遮罩。  
  
7.  按一下 **[確定]**。  
  
8.  如**接收管線**，選取**EdiReceive**。  
  
9. 按一下**確定**，然後按一下 **確定**一次。  
  
10. 在主控台樹狀目錄中，按一下**接收位置**。 在**接收位置** 窗格中，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。  
  
##### <a name="to-create-a-static-one-way-send-port-for-contoso-to-send-the-edi-interchange"></a>建立靜態單向傳送埠 (供 Contoso 使用) 以傳送 EDI 交換  
  
1.  在 Windows 檔案總管中，建立本機資料夾，以便將 EDI 交換傳送至此本機資料夾。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊、 傳送埠的名稱。  
  
4.  在**傳輸**區段中，選取**類型**，例如**檔案**。  
  
5.  如果使用的檔案類型，按一下**設定**。 在**目的地資料夾**，瀏覽至要傳送交換的資料夾。 如**檔案名稱**，輸入**%MessageID%.edi**。 按一下 **[確定]**。  
  
6.  在**傳送管線**，選取**EdiSend**。  
  
7.  在主控台樹狀目錄中，選取**篩選**，並輸入要用來訂閱訊息的傳送埠的篩選運算式。 例如，您可以使用將要接收原始測試訊息的接收位置做為篩選條件運算式。 若要這樣做，**屬性**，輸入**BTS。ReceivePortName**;**運算子**，輸入 **==** ; 以及**值**輸入您要建立的接收埠名稱接收來自 Fabrikam 的 XML 訊息。  
  
    > [!NOTE]
    >  您可以依您的選擇篩選其他屬性，例如 BTS.MessageType。  
  
8.  按一下 **[確定]**。  
  
9. 按一下**傳送埠**節點在管理主控台中，以滑鼠右鍵按一下您的傳送埠，然後按一下**啟動**。  
  
##### <a name="to-create-a-party-and-a-business-profile-for-fabrikam"></a>若要為 Fabrikam 建立合作對象與商務設定檔  
  
1.  以滑鼠右鍵按一下**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下 **合作對象**。  
  
2.  輸入的名稱中的合作對象**名稱**文字方塊，然後再按一下**確定**。  
  
    > [!NOTE]
    >  藉由選取**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定正在建立的合作對象為相同的組織同時裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. 據此，建立協議時將會啟用或停用某些屬性。 不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。  
  
3.  以滑鼠右鍵按一下合作對象名稱，指向**新增**，然後按一下 **商務設定檔**。  
  
4.  在**設定檔屬性**對話方塊**一般**頁面上，輸入**[fabrikam_profile]**中**名稱**文字方塊。  
  
    > [!NOTE]
    >  當您建立合作對象時，會同時建立設定檔。 您可以重新命名再使用該設定檔，而不需建立新設定檔。 若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。 在**一般**頁面上，指定設定檔的名稱。  
  
##### <a name="to-create-a-party-and-a-business-profile-for-contoso"></a>若要為 Contoso 建立合作對象與商務設定檔  
  
1.  以滑鼠右鍵按一下**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下 **合作對象**。  
  
2.  輸入的名稱中的合作對象**名稱**文字方塊，然後再按一下**確定**。  
  
    > [!NOTE]
    >  藉由選取**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定正在建立的合作對象為相同的組織同時裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. 據此，建立協議時將會啟用或停用某些屬性。 不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。  
  
3.  以滑鼠右鍵按一下合作對象名稱，指向**新增**，然後按一下 **商務設定檔**。  
  
4.  在**設定檔屬性**對話方塊**一般**頁面上，輸入**[contoso_profile]**中**名稱**文字方塊。  
  
    > [!NOTE]
    >  當您建立合作對象時，會同時建立設定檔。 您可以重新命名再使用該設定檔，而不需建立新設定檔。 若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。 在**一般**頁面上，指定設定檔的名稱。  
  
##### <a name="to-create-an-agreement-between-the-two-business-profiles"></a>在兩個商務設定檔之間建立協議  
  
1.  以滑鼠右鍵按一下**fabrikam_profile**，指向 **新增**，然後按一下 **協議**。  
  
2.  在**一般屬性** 頁面上，針對**名稱**文字方塊中，輸入協議的名稱。  
  
3.  從**通訊協定**下拉式清單中，選取**X12**。  
  
4.  在**第二個夥伴** 區段中，從**名稱**下拉式清單中，選取**Contoso**。  
  
5.  在**第二個夥伴** 區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。  
  
     您會發現兩個新的索引標籤取得旁新增**一般** 索引標籤。每個索引標籤各用於設定一個單向協議，而每個單向協議各代表一筆完整的訊息交易 (包含訊息傳輸與通知傳輸)。  
  
6.  在**一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，然後選取**儲存報告的訊息內容**。  
  
7.  在上執行下列工作**Fabrikam-> Contoso**  索引標籤。  
  
    1.  在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。  
  
        > [!NOTE]
        >  對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。 它會比對的值**ISA5**， **ISA6**， **ISA7**，和**ISA8**交換標頭與協議屬性中。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 來解析協議。 若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。  
  
        > [!NOTE]
        >  如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**至**ZZ**， **ISA6**至**THEM**， **ISA7**至**ZZ**，和**ISA8**至**美國**。  
  
    2.  在**驗證**頁面**交換設定**區段中，請確定**檢查重複的 ISA13**未選項。  
  
        > [!NOTE]
        >  清除**檢查重複的 ISA13**屬性可讓您接收相同訊息的多個執行個體。  
  
    3.  在**字元集和分隔符號**頁面**交換設定**區段中，選取**CR LF**選項。  
  
    4.  在**傳送埠**頁面**交換設定**區段中，將會從 Fabrikam 接收 EDI 交換的傳送埠產生關聯。 在**傳送埠**方格下方**名稱**資料行中，按一下空白儲存格，並從下拉式清單中，選取 建立從 Fabrikam 接收 EDI 交換的傳送埠。  
  
    5.  在**驗證**頁面**交易集設定**區段中，保留**EDI 類型驗證**檢查，並檢查**擴充驗證**.  
  
    6.  如果您使用隨附之標準結構描述的其中一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上**本機主機設定**頁面**交易集設定**區段中，選取要用於結構描述的命名空間處理內送交換。  
  
        |使用|動作|  
        |--------------|----------------|  
        |**預設值**|選取欄中的核取方塊|  
        |**如 ST1**|選取**850-Purchase Order**。|  
        |**GS2**|輸入**THEM**。|  
        |**目標命名空間**|選取**http://schemas.microsoft.com/BizTalk/EDI/X12/2006**。|  
  
        > [!NOTE]
        >  設定屬性可以讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 判斷要用於處理內送 850 交換的結構描述。 如果交換的 GS02 和 ST01 值是輸入在格線行中，則將會使用同一行的目標命名空間來判斷要使用的結構描述。  
  
    7.  在**信封**頁面**交易集設定**區段中，輸入在格線的第一行中的所有資料行的值。  
  
        |使用|動作|  
        |--------------|----------------|  
        |**預設值**|選取核取方塊**預設**資料行。 **注意：**當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **GS7**，和**GS8**可用即使值**交易類型**，**版本/版次**，和**目標命名空間**都不符合訊息。|  
        |**交易類型**|選取的測試訊息，訊息類型**850-Purchase Order**。|  
        |**版本/版次**|輸入 EDI 版本， **00401**。|  
        |**目標命名空間**|選取**http://schemas.microsoft.com/BizTalk/Edi/X12/2006**。|  
        |**GS1**|確認已選取測試訊息的訊息類型， **PO-Purchase Order (850)**。|  
        |**GS2**|輸入應用程式傳送者的值。|  
        |**GS3**|輸入應用程式接收者的值。|  
        |**GS4**|選取您想要的日期格式。 **注意：**您必須在下拉式清單中選取值，不只是按一下欄位以顯示預設值。 如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。|  
        |**GS5**|選擇您要的時間格式。|  
        |**GS7**|選取**X-Accredited 的 Standards Committee X12**。|  
        |**GS8**|確認已輸入 EDI 版本， **00401**。|  
  
        > [!NOTE]
        >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將值，來設定 GS01、 GS02、 GS03、 GS04、 GS05、 GS07 和 GS08 輸出的輸入值為基礎的通知**交易類型**，**版本/版次**，和**目標命名空間**。 傳送管線會嘗試將交易集類型、X12 版本和目標命名空間，與訊息標頭中的對應值進行比對。 如果成功，它會使用相關聯的 GS 值**交易類型**，**版本/版次**，和**目標命名空間**值。  
  
8.  在上執行下列工作**Contoso-> Fabrikam**  索引標籤。  
  
    > [!NOTE]
    >  在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。 若要成功地建立協議，兩個單向協議索引標籤必須已定義的值**ISA5**， **ISA6**， **ISA7**，和**ISA8**。  
  
    1.  在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。  
  
        > [!NOTE]
        >  如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**至**ZZ**， **ISA6**至**美國**， **ISA7**至**ZZ**，和**ISA8**至**THEM**。  
  
9. 按一下 **[套用]**。  
  
10. 按一下 **[確定]**。 新增的協議會列在**協議**區段**合作對象與商務設定檔**窗格。 預設會啟用新增的協議。  
  
### <a name="testing-the-walkthrough"></a>測試逐步解說  
 本節提供關於如何測試逐步解說的資訊。  
  
##### <a name="to-test-the-walkthrough"></a>若要測試逐步解說  
  
1.  在 Windows 檔案總管中，將測試 EDI 交換置放到本機接收資料夾中。  
  
    > [!NOTE]
    >  對於測試訊息，您可以使用 EDI 介面開發人員教學課程中所使用的 SamplePO.txt 檔案。 該檔案隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial 資料夾中。 這是 X12 850 訊息。 如果您使用這個訊息，則必須完成 X12_00401_850.xsd 結構描述的部署 (該結構描述隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 資料夾)。 您不得使用 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema 資料夾中的 X12 850 結構描述。  
  
2.  在 Windows 檔案總管中，開啟為傳送埠指定的目的資料夾。 確認資料夾包含輸出 EDI 交換，其 ISA、GS 和 ST 標頭符合您在協議屬性中輸入的值。  
  
## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server EDI 解決方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md)