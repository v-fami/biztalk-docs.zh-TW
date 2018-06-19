---
title: 逐步解說 (X12)： 傳送批次 EDI 交換 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b80ea79b-6112-49bd-90e8-9a0a0e604df8
caps.latest.revision: 54
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d5ce491b5cf9ff3d1c142599edee4e6c5f6a324
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22292030"
---
# <a name="walkthrough-x12-sending-batched-edi-interchanges"></a>逐步解說 (X12)：傳送批次 EDI 交換
本逐步解說提供一組逐步程序，說明如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 建立可在合作對象之間傳送批次 EDI 交換的解決方案。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
## <a name="how-the-solution-sends-batched-edi-interchanges"></a>解決方案傳送批次 EDI 交換的方式  
 解決方案會執行下列作業：  
  
1.  接收位置接收來自 EDI 交換**合作對象 A**。  
  
    > [!NOTE]
    >  這份清單中的事件可能不會按照所示的順序發生。  
  
2.  接收管線將交換的 EDI 格式轉換為內部 XML 格式， 並判斷要批次處理該交換。 因此，BatchMarkerReceivePipeline 元件會升級 `EDI.ToBeBatched==True` 和 `EDI.BatchId` 屬性。 接著將該交換放入 MessageBox。  
  
3.  「批次協調流程」根據 `EDI.ToBeBatched==True` 和 `EDI.BatchId==%BatchID%` 訂閱了這個訊息，因而從 MessageBox 擷取收到的交換。  
  
4.  接收位置收到當初傳來第一個交換的同一個合作對象所傳來的第二個 EDI 交換。  
  
5.  接收位置依照步驟 2 中的方式處理交換，然後將交換放置在 MessageBox 中。  
  
6.  「批次處理協調流程」依照步驟 3 中的方式擷取交換。  
  
7.  在達到釋放準則後 (釋放準則定義了交換的比對方式)，「批次協調流程」將所有交換組合成一個交換，然後升級 `EDI.ToBeBatched==False`、`EDI.BatchName` 和 `EDI.DestinationPartyName` 內容屬性。 它會卸除批次的交換放入 MessageBox。  
  
8.  傳送埠透過訂閱 `EDI.ToBeBatched`==False、`EDI.BatchName` 和 `EDI.DestinationPartyName` 這些內容屬性，來收取批次交換。  
  
9. 傳送管線將其他屬性套用至批次交換的信封，然後將交換傳送至目的合作對象，**合作對象 B**。  
  
    > [!NOTE]
    >  如需詳細資訊，請參閱[組合批次 EDI 交換](../core/assembling-a-batched-edi-interchange.md)。  
  
 下圖顯示這個解決方案的架構。  
  
 ![傳送批次 EDI 交換](../core/media/93a09e3c-476d-4bd2-a0e3-b5b219858791.gif "93a09e3c-476d-4bd2-a0e3-b5b219858791")  
  
## <a name="the-functionality-in-this-solution"></a>此解決方案中的功能  
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
  
## <a name="configuring-and-testing-the-walkthrough"></a>設定和測試逐步解說  
 這個解決方案所需的程序包含下列步驟：  
  
-   將必要的訊息結構描述加入 BizTalk 專案，然後建置並部署此專案，因此 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用此結構描述處理訊息。  
  
-   更新中的 SQL 配接器的輪詢間隔**BatchControlMessageReccvLoc**接收位置，如此當您按一下 立即啟動批次處理協調流程**啟動**按鈕傳送控制訊息會啟動批次處理協調流程執行個體。  
  
-   建立接收埠，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收來自合作對象的 EDI X12 編碼 .txt 輸入訊息。  
  
-   為合作對象 A 與合作對象 B 建立合作對象 (交易夥伴)。  
  
-   分別為兩個交易夥伴建立商務設定檔。  
  
-   設定讓訊息收得到的 EDI 屬性，以建立這兩個設定檔之間的協議。 設定讓批次訊息傳送得出去的 EDI 屬性。 就這個解決方案而言，請設定協議，讓 BizTalk Server 每收到兩個 850 交換，就傳送批次交換給 Party B。  
  
-   建立傳送埠，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送批次 EDI 交換給交易夥伴。 此傳送埠將是靜態單向傳送埠。  
  
-   使傳送埠與會負責批次處理交換的協議產生關聯。  
  
-   將兩個測試 EDI 交換放置在與接收位置相關聯的本機資料夾中，並確認 BizTalk Server 已將批次交換放置在與傳送埠相關聯的資料夾中。  
  
