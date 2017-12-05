---
title: "逐步解說 (X12)： 接收批次的 EDI 交換 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f6e6e96-39ec-469d-a845-1bfdce6cc0bf
caps.latest.revision: "34"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95c4bb48805eb0d2b349a8802c0bc8af1d12925a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-x12-receiving-batched-edi-interchanges"></a>逐步解說 (X12)：接收批次 EDI 交換
本逐步解說提供一組逐步執行的程序，來使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 建立可接收 EDI 批次的解決方案。 這個解決方案示範了兩種接收批次 EDI 交換的方法。  
  
-   透過將批次分割為其構成交易集。  
  
-   透過保留交換，做法是以單一文件的方式處理交換而不分割交易集。  
  
 本逐步解說示範如何同時設定分割和保留批次。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
## <a name="how-the-solution-splits-received-edi-batches"></a>解決方案如何分割收到的 EDI 批次  
 當您設定解決方案以便將批次交換分割為其組成交易集時，解決方案將會執行下列作業：  
  
1.  接收位置從合作對象接收包含多個交易集的批次 EDI 交換。  
  
    > [!NOTE]
    >  這份清單中的事件可能不會按照所示的順序發生。  
  
2.  接收管線將收到的交換分割為其組成交易集，並將交易集轉換成內部 XML 格式。  
  
3.  接收管線將整個交易和群組標頭升級至每個從交換分割出來的交易集內容中。 此外還會升級特定交換和群組標頭，例如 ISA6、GS1 和 GS2，如此就能使用這些欄位進行路由。  
  
4.  接收管線將每個交易集 XML 檔案放入 MessageBox 中。  
  
    > [!NOTE]
    >  在這個解決方案中，批次中包含相同訊息類型的多個執行個體。  
  
5.  傳送埠透過訂閱適當的內容屬性來收取每個交易集。  
  
6.  傳送管線將每個交易集建置成 EDI 交換，然後將交換傳送至目的地。  
  
    > [!NOTE]
    >  如需有關如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]分割交易集批次，請參閱[分割批次 EDI 交換](../core/splitting-a-batched-edi-interchange.md)。  
  
 下圖顯示設定解決方案以分割批次交換中的交易集時，該解決方案的架構和訊息流程。  
  
 ![分割批次的 EDI 交換](../core/media/ef386df6-e195-45d9-abff-4d0bd3a82a4f.gif "ef386df6-e195-45d9-abff-4d0bd3a82a4f")  
  
## <a name="how-the-solution-preserves-received-edi-batches"></a>解決方案如何保留收到的 EDI 批次  
 當您設定解決方案以保留批次交換時，解決方案將會執行下列作業：  
  
1.  接收位置從合作對象接收包含多個交易集的批次 EDI 交換。  
  
2.  接收管線處理交換但不分割交易集，並將兩個交易集視為一個單位轉換成內部 XML 格式。  
  
3.  接收管線升級相同的屬性，如同交換不是批次的情況一樣，唯一的不同是它會在產生的 XML 上套用保留標記。 此標記是\<X12InterchangeXml\>針對 X12 編碼的 EDI 交換或\<EdifactInterchangeXml\>針對 EDIFACT 編碼的 EDI 交換。 EDI 接收管線也會套用內容屬性 `ReuseEnvelope`，以識別保留的交換。  
  
    > [!NOTE]
    >  EDI 傳送管線會使用\<X12InterchangeXml\>或\<EdifactInterchangeXml\>標記來識別為保留的批次訊息。 `ReuseEnvelope` 內容屬性可讓您建立傳送埠，以訂閱保留的所有批次交換。  
  
4.  接收管線會將訊息 XML 檔案放置在 MessageBox。  
  
5.  傳送埠透過訂閱適當的內容屬性來收取交換。  
  
6.  傳送管線將 XML 檔案中的兩個交易集建置成批次 EDI 交換，然後將交換傳送到目的地。  
  
    > [!NOTE]
    >  如需有關如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理保留批次，請參閱[保留收到批次 EDI 交換](../core/preserving-a-received-batched-edi-interchange.md)。  
  