### <a name="configuring-the-walkthrough"></a>設定逐步解說  
 本節說明設定逐步解說的程序。  
  
##### <a name="to-deploy-the-message-schema"></a>若要部署訊息結構描述  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。  
  
    > [!NOTE]
    >  本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)， 如果沒有，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
2.  以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **現有項目**。 移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\X12\00401，然後按兩下與測試訊息對應的結構描述。  
  
    > [!NOTE]
    >  如果 EDI 結構描述尚未解壓縮至 \XSD_Schema\EDI 資料夾，執行**MicrosoftEdiXSDTemplates.exe** \XSD_Schema\EDI 資料夾，將結構描述解壓縮至預設資料夾中的檔案。  
  
    > [!NOTE]
    >  對於測試訊息，您可以使用「EDI 介面開發人員」教學課程中所使用的 850 範例訊息。 這是檔案中的 SamplePO.txt [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\\。 如果這樣做，您就必須使用位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 中的結構描述 x12_00401_850.xsd。  
  
3.  設定組件金鑰檔案，然後建置並部署組件。  
  
##### <a name="to-update-the-polling-interval"></a>若要更新輪詢間隔  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，開啟**BizTalk 群組**，**應用程式**， **BizTalk EDI 應用程式**節點，和**接收位置**節點。 在下**接收位置**] 節點，以滑鼠右鍵按一下**BatchControlMessageRecvLoc**，然後按一下 [**屬性**。  
  
2.  針對 SQL 傳輸類型，按一下**設定**。  
  
3.  在**SQL 傳輸屬性**對話方塊方塊中，將輪詢間隔設定為較小的值。 例如，您可以變更**輪詢的度量單位**至**秒**，而不是變更輪詢間隔為 5 秒，以分鐘為單位。  
  
    > [!NOTE]
    >  變更輪詢間隔可確保立即啟動批次處理協調流程。  
  
4.  按一下**確定**，然後按一下 **確定**一次。  
  
##### <a name="to-create-a-one-way-receive-port-to-receive-the-edi-messages-to-be-batched"></a>若要建立單向接收埠以接收要批次處理的 EDI 訊息  
  
1.  建立本機資料夾以接收要批次處理的 EDI 訊息。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠。**  
  
3.  將接收連接埠，再按一下**接收位置**在主控台樹狀目錄中。  
  
4.  按一下 **[新增]**。  
  
5.  接收位置命名，選取**檔案**如**類型**，然後按一下 **設定**。  
  
6.  輸入的資料夾**接收資料夾**，和遮罩**檔案遮罩**，例如 **\*.txt**。  
  
7.  按一下 **[確定]**。  
  
8.  如**接收管線**，選取**EdiReceive**。  
  
9. 按一下**確定**，然後按一下 **確定**一次。  
  
10. 在主控台樹狀目錄中，按一下**接收位置**。 在**接收位置** 窗格中，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。  
  
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
  
    4.  在**批次組態**頁面**交換設定**區段中，執行下列動作：  
  
        1.  按一下**新批次**。  
  
        2.  在下**識別** 區段中，針對**批次名稱**文字、 輸入`Batch1`。  
  
        3.  在下**篩選**區段中，按一下**篩選** 按鈕，然後在**批次篩選條件**對話方塊方塊中，執行下列動作：  
  
            1.  按一下下方的空白儲存格**屬性**資料行，然後選取**BTS。ReceivePortName**。  
  
            2.  按一下下方的空白儲存格**運算子**資料行，然後選取 **==** 。  
  
            3.  按一下下方的空白儲存格**值**資料行，然後輸入您稍早建立的接收埠名稱。  
  
            4.  按一下 **[確定]**。  
  
        4.  在下**發行**區段中，選取**最大數目的交易集**選項，從下拉式清單中選取**交換**，並在文字方塊中輸入的數目將批次處理的交換。 在此解決方案中，您將會批次處理兩個交換，因此請在文字方塊中，輸入`2`。  
  
        5.  在下**啟用**區段中，選取**立即開始**。  
  
    5.  在**信封**頁面**交易集設定**區段中，輸入在格線的第一行中的所有資料行的值。  
  
        |使用|動作|  
        |--------------|----------------|  
        |**預設值**|選取**預設**。 **注意：** 當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **GS7**，和**GS8**可用即使值**交易類型**，**版本/版次**，和**目標命名空間**都不符合訊息。|  
        |**交易類型**|選取的測試訊息，訊息類型**850-Purchase Order**。|  
        |**版本/版次**|輸入 EDI 版本， **00401**。|  
        |**目標命名空間**|選取**http://schemas.microsoft.com/BizTalk/Edi/X12/2006**。|  
        |**GS1**|確認已選取測試訊息的訊息類型， **PO-Purchase Order (850)**。|  
        |**GS2**|例如，輸入應用程式傳送者的值**Purchasing**。|  
        |**GS3**|例如，應用程式接收者中，輸入的值 **[ordercontrol]**。|  
        |**GS4**|選取您想要的日期格式。 **注意：** 您必須在下拉式清單中選取值，不只是按一下欄位以顯示預設值。 如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。|  
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
  
##### <a name="to-create-a-static-one-way-send-port-to-send-the-batched-edi-interchange"></a>若要建立靜態單向傳送埠以傳送批次 EDI 交換  
  
1.  建立本機資料夾以將批次 EDI 訊息傳送至其中。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠。**  
  
3.  在**傳送埠屬性**對話方塊、 傳送埠的名稱。  
  
4.  在**傳輸**區段中，選取**檔案**如**類型**，然後按一下 **設定**。  
  
5.  輸入的資料夾**目的地資料夾**，和**檔案名稱**，例如 **%MessageID%.txt**。  
  
6.  按一下 **[確定]**。  
  
7.  在**傳送管線**，選取**EdiSend**。  
  
8.  在主控台樹狀目錄中，選取**篩選**。 在**篩選**頁面上，執行下列動作：  
  
    1.  在方格的第一行中，選取**EDI。DestinationPartyName**如**屬性**，  **==** 如**運算子**，您所選取的合作對象傳送的批次名稱**值**，和**和**如**分組**。  
  
    2.  在第二行中，選取**EDI。ToBeBatched**如**屬性**，  **==** 如**運算子**，和**False**如**值**，和**和**如**分組**。  
  
    3.  在第三行中，選取**EDI。BatchName**如**屬性**，  **==** 如**運算子**，和的批次名稱**值**。  
  
9. 按一下 **[確定]**。  
  
10. 在主控台樹狀目錄中，按一下**傳送埠**。 在**傳送埠**] 窗格中，以滑鼠右鍵按一下您的傳送埠，然後按一下 [**啟動**。  
  
##### <a name="to-associate-the-send-port-with-the-agreement-created-for-batching"></a>若要讓傳送埠與建立要用於批次處理的協議產生關聯  
  
1.  以滑鼠右鍵按一下您稍早建立的協議，然後按一下**屬性**。  
  
2.  在**協議屬性**對話方塊**party a-> partyb**索引標籤上，按一下 **傳送埠**的左窗格中。  
  
3.  在**傳送埠**頁面**交換設定**區段中，將您稍早建立的傳送埠產生關聯。 在**傳送埠**方格下方**名稱**資料行，按一下空白儲存格，然後從下拉式清單中，選取 傳送埠。  
  
4.  按一下 **[確定]**。  
  
### <a name="testing-the-walkthrough"></a>測試逐步解說  
 本節提供關於如何測試逐步解說的資訊。  
  
##### <a name="to-test-the-walkthrough"></a>若要測試逐步解說  
  
1.  在 [Windows 檔案總管] 中，開啟與接收位置相關聯的本機資料夾，然後將測試 EDI 交換放置在該資料夾中。  
  
    > [!NOTE]
    >  對於測試訊息，您可以使用「EDI 介面開發人員」教學課程中所使用的 850 範例訊息。 這是檔案中的 SamplePO.txt [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\\。 如果這樣做，您就必須使用位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 中的結構描述 x12_00401_850.xsd。  
  
2.  將測試 EDI 交換的第二份複本放置到該資料夾中。  
  
3.  開啟您為了放置交換而與傳送埠產生關聯的資料夾，然後開啟批次交換。 確認此交換包含一組 ISA 與 GS 標頭和兩個交易集。  
  
## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server EDI 解決方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md)   
 [設定外寄批次](../core/configuring-an-outgoing-batch.md)   
 [組合批次的 EDI 交換](../core/assembling-a-batched-edi-interchange.md)   
 [組合批次的 EDI 交換](../core/assembling-a-batched-edi-interchange.md)   
 [逐步解說 (X12)： 接收 EDI 交換並傳回通知](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)   
 [逐步解說 (X12)： 傳送 EDI 交換](../core/walkthrough-x12-sending-edi-interchanges.md)