## <a name="functionality-in-this-solution"></a>本解決方案中的功能  
 為了完成這個逐步解說，將會啟用下列功能：  
  
-   這個解決方案是專為使用 X12 編碼 (而非 EDIFACT 編碼) 的交換所設計。  
  
    > [!NOTE]
    >  用於 HIPAA 與 EDIFACT 編碼的組態，與用於 X12 編碼的組態近乎相同。  
  
-   將不會傳回技術或功能通知，以回應原本收到的交換或任何傳送的批次交換。  
  
    > [!NOTE]
    >  如需產生 EDI 通知的資訊，請參閱[(X12) 逐步解說： 接收 EDI 交換並傳送傳回通知](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)。  
  
-   這個解決方案會使用單向接收埠和靜態單向傳送埠， 因此會將這些連接埠設定為 FILE 傳輸類型。  
  
-   將會啟用 EDI 報告。  
  
-   將會儲存交易集，以從交換狀態報告中檢視交易集。  
  
-   為了測試目的，解決方案會使用傳送埠將分割的交換或保留批次傳送至本機資料夾。  
  
## <a name="configuring-and-testing-the-walkthrough"></a>設定和測試逐步解說  
 這個解決方案所需的程序包含下列步驟：  
  
-   將必要的訊息結構描述加入 BizTalk 專案，然後建置並部署此專案，因此 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用此結構描述處理訊息。  
  
-   建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的接收埠，以接收來自合作對象的 EDI X12 編碼 .txt 批次輸入訊息。  
  
-   建立傳送埠，以供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 利用批次中收到的每個交易集來建置交換 (如果分割批次的話)，或是使用接收之批次中的交易集來建置單一交換 (如果保留批次的話)。 接著傳送埠會將交換傳送至目的合作對象。 此傳送埠將是靜態單向傳送埠。  
  
-   為合作對象 A 與合作對象 B 建立合作對象 (交易夥伴)。  
  
-   分別為兩個交易夥伴建立商務設定檔。  
  
-   透過分割或保留交換，設定 EDI 屬性以接收訊息，在兩個設定檔之間建立協議。  
  
-   將一個批次 EDI 交換放入與接收位置關聯的本機資料夾。 接著您可以確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 是否已將接收之批次中的個別交換 (如果分割批次的話) 或單一保留的批次交換 (如果保留批次的話) 放入與傳送埠關聯的資料夾中。  
  
    > [!NOTE]
    >  如果您已經執行傳送批次交換逐步解說中的步驟，可以使用來自該解決方案的輸出做為此解決方案的輸入。 該解決方案的輸出是兩則 850 訊息的批次。 如需詳細資訊，請參閱[(X12) 逐步解說： 傳送批次 EDI 交換](../core/walkthrough-x12-sending-batched-edi-interchanges.md)。  
  
 本節說明設定逐步解說的程序。  
  
##### <a name="to-deploy-the-message-schema"></a>若要部署訊息結構描述  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。  
  
    > [!NOTE]
    >  本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)， 如果沒有，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
2.  以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **現有項目**。 移至**\<磁碟機\>: \Program Files\Microsoft BizTalk Server 2009\XSD_Schema\EDI\X12\00401**，然後按兩下測試訊息的對應結構描述。  
  
    > [!NOTE]
    >  如果 EDI 結構描述尚未解壓縮至 XSD_SchemaEDI 資料夾，執行**MicrosoftEdiXSDTemplates.exe** XSD_SchemaEDI 資料夾結構描述解壓縮至預設資料夾中的檔案。  
  
    > [!NOTE]
    >  針對測試訊息，您可以使用傳送批次交換逐步解說中解決方案所產生的批次交換。 該解決方案的輸出是兩個用於「EDI 介面開發人員」教學課程之 850 範例訊息執行個體的批次。 如果您這樣做，您必須使用中的結構描述 x12_00401_850.xsd [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDKEDI 介面開發人員 TutorialInbound_EDI。  
  
3.  設定組件金鑰檔案，然後建置並部署組件。  
  
##### <a name="to-create-a-one-way-receive-port-to-receive-the-batched-edi-messages"></a>建立單向接收埠以接收要批次處理的 EDI 訊息  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠。**  
  
2.  將接收連接埠，再按一下**接收位置**在主控台樹狀目錄中。  
  
3.  按一下 **[新增]**。  
  
4.  接收位置命名，選取**檔案**如**類型**，然後按一下 **設定**。  
  
5.  輸入的資料夾**接收資料夾**，和遮罩**檔案遮罩**，例如 **\*.txt**。  
  
6.  按一下 **[確定]**。  
  
7.  如**接收管線**，選取**EdiReceive**。  
  
8.  按一下 **[確定]**。  
  
9. 在主控台樹狀目錄中，按一下**接收位置**。 在**接收位置** 窗格中，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。  
  
##### <a name="to-create-a-static-one-way-send-port-to-send-the-batched-edi-interchange"></a>若要建立靜態單向傳送埠以傳送批次 EDI 交換  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠。**  
  
2.  在**傳送埠屬性**對話方塊、 傳送埠的名稱。  
  
3.  在**傳輸**區段中，選取**檔案**如**類型**，然後按一下 **設定**。  
  
4.  輸入的資料夾**目的地資料夾**，和遮罩**檔案遮罩**，例如 **\*.txt**。  
  
5.  按一下 **[確定]**。  
  
6.  在**傳送管線**，選取**EdiSend**。  
  
7.  在主控台樹狀目錄中，選取**篩選**。 在**篩選**頁面上，輸入將訂閱的訊息批次中的篩選條件運算式。 例如，選取**BTS。ReceivePortName**如**屬性**，  **==** 如**運算子**，和您剛建立的的接收埠名稱**值**。  
  
8.  按一下 **[確定]**。  
  
9. 在主控台樹狀目錄中，按一下**傳送埠**。 在**傳送埠**] 窗格中，以滑鼠右鍵按一下您的傳送埠，然後按一下 [**啟動**。  
  
##### <a name="to-create-a-party-and-a-business-profile-for-party-a"></a>為合作對象 A 建立合作對象與商務設定檔  
  
1.  以滑鼠右鍵按一下**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下 **合作對象**。  
  
2.  輸入的名稱中的合作對象**名稱**文字方塊，然後再按一下**確定**。  
  
    > [!NOTE]
    >  藉由選取**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定正在建立的合作對象為相同的組織同時裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. 據此，建立協議時將會啟用或停用某些屬性。 不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。  
  
3.  以滑鼠右鍵按一下合作對象名稱，指向**新增**，然後按一下 **商務設定檔**。  
  
4.  在**設定檔屬性**對話方塊**一般**頁面上，輸入**PartyA_Profile**中**名稱**文字方塊。  
  
    > [!NOTE]
    >  當您建立合作對象時，會同時建立設定檔。 您可以重新命名再使用該設定檔，而不需建立新設定檔。 若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。 在**一般**頁面上，指定設定檔的名稱。  
  
##### <a name="to-create-a-party-and-a-business-profile-for-party-b"></a>若要為 Party B 建立合作對象與商務設定檔  
  
1.  以滑鼠右鍵按一下**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下 **合作對象**。  
  
2.  輸入的名稱中的合作對象**名稱**文字方塊，然後再按一下**確定**。  
  
    > [!NOTE]
    >  藉由選取**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定正在建立的合作對象為相同的組織同時裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. 據此，建立協議時將會啟用或停用某些屬性。 不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。  
  
3.  以滑鼠右鍵按一下合作對象名稱，指向**新增**，然後按一下 **商務設定檔**。  
  
4.  在**設定檔屬性**對話方塊**一般**頁面上，輸入**PartyB_Profile**中**名稱**文字方塊。  
  
    > [!NOTE]
    >  當您建立合作對象時，會同時建立設定檔。 您可以重新命名再使用該設定檔，而不需建立新設定檔。 若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。 在**一般**頁面上，指定設定檔的名稱。  
  
##### <a name="to-create-an-agreement-between-the-two-business-profiles"></a>在兩個商務設定檔之間建立協議  
  
1.  以滑鼠右鍵按一下**PartyA_Profile**，指向 **新增**，然後按一下 **協議**。  
  
2.  在**一般屬性** 頁面上，針對**名稱**文字方塊中，輸入協議的名稱。  
  
3.  從**通訊協定**下拉式清單中，選取**X12**。  
  
4.  在**第二個夥伴** 區段中，從**名稱**下拉式清單中，選取**Party**。  
  
5.  在**第二個夥伴** 區段中，從**設定檔**下拉式清單中，選取**PartyB_Profile**。  
  
     您會發現兩個新的索引標籤取得旁新增**一般** 索引標籤。每個索引標籤各用於設定一個單向協議，而每個單向協議各代表一筆完整的訊息交易 (包含訊息傳輸與通知傳輸)。  
  
6.  在**一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，然後選取**儲存報告的訊息內容**。  
  
7.  在上執行下列工作**party a-> partyb**  索引標籤。  
  
    1.  在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。  
  
        > [!NOTE]
        >  對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。 它會比對的值**ISA5**， **ISA6**， **ISA7**，和**ISA8**交換標頭與協議屬性中。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 來解析協議。 若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。  
  
        > [!NOTE]
        >  如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**至**ZZ**， **ISA6**至**THEM**， **ISA7**至**ZZ**，和**ISA8**至**美國**。  
  
    2.  在**驗證**頁面**交換設定**區段中，請確定**檢查重複的 ISA13**未選項。  
  
        > [!NOTE]
        >  清除**檢查重複的 ISA13**屬性可讓您接收相同訊息的多個執行個體。  
  
    3.  在**字元集和分隔符號**頁面**交換設定**區段中，選取**CR LF**選項。  
  
    4.  在**本機主機設定**頁面**交換設定**區段的**輸入訊息處理選項**方塊中，選取**分割交換為交易集-發生錯誤時暫停交易集**選項。  
  
        > [!NOTE]
        >  我們在此解決方案中，一開始會選取此選項，來分割交換。 稍後一部分[以測試逐步解說](../core/walkthrough-x12-receiving-batched-edi-interchanges.md#BKMK_Proc)下列程序，我們會將解決方案設定為保留交換。  
  
    5.  在**傳送埠**頁面**交換設定**區段中，將您稍早建立的傳送埠產生關聯。 在**傳送埠**方格下方**名稱**資料行，按一下空白儲存格，然後從下拉式清單中，選取 傳送埠。  
  
    6.  在**信封**頁面**交易集設定**區段中，輸入在格線的第一行中的所有資料行的值。  
  
        |使用|動作|  
        |--------------|----------------|  
        |**預設值**|選取**預設**。 **注意：**當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **GS7**，和**GS8**可用即使值**交易類型**，**版本/版次**，和**目標命名空間**都不符合訊息。|  
        |**交易類型**|選取的測試訊息，訊息類型**850-Purchase Order**。|  
        |**版本/版次**|輸入 EDI 版本， **00401**。|  
        |**目標命名空間**|選取**http://schemas.microsoft.com/Edi/X12**。|  
        |**GS1**|確認已選取測試訊息的訊息類型， **PO-Purchase Order (850)**。|  
        |**GS2**|例如，輸入應用程式傳送者的值**Purchasing**。|  
        |**GS3**|例如，應用程式接收者中，輸入的值**[ordercontrol]**。|  
        |**GS4**|選取您想要的日期格式。 **注意：**您必須在下拉式清單中選取值，不只是按一下欄位以顯示預設值。 如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。|  
        |**GS5**|選擇您要的時間格式。|  
        |**GS7**|選取**X-Accredited 的 Standards Committee X12**。|  
        |**GS8**|確認已輸入 EDI 版本， **00401**。|  
  
        > [!NOTE]
        >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將值，來設定 GS01、 GS02、 GS03、 GS04、 GS05、 GS07 和 GS08 輸出的輸入值為基礎的通知**交易類型**，**版本/版次**，和**目標命名空間**。 傳送管線會嘗試將交易集類型、X12 版本和目標命名空間，與訊息標頭中的對應值進行比對。 如果成功，它會使用相關聯的 GS 值**交易類型**，**版本/版次**，和**目標命名空間**值。  
  
8.  在上執行下列工作**partyb-> party a**  索引標籤。  
  
    > [!NOTE]
    >  在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。 若要成功地建立協議，兩個單向協議索引標籤必須已定義的值**ISA5**， **ISA6**， **ISA7**，和**ISA8**。  
  
    1.  在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。  
  
        > [!NOTE]
        >  如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**至**ZZ**， **ISA6**至**美國**， **ISA7**至**ZZ**，和**ISA8**至**THEM**。  
  
9. 按一下 **[套用]**。  
  
10. 按一下 **[確定]**。 新增的協議會列在**協議**區段**合作對象與商務設定檔**窗格。 預設會啟用新增的協議。  
  
### <a name="testing-the-walkthrough"></a>測試逐步解說  
 本節提供關於如何測試逐步解說的資訊。  
  
####  <a name="BKMK_Proc"></a>若要測試逐步解說  
  
1.  在 [Windows 檔案總管] 中，開啟與接收位置相關聯的本機資料夾，將測試批次 EDI 交換放置在該資料夾中。  
  
    > [!NOTE]
    >  針對測試訊息，您可以使用傳送批次交換逐步解說中解決方案所產生的批次交換輸出。 此範例訊息包含兩個交易集。  
  
2.  開啟與先前建立之傳送埠相關聯的資料夾。 確認資料夾中包含兩個新檔案，而且每個檔案都是 850 交換，內含測試批次訊息中的其中一個交易集。  
  
3.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象**節點中，按一下任何稍早建立的協議一部分的兩個商務設定檔。 在**協議**區段中，以滑鼠右鍵按一下 協議，然後按一下 **屬性**。  
  
4.  在**協議屬性**對話方塊**本機主機設定**頁面**交換設定**區段的**輸入訊息處理選項**方塊中，選取 **保留交換-發生錯誤時暫停交換**或**保留交換-發生錯誤時暫停交易集**按一下**確定**。  
  
5.  按一下**主控件執行個體**下**平台設定**] 節點，以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下 [**重新啟動**。  
  
6.  在 Windows 檔案總管中，開啟與接收位置相關聯的本機資料夾，然後再次將相同的測試批次 EDI 交換放入該資料夾中。  
  
7.  在 [Windows 檔案總管] 中，開啟與先前建立之傳送埠相關聯的資料夾。 確認資料夾中現在只包含一個新檔案，而且該檔案是交換，內含測試批次訊息中的兩個 850 交易集。  
  
## <a name="see-also"></a>請參閱  
 [開發和設定 BizTalk Server EDI 解決方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md)   
 [分割批次的 EDI 交換](../core/splitting-a-batched-edi-interchange.md)   
 [分割 HIPAA 子文件](../core/splitting-hipaa-subdocuments.md)   
 [保留收到的批次 EDI 交換](../core/preserving-a-received-batched-edi-interchange.md)   
 [逐步解說 (X12)： 傳送批次的 EDI 交換](../core/walkthrough-x12-sending-batched-edi-interchanges.md)   
 [逐步解說 (X12)： 接收 EDI 交換並傳回通知](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)   
 [逐步解說 (X12)：傳送 EDI 交換](../core/walkthrough-x12-sending-edi-interchanges.md)